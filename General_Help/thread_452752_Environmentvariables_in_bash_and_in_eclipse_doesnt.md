---
title: "Environmentvariables in bash and in eclipse doesnt match!"
date: 2007-05-23
forum: General Help
---

### Post by Nasso on 2007-05-23
I have a problem. I am trying to use an arm-compiler from eclipse and to do so i need some environmentvariables set. i have set them in my .bashrc and their names are DEVKITPRO,DEVKITARM and i want to add DEVKITARM/bin to the path-variable.

Take a look at this screenshot. The variables are set in my shell but not in my program run through eclipse, how is this?

[IMG]http://nasso.se/ul/env-comparison.png[/IMG]

---

### Post by lloyd_b on 2007-05-23
Just a guess, but I'd suspect that eclipse is running "/bin/sh", which is linked to "dash" rather than "bash".  In which case "~/.bashrc" is simply never executed.

Try creating a "~/.profile" file in your home directory, and put those environment variables in there (so "dash" sees them"), and see if this resolves the problem.

Lloyd B.

---

### Post by hartz on 2007-05-25
Try starting the application from the terminal/shell session in which you have confirmed that the variables are set and exported (env).  dash will still inherit the exported environment from a parent bash shell.

---

