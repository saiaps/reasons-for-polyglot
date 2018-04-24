# Why Polyglot

Why choose to add a programming language?

## To Automate

In our own work, when we are using software instead of creating it, often the tool we need exists in a language that is not our favorite.

Example: [the source](https://github.com/atomist/end-user-documentation) for [docs.atomist.com](http://docs.atomist.com/)

## Fit the Language to the Problem

### "Language" is broader than we think

Choosing a programming language gets you more than the syntax. It gets you an ecosystem (libraries, build tools, dependency managers, books) and a community. A language is good at what its community is good at, because that's what gets built into frameworks, documented in tutorials, and discussed at meetups. This spirals: people who want to do that thing join the language community.

Python is good for data science. The syntax has very little to do with it. Python is good for data science because of libraries (Pandas/Numpy, which is built on C and Fortran under the covers) and tools like Jupyter Notebook.

Scala is good for data science at scale. The libraries exist, people use them, a community forms to solve the problems that come up.

Ruby is good for web apps that you need to write quickly and iterate on quickly. Stripe started there, for instance, and then when they needed serious data science and machine learning, they brought in Scala.

Java is good for ... pretty much everything, it may not be the shining example of anything but there's sufficient quantity of people working in it that something exists for everyone. And it's probably been around for decades and is likely solid.

If you're trying to build a maintainable web site, or build firmware, or make mobile apps, find the _people_ who are doing that, find the language they're using, and that language system will fit your problem.

### "Problem" is broader than we think

Yet, whatever service we're trying to build -- the future state of a piece of software we're aiming for -- is only part of the problem.

The interesting part of building our systems is not envisioning the desired state and constructing that out of air. The mythical greenfield development. The interesting part is moving from where we are, to there, and beyond.

On the production software side, we'll need to interface with existing databases and existing services. Which language systems make that easy?

On the tooling software side, we'll need to be compatible with existing logging and monitoring and build and deployment. Which language systems make that easy?

On the social side, the people on this team and in this company will need to work on and with whatever we build. What language systems are they already compatible with?

Michael Feathers said, "The best designs come from paying attention to what is there."

![Fallingwater, by Frank Lloyd Wright](https://pbs.twimg.com/media/DbApvCVVQAAzDR0.jpg)

He was talking about architecture of buildings, but it's true of software too.

Your problem is not only your problem. It is also the surrounding context. Especially the people.

## For the People

People want to work in modern languages.

-  to be more productive at adding code
-  to learn new shapes of thinking
-  to keep our skills relevant

Bringing in a more recent programming language can change existing people. It also changes the kind of people who join your organization.

-  recruiting. Forget about "how many" -- what kind of people do you want to hire?
-  retention. Developer experience matters

What other effects does it have on the people in the organization?

-  adds obstacles to troubleshooting
-  divides people more strongly into categories

At best, divisions can be a positive, if you're aiming for modularity and drawing these boundaries at architectural seams. Conway's Law can go both ways: changing tech can change communication boundaries in the organization, although not in ways that are easy to predict.

At worst, people hate the new language because it makes them feel stupid. When you have years of experience with one system, you've built up knowledge and context and speed. Switching to a new one throws much of this away. After a decade in the JVM, moving to Node is trivial at first and then repeatedly, unexpectedly painful. How do I get a thread dump? Which of these twenty libraries is any good?

If your goal is to edify yourself, then add the new language in the lower-risk portions of the technical system: personal or team-level automations. Internal tooling is lower-cost and lower-risk.

If your goal is to improve your experience, consider creating custom automation (in a language of your choice) around the existing language system.

## To meet constraints

Sometimes you really are trying to solve something new to the company -- or under new constraints.

Platforms the app needs to run on. Less frequent deployments (mobile), or more frequent. Privacy restrictions. Verification needs (can a bug kill a person?). Incredibly high uptime.

This lets you attach a business value to introducing the new language. How much is it really worth to meet that constraint?

## To break constraints

Other times, the current software was built to meet constraints that don't apply to what you're building. 

Stripe is extremely careful about backwards compatibility, which constrains framework upgrades. Internal services don't need to meet that.

At Atomist, we used to have a "you write a program, we run it" design, so we ran on the JVM with sandboxing. Once we switched to "you write it, you run it, it calls our service" then many options were open to us. We threw away the internal DSL, stopped using Scala, and moved all our automations to TypeScript. 

More subtly, constraints can be introduced as tools, as enhancements, as process.

If I did write an internal tool in Ruby in Stripe, and chose not to use the internal library that limited the version of a framework, that raised eyebrows. And it threw off the expectations of people who were used to using those libraries; it made my code violate expectations.

A new programming language comes with freedom. Goodbye, internal libraries written by other people. Hello, functions written by me! Goodbye, "best practices" that are ten years out of date. Goodbye, elaborate hierarchical build configuration. This is an opportunity to break away from standards and infrastructure that slow you down or hold you back.

And this comes with responsibility, to build most of that back up around your new language. All that complexity is there for reasons, and most of those reasons come around again.

Take this as an opportunity to define what a requirements a language system has at your organization. Build the [Language System API](https://github.com/saiaps/language-system-api/blob/master/README.md).
