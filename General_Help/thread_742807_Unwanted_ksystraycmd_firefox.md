---
title: "Unwanted ksystraycmd firefox"
date: 2008-04-02
forum: General Help
---

### Post by Njall on 2008-04-02
o Running (testing?) Kubuntu 8.04 Hardy Heron Beta (If not me, who?  If not now, when?  If not Kubuntu, what?)
o Updated multiple times a day during beta.
o Clean install.
o Firefox and all other programs installed via adept-manager
o I **do not** believe this is a bug per se.

Problem: ksystraycmd is a program which is, for want of a better term, hijacking my Firefox run.  I don't know what ksystraycmd is... I don't care.  Don't know what it does.  Don't care, though nothing actually useful that I can quickly detect.  Perhaps something arcane; but, nothing tip of my nose obvious.

I don't need a stupid Firefox icon in the "System Tray".  It is annoying my sense that I am supposed to be in charge of my system.

Every time I start Firefox apparently the command  "ksystraycmd firefox-2" is also run.  This is obvious for two reasons.  1. There a stupid, visually offensive, and totally useless ksystraycmd connected Firefox icon in the "System Tray".  2. A "ps aux | grep firefox" results in the output of a line "ksystraycmd firefox-2".   Something is kicking off the ksystraycmd and I haven't found out what.

Help?!  What is starting ksystraycmd?  How can I stop ksystraycmd?  

I would uninstall it except it is **NOT** listed under adept-manager.

Thanks in advance...

- Nelson

PS - I will be severely embarrassed if it is something simple I should have seen.  If it is something trivially obvious,  as penance, I will donate $10 to that opensource organization of your choice.

---

### Post by ryanhaigh on 2008-04-02
Could it be that the launcher you are using for firefox is set up to launch with ksystraycmd or that you have some extension installed that is doing this?

---

### Post by Njall on 2008-04-03
> **ryanhaigh said:**
> Could it be that the launcher you are using for firefox is set up to launch with ksystraycmd or that you have some extension installed that is doing this?

I wish it were that simple.  I checked that.  It isn't.  I looked at all the Firefox icons, menu and tray specifically, and ksystraycmd ain't in any of them anywhere. 

Thanks for the good suggestion though.  Great minds often go through similar ruts to get to new enlightenments.

- Nelson

---

