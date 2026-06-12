---
title: "Dumb terminal vs Reboot to restore"
date: 2008-03-16
forum: General Help
---

### Post by scottevan on 2008-03-16
I am setting up a group of three, publicly accessible workstations that need to run Firefox and OpenOffice. Could anyone advise me on whether I'm better off with (graphical) dumb terminals or "reboot to restore" software? I have no experience with either.

Scalability is not crucial but the ability to remotely control a workstation would be a huge plus. My budget is really limited, so I'm hoping to avoid proprietary software (eg. Deep Freeze). 

Any suggestions appreciated!

---

### Post by scottevan on 2008-03-20
I'm bumping this post b/c I know that someone out there has experience with this issue :)

---

### Post by pointone on 2008-03-20
I use what you probably refer to as the "reboot to restore" method for the Internet kiosk I developed. After each user logs off, the home directory is wiped and regenerated, and the system restarts daily, reloading from CD-ROM. This ensures the cache is always cleared out (important for an Internet kiosk) and the system is always in a "pristene" state.

Dumb terminals (vague term; I'm guessing you mean loading from a central server) were not really considered for the project. I can see it being a plus to have one central server to manage everything--but that doesn't really help much when you're only using three workstations, right?

---

### Post by scottevan on 2008-03-20
> **pointone said:**
> I use what you probably refer to as the "reboot to restore" method for the Internet kiosk I developed.
Thanks for the feedback! Are you using software that is freely available or is this a complex, undocumented setup that you originated? It sounds like you are doing exactly what I need to do.

---

### Post by pointone on 2008-03-21
I'm using the live-helper scripts from the [Debian Live]("http://debian-live.alioth.debian.org/") project. They're a relatively simple way to build customized live images with a great deal of control over the final product. Ubuntu support is planned, but it's a bit sketchy at the moment--the scripts are still in development.

I basically build an image with a minimal X install (using IceWM) and Opera, then edit a few configuration files. It takes a bit of skill to know what's going on if you want to do something advanced, though.

[Webconverger]("http://webconverger.com/") is built using Debian Live, for an example. He documents his process [here]("http://webconverger.org/develop/"), so it's probably a good template to follow.

---

