---
title: "P2P problems!"
date: 2007-04-08
forum: General Help
---

### Post by mattgsx on 2007-04-08
So, every time I try to open gtk-gnutella (which I ran without issue for weeks) or Frostwire (which I just installed), the programs will begin opening and then immediately close. They don't crash (or I don't get crash reports), but they don't stay open. Gnutella doesn't even appear on my taskbar as an open application. My processor just grinds for a few seconds and then stops.

Has anyone else had this problem? What can I do about it?

---

### Post by mattgsx on 2007-04-08
Additional apps:

Azureus and BitTorrent also do this. No problems with any of them previously, and I don't remember changing anything.

---

### Post by zanglang on 2007-04-08
Try running any of the programs from command line, and see if they dump out any weird error messages? You might have installed/uninstalled something essential for them to run, causing them to crash.

---

### Post by indigoshift on 2007-04-10
> **zanglang said:**
> Try running any of the programs from command line, and see if they dump out any weird error messages?

I was having the same problem, so I did this, and got the following message:

> *** ANCIENT VERSION DETECTED! ***

Sorry, this program is too ancient to run without
an explicit user action: If it's not possible to upgrade
you may edit the file

        /home/indigoshift/.gtk-gnutella/config_gnet

and set the variable "ancient_version_force" to
"gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)".

You will then be able to run this version forever, but
please consider upgrading, as Gnutella is an evolving
network in which ancient software is less useful or even
harmful!


Setting this variable (scroll down to line 742) fixed the problem, and it's running for me just fine now.

What's funny is that the most recent version of gnutella I've been able to find is 0.96.1, yet it freaks out and says it's an ancient version.  *shrug*

EDIT:  Looks like the latest version is 0.96.3, which I found out about on [this thread]("http://ubuntuforums.org/showthread.php?t=399171&highlight=gnutella").  ;)

---

