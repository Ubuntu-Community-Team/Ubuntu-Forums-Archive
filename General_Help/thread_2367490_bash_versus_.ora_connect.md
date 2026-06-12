---
title: "bash versus ./ora_connect"
date: 2017-07-31
forum: General Help
---

### Post by pkoukoulis-r on 2017-07-31
why is it that I cannot execute a binary using bash, but I can using the ./ method, for example, when in the current directory:

```
$ pwd
/home/xxx/C++/sqlapi
$ ./pg_connect_test 
Rows affected : 1
Rows affected : 0
$ bash pg_connect_test
pg_connect_test: pg_connect_test: cannot execute binary file

```
The same error message appears when using "sh pg_connect_test" .

---

### Post by TheFu on 2017-07-31
bash is an interpreter.  It expects a bash script.  You can't just run any program in the way you are trying.
If ./pg_connect_test is a bash script, then it would work.

BTW, you could run it as ~/C++/sqlapi/pg_connect_test too.

These are my guesses based on what you've shown above.  To really know, please post the command AND output from **file ~/C++/sqlapi/pg_connect_test**.

If you want to run it from a bash script, you can do that, but it wastes an extra process. Create a file, put this inside:```

#!/bin/bash
`~/C++/sqlapi/pg_connect_test`
```
chmod +x the file you created then run it using full or relative paths.

There are times when we might want to do something like that, but usually it is to hide the contents of a script that runs with elevated privileges, not a compiled program.  All scripts must have read privileges for the effective userid running it.  By having a 'wrapper' shell script that is allowed to run as a different userid (usually via sudo), then having the 1st script call the 2nd AFTER the escalation happened, the contents of the 2nd script can be hidden from the end user.  I don't think you want that here.

---

### Post by vocx on 2017-07-31
> **pkoukoulis-r said:**
> why is it that I cannot execute a binary using bash, but I can using the ./ method, for example, when in the current directory:

```
...
bash pg_connect_test
pg_connect_test: pg_connect_test: cannot execute binary file

```
The same error message appears when using "sh pg_connect_test" .

> **TheFu said:**
> bash is an interpreter.  It expects a bash script.  You can't just run any program in the way you are trying.
...
TheFu is correct.

Bash is, in a more general way, a programming language. So, only those scripts that conform to that programming language syntax can be run by the Bash interpreter. The simplest Bash script is just a collection of commands in a file. What Bash does is running each line in sequence.
```

#!/bin/bash
echo this is one command

# This is a comment, and the following line is a command
ps aux | grep bash

echo This is another command

```
You can open, read, and write Bash scripts with a simple text editor. Other types of scripts are Perl, Python, PHP, Tcl, etc. They are run by their respective interpreters.

If "pg_connect_test" is a binary file, it is probably produced by the compilation of the C++ code. These binary programs are run in a different way, not by Bash, but by the system's loader. They are basically run by the CPU itself, not by an interpreter such as Bash.

In Linux, to run a binary program, it needs to be in one of the directories indicated by the PATH environmental variable, or the relative or full path of the program needs to be given.
```

# This shows the value of the variable
echo $PATH

# In the current directory indicated by the dot and forward slash "./" run the program called "pg_connect_test"
./pg_connect_test

# Run the program specified by the full path
/home/xxx/C++/sqlapi/pg_connect_test

```

---

