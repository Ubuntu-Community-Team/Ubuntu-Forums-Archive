---
title: "Evolution getting floating point exception"
date: 2007-11-10
forum: General Help
---

### Post by dre1187 on 2007-11-10
Hey everyone,

This is the problem that I have been having, anytime that I try to load evolution it crashes nautilus, and when I try to load it up from terminal  I get this:

CalDAV Eplugin starting up ...
Loading Spamassasin as the default junk plugin
Floating point exception (core dumped)

Now if  I try to load it up without any plugins it loads, but then as soon as I do anything, it crashes. 

Any ideas on how to fix, I have looked around, but to no avail. 

Thanks in advance, 
Andre

---

### Post by jhorner on 2008-01-23
I am having the same issue.  I assumed it was Evolution being to "beefy" for my legacy laptop. Below is the error I receive 

[I]justin@ubuntu-t23:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:5522): DEBUG: mailto URL command: evolution %s
** (evolution:5522): DEBUG: mailto URL program: evolution
Floating point exception (core dumped)
[/I]

Any suggestions?

---

### Post by zolw on 2008-01-28
Go here:

[https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/133692](https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/133692)

Change icone theme. worked for me.

---

