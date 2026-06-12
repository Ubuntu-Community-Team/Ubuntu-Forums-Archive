---
title: "[SOLVED] The linux terminal is magic"
date: 2008-03-11
forum: General Help
---

### Post by Kenchu on 2008-03-11
I've been wondering about the terminal in ubuntu. How is it that it knows what commands are relevant when running different programs? You know, when you press tab. For example, if I do sudo apt-get --p and then press tab, it knows I mean --purge, and then I kan do r tab -> remove. Arent --purge and remove arguments to a program called apt-get? How would that work? How can the terminal "know" what arguments (or programs?) that are related to this command?

Love

---

### Post by aysiu on 2008-03-11
It's called *autocomplete*. It looks for the possible commands that could finish what you started typing.

---

### Post by Kenchu on 2008-03-11
Great! And how does it work? How does it know what arguments the program can receive? In windows when you press tab, all it does is to look for files in the current folder matching what youve written, while in ubuntu it seems to look like everywhere + arguments. o.O It is especially that argument that I am curious about.

---

### Post by azimuth on 2008-03-11
You can type "help" at the CLI to get a list of many of the builtin bash commands. Then you can type "help command" to see the options for a command. There is also a path that is set to check all of the /bin locations for executable files. Example: When you type firefox at the command line, the program firefox will be found within the path and executed.

---

### Post by Kenchu on 2008-03-11
What about apt-get --purge/install/remove? What exactly are --purge, install and remove? Arguments? Programs? If programs, how come i cant use them seperately? If arguments, how does ubuntu "know" that apt-get has those arguments? If I made and compiled a C program that can handle arguments, would ubuntu automaticall know what arguments it handles? (I guess thats a no, so why does it work with apt-get?)

---

### Post by koenn on 2008-03-11
bash uses the program 'complete' and a script /etc/bash_completion to accomplish this. 
I guess if you really want to get to the bottom of this, you'll have to study the source of 'complete' (no man page, apparently), or see if you can find online documentation

---

### Post by mali2297 on 2008-03-11
[An introduction to bash completion]("http://www.debian-administration.org/articles/316")

---

### Post by sajro on 2008-03-11
> **Kenchu said:**
> What about apt-get --purge/install/remove? What exactly are --purge, install and remove? Arguments? Programs? If programs, how come i cant use them seperately? If arguments, how does ubuntu "know" that apt-get has those arguments? If I made and compiled a C program that can handle arguments, would ubuntu automaticall know what arguments it handles? (I guess thats a no, so why does it work with apt-get?)

They are called "switches" and are like mini programs. Apt-get itself is a package manager and switches tell it what part of itself it needs to use. Visualize it like files.
```
/home/billy_bob/movies/persopolis.ogg
is like
/apt-get/install/amarok
which means
apt-get install amarok
```

Hope that helped.

---

### Post by Kenchu on 2008-03-11
Thanks guys. I guess this pretty much cleared it up. :)

---

