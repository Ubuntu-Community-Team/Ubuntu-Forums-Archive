---
title: "Linux illogical! ls -d doesn't display directories"
date: 2007-01-12
forum: General Help
---

### Post by john_spiral on 2007-01-12
Hi,

Have you ever tried to list all the directories from a shell with the command:

**[SIZE="3"]ls -d [/SIZE]**

it only outputs:

**[SIZE="3"]. [/SIZE]**

what use is that to man or beast?

A better way of listing all the directories in the current directory is:

**[SIZE="3"]ls -d */[/SIZE]**

Think twice before you bash a Windows user for using a tangeled mass like regedit.

---

### Post by po0f on 2007-01-12
john_spiral,

Well, according to the [man page](http://web.cse.msu.edu/cgi-bin/man2html?ls?1?/usr/man):
[quote=ls man page]-d 	

If an argument is a directory, lists only its name (not its contents). Often used with -l to get the status of a directory.[/quote]

You gave your `ls -d` command **no** arguments, so it defaulted to running ls on the current directory.  And the current directory's name *is* just a dot (.) to itself, so the output should be* expected and is correct.

[EDIT]

*: s/is/should be/

---

### Post by john_spiral on 2007-01-12
> **po0f said:**
> john_spiral,

Well, according to the [man page](http://web.cse.msu.edu/cgi-bin/man2html?ls?1?/usr/man):


You gave your `ls -d` command **no** arguments, so it defaulted to running ls on the current directory.  And the current directory's name *is* just a dot (.) to itself, so the output should be* expected and is correct.

[EDIT]

*: s/is/should be/

Ummmm why would anyone wan't a dot? 

I can't even forsee it even being usefull in a program. Running the **ls -d** command would output the same result irrespective of where it was run.

Does anyone else think it's usefull?

---

### Post by pgilmon on 2007-01-12
Are you joking?

try typing this in Windows:
```
copy
```

I guess that the result isn't useful at all, but that's because you are not giving the command the necessary arguments. Does that mean than 'copy' is useless?

---

### Post by po0f on 2007-01-12
john_spiral,

[quote=john_spiral]... Running the ls -d command would output the same result irrespective of where it was run. ...[/quote]

[quote=ls man page]... When no argument is given, the current directory is listed. ...[/quote]

Exactly, you are running it with the same exact arguments.  Like I said above, **when you run 'ls' with no arguments, it defaults to the current directory**.  Run `ls -la` from a directory.  See those two entries at the very top, the '.' and '..'?

The single dot is a reference to the current directory.  It is also how the directory names itself.  This is how you are able to run executables that aren't in your path (ie, `./some_executable`).  It is also useful for getting rid of files that (for some reason) have dashes for their filename, which are passed as arguments to other commands (ie, `rm ./-i`).

The double dot is a reference to the parent directory.  Ever run `cd ..`?  You can also chain these multiple times, `cd ../../..`.

Now, try running `ls -d` *with an argument*.  You get the results you wanted.

Final thought: seriously, read the man page if you have any doubts about a command's output, or its options, or anything about it.

---

### Post by bodhi.zazen on 2007-01-12
Lol john_spiral

That is what aliases are for.

Add this to ~/.bashrc> alias lsd='ls -d */'

now type lsd to list directories

---

### Post by mrunion on 2007-01-12
@john_spiral

I see your point -- for about 2 seconds.  Give the command some more options and it'll work differently.  And a GREAT many programmers/scripts would potentially have use of "ls -d".

Oh, and before bashing Linux, think about the Window's additional resource kit(s) which allow you to include the *nix commands like "ls, cp, mkdir", etc.  they must be useful for even Windows users.

Just my $0.02.  Take it for what you paid for it.

---

### Post by john_spiral on 2007-01-12
Linux is great in every respect!

My gripe was purely from a newbie standpoint.  Thanks for all the feedback thus far.

---

### Post by Delkster on 2007-01-12
> **john_spiral said:**
> My gripe was purely from a newbie standpoint.  Thanks for all the feedback thus far.

Yeah, usually there's some kind of internal logic to things but it may not be immediately apparent because the logic is deeper in the principles of the system (like in this case) instead of always being built from a goal-based desktop view of things.

---

