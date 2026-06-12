---
title: "KDE login failure"
date: 2007-02-26
forum: General Help
---

### Post by dregnus on 2007-02-26
Hey guys,

Last night I installed Kubuntu - Edgy on my laptop and went to sleep. Woke up this morning hoping I could get to play with my new system, however when typing in my username and password to kdm I get "login failed".

I did open up a terminal with Ctrl-Alt-F1 and successfully logged in there, as well as used sudo for a few commands, so I know that my user account exists. Any ideas to get me into KDE? I'm not logged into my system right now but I do recall that I only had about 5 hidden files in my home directory and almost all of them had to do with bash.

Thanks

---

### Post by an.echte.trilingue on 2007-02-26
Do you have a non-standard keyboard?

---

### Post by nereid on 2007-02-26
Strange problem. The files in your home directory have nothing to do with this. Maybe a *sudo aptitude reinstall kubuntu-desktop* will set everything right again.

---

### Post by dregnus on 2007-02-26
Yeah...so I tried reinstalling fresh with the alternate disk, in expert mode. And I still get the exact same problem. No idea what it is...

Also I did a sudo aptitude reinstall kubuntu-desktop. No dice there.

---

### Post by nereid on 2007-02-26
Any dicey characters in your username or password which the terminal will recognize but the Xserver won't?

---

### Post by dregnus on 2007-02-26
Shouldn't be. This the same username/password set I've been using through multiple versions of Ubuntu. Nothing but lowercase and uppercase letters.

---

### Post by nereid on 2007-02-26
Does any other window manager work or are all of them off limits? Since you installed in expert mode, normally you have to log in at the terminal, haven't you? Xserver is installed and you could start it with startx from the terminal?

---

### Post by dregnus on 2007-02-26
No other window manager is installed. Expert mode defaults to a kdm login also, not to mention that I ran it last night from a standard install and got the same error. I was unable to install from the liveCD, the partitioner seemed to give up halfway through. 

I went throught the kdm config file and saw nothing that looks to cause this. I should also mention that the man pages are displayed in some fairly messed up formatting. Every now and then it displays a random character.

I have not had much success with Edgy. The only reason I reinstalled is because the previous version 6.10 Ubuntu Edgy never worked right and finally stopped booting. I had no problems with Dapper

Thanks for the help

---

### Post by nereid on 2007-02-26
How is it with the Live CD booting and working from it is alright or also messed up (beside the problems with the partitioner)? You could try to disable the graphical login (shutdown the xdm service if my memory serves me right) and the start the Xserver from the terminal.

---

### Post by dregnus on 2007-02-26
> **nereid said:**
> How is it with the Live CD booting and working from it is alright or also messed up (beside the problems with the partitioner)? You could try to disable the graphical login (shutdown the xdm service if my memory serves me right) and the start the Xserver from the terminal.

Heh...I switched from Gentoo so I wouldn't have to do workarounds like that. The LiveCD works fine. KDE runs and its a very pretty interface. I cannot install from there though, as I cannot wipe my entire drive and the manual partition editor never comes online.

This could possibly be a bug with KDE. I have not tried reinstalling kubuntu-desktop, kde or kdm with an updated source repository (i.e. updating), as I don't have a network cable on me here at school. I think it may have something funky to do with the ' or " characters as the man pages seem to be messing up on those. Then again, that would have nothing to do with KDE. Ugh...

I'll let you know if what I do fixes the problem.

UPDATE: Able to log in by changing my password to something simpler. Not sure why this worked as I was able to log in in previous versions. But oh well. Funny man page output is also gone

---

### Post by nereid on 2007-02-27
I also switched from Gentoo. Gentoo is a really cool distro but the compiling takes too long.

---

