---
title: "Evolution crashes at start up (edgy)"
date: 2007-04-05
forum: General Help
---

### Post by qrdl on 2007-04-05
Hello!

I have a problem with evolution

I've installed Ubuntu 6.10 (amd64) couple of days ago, updated it (something like 170 packages were updated), installed l10n packages for FF an OO and that's it. When i try to start evolution it fails. Starting evolution from terminal leads to this:

specter@specter-laptop:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.8:4629): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.8:4629): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

** (bug-buddy:4637): WARNING **: Couldn't load icon for Open Folder
specter@specter-laptop:~$ 

and evo fails.
Can anybody help me?

---

### Post by kabuto_san on 2007-04-19
I've the same problem.... and I tried with: 

***evolution --disable-eplugin***

But, I've not fixed the problem....

Kabu

---

