---
title: "terminal, bash, and quick questions!"
date: 2014-07-10
forum: General Help
---

### Post by thexnightmare on 2014-07-10
Dear ubuntuers,
I am new to ubuntu and switched from windows, and I wasn't imaging how much the system is stable, good and flexible.
I have a quick quesitons which are still not clear for me:

1- I know that there is terminal, tty what are the differences between them?
2- What is bash? and does it the same as SSL and SSH?
3- What are .sh files?
Thanks

---

### Post by ajgreeny on 2014-07-10
Terminal is generally thought of as the GUI application, eg gnome-terminal, xfce4-terminal, etc etc, in which you run commands.  Linux uses different run levels; in Ubuntu there are six tty command lines available from Ctrl+Alt+F1-6, and the GUI, which sits at run level 7, Ctrl+Alt+F7.

Bash is the shell  used to run many distros' commands, though there are many other shells that can be used, eg csh, zsh, fish, but you don't really need to bother about that as the default shell for Ubuntu is bash.  However any commands run at boot by the system, as opposed to run by user, make use of dash (bin/sh).  Complicated, but as I say, you don't really need to bother about the differences in normal use.  See [http://askubuntu.com/questions/161705/what-is-the-default-shell-and-are-there-any-other-options](http://askubuntu.com/questions/161705/what-is-the-default-shell-and-are-there-any-other-options) for more info.

.sh files are shell scripts, text files that can be run like commands, either in a terminal or directly by the system, for example, at boot.  They are often likened to batch files (file.bat) in windows and they do have similarities, but can also be quite different.  See [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting) for more detailed info.

---

### Post by thexnightmare on 2014-07-12
Thanks for your clarifications.

1. So, terminal is just a tty inside the GUI to be able to run command while you are in GUI right?
2. What is the tty exactly? and does the in interface of kernel with he user? in another word, it is the terminal of kernel?
3. I understood the shell is the console which allow do series of commands to linux, these commands are categorized into some kind of structures like bash, csh, zsh, etc.., right? and .sh is just a combination of routines which are executed and managed by the bash in another way shell), right?

---

### Post by grahammechanical on 2014-07-12
> [COLOR=#000000]1. So, terminal is just a tty inside the GUI to be able to run command while you are in GUI right?[/COLOR]

No. The Terminal (A.K.A., Gnome Terminal) is a terminal emulator that runs in the Graphical User Interface (GUI), which itself is running in tty7.

If you press Ctrl +Alt+F2 you will get a tty. To get back to the desktop GUI press Ctrl+Alr+F7

TTY = TeleTYpewriter. It dates from the days when computers communicated with the operator by printing on paper. It was later when computers could print to Cathode Ray Tube (CTR) screens and "ECHO" to the screen what was typed at the electromechcanical hardware device that was used for entering data into the computer and displaying data from the computer that the terminal/workstation was called a console.

What we have here are names and labels being used in new ways as computers developed. Linux can switch between 7 virtual terminals or virtual consoles. Think - a conceptual combination of keyboard and display for a User Interface.

TYY1 to TTY6 give us a text terminal with a login to a Unix shell. TTY7 is where the X window system runs. On Linux we use a re-mix of the Unix shell intended to be a free replacement for the Bourne shell. So, it was called the Bourne Again Shell (BASH). SH is an abbreviation for shell = command-line interpreter.

Back in the days before Linux got the X window system and a Desktop Environment with a Graphical User Interface, these virtual terminals could be used for multitasking as each terminal could run a different program.  Microsoft DOS could not do that until it got Windows 3 and even then, if one program crashed it brought down the entire OS but on Linux each tty/terminal/console was isolated.

It is amazing what one can learn from a simple Wikipedia search. It can make a person seem educated! :) Ask quick questions - get quick answers and learn little.

Regards.

---

### Post by buzzingrobot on 2014-07-12
The way the word "shell" is used in this context means the program the system executes and that, in the absence of any other program being executed, displays a prompt and awaits input from the user. Because Unix was created before graphic displays were practical, all interaction with Unix was with text:  entering commands with a keyboard.  The program that displayed the prompt, accepted commands entered by a user, parsed them and passed the commands along to the system for execution was called the "shell". When a program terminates, control returns to the shell and its prompt is again displayed.  The shell is analagous to, but much more capable, than the command.com program used in DOS prior to Windows.

In typical Unix fashion, the name of the shell program was "sh". A good number of other shells have been implemented since then.  Bash is the shell used in Linux, as well as OS X.

In a GUI environment, a terminal,  AKA "terminal emulator", is a program that launches a shell (Bash) and displays its prompt in a window.  Multiple independent instances of Bash can be executing at any given time. 

"Terminal" being a word from the ancient days of Unix applied generically to a an actual text-based monitor, and emulator being a little GUI package that emulates the behavior of those physical terminals.  Unlx, and Linux, are capable of supporting multiple independent users simultaneously. (That's why there's a "home" directory where sub-directories for every user are created.  Today, it's usually just one user, but it doesn't have to be.) Originally, it was common for various users to work off a single Unix machine, each with their own keyboard and their own terminal display.

---

