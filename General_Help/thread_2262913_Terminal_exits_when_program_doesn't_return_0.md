---
title: "Terminal exits when program doesn't return 0"
date: 2015-01-28
forum: General Help
---

### Post by calzakk on 2015-01-28
Hi all,

I'm running a proprietary program from Konsole using:

[INDENT]export LD_LIBRARY_PATH=`pwd`/../../libdir
./program[/INDENT]

The program loads a shared library that's in another directory.
If the program returns 0, everything's fine.  But if the program returns 1 - to indicate an error - then the shell exits and Konsole disappears!

But if I move the library into the same directory as the executable, and use just `pwd` for LD_LIBRARY_PATH, then all is well!

So why does the library cause a problem?  Why does it matter that it's not in the same directory as the executable?  Is this a bug within the shell?  (Although it happens with both Bash and Dash!)

Thanks in advance for any insight :)

---

### Post by calzakk on 2015-01-30
Any ideas from anybody?

---

### Post by Erik1984 on 2015-01-30
What If you try this in another terminal application like xterm (you probably have that installed already), does that other terminal application close too?

---

### Post by kpatz on 2015-01-30
The terminal exits when the initial shell for the terminal ends.  This is what happens when you type "exit" or Ctrl-D at the prompt, it causes the shell to exit.

Normally a program launched from the shell won't cause the shell to terminate, unless it's launched with the "exec" command, or in the case of a shell script, run within the current shell by entering ". (path_to_script)".

Is "./program" a binary or a shell script?  Are you accidentally adding a space between the dot and the slash?

What happens if you launch a child shell (just run bash from the prompt) and then launch the program?

Try using an absolute path to the library for LD_LIBRARY_PATH instead of the path relative to pwd.

Another possibility is that the program is sending the parent process (the shell) a signal which is causing it to terminate.

Try this command before launching your program:

```

for (( i=1; i<65; i++ )); do trap "echo caught signal $i" $i; done
trap 17
trap "echo Shell exiting in 5 seconds" 0

```

When the program terminates with a non-zero exit code, see what signals get caught.  The above script sets up traps on all signals except 17 (SIGCHLD).  17 fires anytime a child program finishes; this won't terminate the shell, so no need to trap that one.  The trap on signal 0 (which fires right before the shell terminates) displays a message and then sleeps for 5 seconds so you can see what happened before the window closes.

---

### Post by calzakk on 2015-02-02
@Erik1984:
Yes, it happens with XTerm and Terminator too.

@kpatz:
./program (no space between the dot and slash) is a compiled program. (I'm using g++ and scons to build it).
If I launch a child shell then this will exit when the program fails, and return me to the original shell.
The LD_LIBRARY_PATH is actually an absolute path.
No signal was caught if I used your command.

Thanks for your help guys.

---

### Post by calzakk on 2015-02-02
I've figured it out!

I neglected to mention that before running scons to build the program, we run an initialization script that sets up a few things:

[INDENT]. ./init.sh[/INDENT]

(There's a space between the two dots.)

And this script contains:

[INDENT]set -e[/INDENT]

If I comment this out, then the program *doesn't * cause the shell to exit! So the set option (-e "Exit immediately if a command exits with a non-zero status") is being brought into the shell, and this will cause it to exit when *anything* returns a non-zero error code. D'oh!

---

