---
title: "Launch a script that uses function defined in .bashrc"
date: 2014-07-04
forum: General Help
---

### Post by g-g-salt on 2014-07-04
I have a bash script that calls a function that is defined in .bashrc

This script runs fine from the command line.  However, when I try to launch this script from a desktop launcher, it cannot find the function and execution fails.

Is there any way to launch this script from a desktop launcher?

**UPDATE:**  Basically, you cannot do this.  The desktop launcher is unaware of the bash environment.  You can put environment variables in a separate file and source that file in your script; however, the shell that the launcher uses is /bin/sh and it does not recognize bash functions.

My function is pretty simple, so I moved it to the script I want to launch.

---

