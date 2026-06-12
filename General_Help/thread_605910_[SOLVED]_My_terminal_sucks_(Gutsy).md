---
title: "[SOLVED] My terminal sucks (Gutsy)"
date: 2007-11-07
forum: General Help
---

### Post by MiCovran on 2007-11-07
I don't know if this is a change in Ubuntu release (I hope not) or just a problem with my installation, but Gutsy's terminal sucks. It doesn't have colors (like ls command) and tab-complete (apt-get) where it used to. These two things make it much harder to use terminal.

Is there a way to solve this?

---

### Post by bukwirm on 2007-11-07
Does Gutsy use bash as the default shell? Type "echo $SHELL" to find out - if it returns "/bin/bash", you're using bash.

If you are using bash, post your .bashrc file.

---

### Post by ajgreeny on 2007-11-07
Double check your default session setup;  mine is in colour just like every other ubuntu version I've used.

---

### Post by MiCovran on 2007-11-07
> Does Gutsy use bash as the default shell? Type "echo $SHELL" to find out - if it returns "/bin/bash", you're using bash.

If you are using bash, post your .bashrc file.
Default shell is bash and I don't have .bashrc file.

> Double check your default session setup; mine is in colour just like every other ubuntu version I've used.
Well, it is in colour, actually. I have colour in vim and telnet, for instance. I just don't have colour for ls, which is very crippling. At least that's what I've noticed.


And about this tab-complete: don't get me wrong. It works. Just not as powerful as before. I can't tab-complete anything but commands and file or directory names. So I can't use it to list available packages in apt-get.

---

### Post by bukwirm on 2007-11-07
The color ls is easy, just add this to your .bashrc file (create it if necessary, it goes in your home directory):

# enable color support of ls
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

For the tab-completion, try adding the following lines to your .bashrc:

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

I copied these out of my .bashrc file, so they work for me at least.

---

### Post by MiCovran on 2007-11-08
Nice. Thanks.

I didn't even know this /etc/bash.bashrc file exists. I added these options there instead of my home because I think no one wants to live without them. :)
Actually, this code for tab-completion in interactive shells was commented out. I wonder why. :confused:

By the way, I just noticed that bash doesn't keep command history between sessions (for using later with the up arrow). It did remember it on Feisty. I just don't understand this. Why?

---

### Post by MiCovran on 2007-11-08
> By the way, I just noticed that bash doesn't keep command history between sessions (for using later with the up arrow). It did remember it on Feisty. I just don't understand this. Why?
Ignore this, I found the problem. My stupid mistake.

---

### Post by fuoco on 2007-11-09
I also don't have a .bashrc and have missing colors and auto completion - why did it disappear and how do i get it back?

---

### Post by MiCovran on 2007-11-09
I just found a simpler way to recover .bashrc file. A copy of it is located in /etc/skel. So you can simply copy it to your home directory:```
cp /etc/skel/.bashrc ~/
```
I hope that helps.

---

