---
title: "trouble installing pysqlite"
date: 2007-12-24
forum: General Help
---

### Post by vizitorq on 2007-12-24
i installed pysqlite2.3.5.tar.gz as directed. and when i ran the command:```
me@box:~/pysqlite-2.3.5 % python setup.py build
```

it gave several lines of errors and at the end```
error: command 'gcc' failed with exit status 1
```

so then i read that i should look at customizing my build by editing the setup.cfg file. but when i got there i had no idea what to do. can anyone help me? python-friendly :confused:

---

### Post by pjkoczan on 2007-12-24
It's possible that the setup script isn't finding some shared libraries. I've seen this with configure scripts many times. You might need to set some environment variables (LDFLAGS, PYTHON_HOME) and re-run the setup script. Read the README or online docs to see exactly what you're doing. Basically, without properly finding those libraries, gcc can't create assembly output, and the script thinks that gcc is broken.

Also, there is probably some sort of setup.log file that details the output of all commands (it's called config.log with configure scripts). Read through it to find out the problem.

---

### Post by vizitorq on 2007-12-24
so how do i setup environment variables? how do i know which ones to change and what to change them to?

---

### Post by vizitorq on 2007-12-24
actually it was easier than that. sudo apt-get install python-sqlite

---

### Post by pjkoczan on 2007-12-25
> **vizitorq said:**
> so how do i setup environment variables? how do i know which ones to change and what to change them to?

Good to hear that it's resolved, but to set environment variables, you should use one of the following:

in bash (likely what you're using): export [VARIABLE_NAME]=[VALUE]
in tcsh: setenv [VARIABLE_NAME] [VALUE]

For instance, if you want to add a new directory to your path ([http://en.wikipedia.org/wiki/Environment_variable](http://en.wikipedia.org/wiki/Environment_variable)), you'd type export PATH=$PATH:/new/path/to/search

Compiling software can be tough, work at it if you find that you need it, and use READMEs. In any event, good to hear that you found a solution.

---

