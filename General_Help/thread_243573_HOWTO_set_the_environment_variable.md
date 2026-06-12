---
title: "HOWTO set the environment variable"
date: 2006-08-25
forum: General Help
---

### Post by Xiong on 2006-08-25
i am having trouble while building a project. It was shown that i need to set the environment variable as "export MACHINE=target".And target can be linux_pgi,linux_intel and so on.The point is that i don't where to set this environment variable.

Someone help please.

BTW:My programming platform is eclipse and language is fortran.

---

### Post by patrickthebold on 2006-08-25
You should just type it in the terminal.  type "env" to list all environmental variables.  You can also add the line to .bashrc in you home directory.

---

### Post by steve.horsley on 2006-08-25
You need to type that command into the same terminal as you are then going to run the commands to build/compile the project. So you do something like:
> cd myproject
export MACHINE=linux_intel
./configure
make


---

