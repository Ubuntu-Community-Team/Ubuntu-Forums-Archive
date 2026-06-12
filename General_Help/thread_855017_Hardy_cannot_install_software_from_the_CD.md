---
title: "Hardy cannot install software from the CD?"
date: 2008-07-10
forum: General Help
---

### Post by jubilee33 on 2008-07-10
I have an odd problem here.  It's no big deal but it's really strange.  Whenever I try to install some applications from the CD (if they happen to need the Hardy i386 CD), I keep getting the same message again and again in my terminal:

please insert the hardy cd to /cdrom/, and press enter.

Of course I comply but nothing happens.  It's as if the CD is never there.  My CD is perfectly good.  My solution for now is that I removed CD from the software sources and download everything from the repositories.

Is this a bug?  Or is there something that I messed up?

---

### Post by iaculallad on 2008-07-10
Make sure that you uncheck the CD/DVD-ROM source in your Software Sources.

System->Administration->Software Sources, and under "Ubuntu Software" tab, see to it that the "Installeable from CD-ROM/DVD" option is uncheck.

Place a check mark forMain, Universe, Restricted, and Multiverse.

Download From: Main Server.

Click on Close button and on the next windows that shows, click on Reload.

and on the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Vivaldi Gloria on 2008-07-10
Put in your cd. Start synaptic. Goto Repository settings from the settings menu. Add the cd as a repo. Close the settings dialog. Press the refresh button. 

Now if you install a program in synaptic the cd is used if it has the program. This is transparent. It DOES use the cd if it has the program.

But since it's a hassle to put the cd in every time I say don't bother using it as a repo and it's OK to remove it from repos.

---

