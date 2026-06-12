---
title: "Command-line shortcut: Repeat last command, but..."
date: 2013-04-21
forum: General Help
---

### Post by GameX2 on 2013-04-21
Hi,

Simple question; I would like to repeat the last typed command in the terminal.  I already know about the " !! " command, but it's not exactly what I want to do, in that case.

Assuming I type " sudo apt-get install audacity ".  On the next command I type, I want to avoid retyping "sudo apt-get install", and only change the last word.
Another example would be with gksudo: " gksudo gedit "~/textfile.txt".  I would like to only change the last word (well, everything in brackets).

How can I do this?

Thanks!

---

### Post by teeth on 2013-04-21
I think you can just hit the up arrow key and it will re enter your last command, then use the arrows to move around and edit it.

---

### Post by GameX2 on 2013-04-21
Yes, that's a great way to do it, but can I avoid it?
A trick to repeat the last command, excluding the last word ?

---

### Post by steeldriver on 2013-04-21
Well you could try: up arrow followed by Ctrl-Alt-h (delete word to the left of current cursor position)

---

### Post by Lars Noodén on 2013-04-21
AFAIK, teeth has covered your options.

You could do subsitution,

```

sudo apt-get install audacity
^audacity^tinyfugue

```

but that would be about as much work as *up arrow + backspace*, or *up arrow + ctrl-w* will delete the last word.

---

### Post by Lars Noodén on 2013-04-21
For a complete list of options see the manual page for [bash](http://manpages.ubuntu.com/manpages/quantal/en/man1/bash.1.html) and scroll down to "Commands for Moving"  That and the next few sections have a lot of options.  M there stands for meta, which is usually the escape key (esc).

---

### Post by matt_symes on 2013-04-21
Hi

Bash history expansion is very powerful and there are many little known features.

In the terminal look at the relevant section in the man page with

```
man bash | less +/"^HISTORY EXPANSION"
```

Just an addendum to Lars' excellent advice, a quick way to get there.

```
man bash | less +/"Commands for Moving"
```

Copy and paste both into the terminal. 

as an extension to ajgreeny's excellent advice about the usefulness of alias...

...these are also good things for alias. Sections in man pages you use alot.

```
alias hise='man bash | less +/"^HISTORY EXPANSION"'
```

```
alias cfm='man bash | less +/"Commands for Moving"'
```

I have found this use for aliases very useful when learning something.

Kind regards

---

### Post by GameX2 on 2013-04-21
I'll check this, thanks!

For now, I can imagine a workaround...
How about running a script.  The script will have an alias to " R! " (Let's say R for Repeat).  The script will select the last line from .bash_history, then delete the last word, and store it into a variable.  Then, execute the variable.

I guess it should work..  But I'm not sure how.
(So much work for so much laziness. XD)

---

### Post by ajgreeny on 2013-04-21
How about using aliases instead of a simple repeat of the last command, eg ```
alias sagi='sudo apt-get install'
```added to your home's .bashrc file.

I use lots of aliases for all sorts of actions that are quicker to carry out in terminall than using a GUI application.

---

### Post by GameX2 on 2013-04-21
> **ajgreeny said:**
> How about using aliases instead of a simple repeat of the last command, eg ```
alias sagi='sudo apt-get install'
```added to your home's .bashrc file.

I use lots of aliases for all sorts of actions that are quicker to carry out in terminall than using a GUI application.

I have already put an alias for Sudo Apt-Get Install. ;)
Mine is " agi ".  Also have " agu ", " agr " and " aga (Apt-Get Autoremove) ".


I just can't seem to get my script do the thing I want, exactly.  I use " tail " to select the last line from the file ".bash_history", but for some reason, not every command I type the terminal are added to the file.

---

### Post by steeldriver on 2013-04-21
... I don't get how that's easier than 2 keystrokes (up-arrow + Ctrl-w) :confused:

---

### Post by GameX2 on 2013-04-21
I read quite often "A Linux user is lazy". ;)
Well, doing "R! audacity" (R! for repeat last command, exclude last word) would be OK as well.

I know, that's a lot, for extreme laziness. XD

---

### Post by matt_symes on 2013-04-21
Hi

I just updated my post #7 with some information that you may (or may not) find useful :)

Kind regards

---

