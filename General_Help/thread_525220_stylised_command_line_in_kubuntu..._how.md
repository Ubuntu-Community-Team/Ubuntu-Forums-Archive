---
title: "stylised command line in kubuntu... how?"
date: 2007-08-14
forum: General Help
---

### Post by rextor on 2007-08-14
I found that i backtrack2 (and many other bootable OSes) that the command line can be stylised.. that is smaller fonts, background images and the likes.. and these are only command lines and not the complete GUI.

How do i do this with Kubuntu?

---

### Post by apetresc on 2007-08-14
KDE's standard terminal app, the "Konsole", is very configurable. Open it from Menu->System->Konsole. From there you can go to "Settings->Configure Konsole" and select the "Schema" tab. From there you can customize the look of the Konsole completely.

Good luck :)

---

### Post by Steve1961 on 2007-08-14
You can also edit .bashrc for coloured prompt.  Here's teh relevant section of my .bashrc file:

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
PS1='\[\e[32m\]\u@\h/\[\e[1;31m\]\w\[\e[1;34m\]\$\[\e[0m\] '

---

### Post by rextor on 2007-08-14
Yeah AdrianP.. i've been using konsole for a long while. I guess you did not get my question right.. or probably i wasn't as clear in explaining my query..

What i meant to say was that.. in backtrack, init 3 would drop you into a command prompt which was much more attractive than the standard command prompt that we get with Ubuntu or RedHat. What is the package that they use there?

---

### Post by kellemes on 2007-08-14
> **rextor said:**
> Yeah AdrianP.. i've been using konsole for a long while. I guess you did not get my question right.. or probably i wasn't as clear in explaining my query..

What i meant to say was that.. in backtrack, init 3 would drop you into a command prompt which was much more attractive than the standard command prompt that we get with Ubuntu or RedHat. What is the package that they use there?

Steve is giving you the hint you need.
Google for customizing your bashprompt using .bashrc

---

