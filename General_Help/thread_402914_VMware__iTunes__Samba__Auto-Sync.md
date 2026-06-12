---
title: "VMware / iTunes / Samba / Auto-Sync"
date: 2007-04-06
forum: General Help
---

### Post by signul9 on 2007-04-06
Any known issues with auto-syncing an iPod, within an XP Virtual machine, that targets a samba share?

---

### Post by strabes on 2007-04-06
Why are you using a virtual machine to sync your ipod? There are plenty of native linux programs that sync ipods. Off the top of my head, gtkpod (for gnome) & amarok (for kde) work easily.

---

### Post by signul9 on 2007-04-06
Hi Alex,  

Tried 'em all... still want my iTunes.   (Podcasts, Movies, Music Vids, DRM etc.)  I like where Songbird is going, but I don't think its quite where I would like it yet.  Amarok and GTK I didn't vibe with.

---

### Post by mortsahl on 2007-12-29
If you figure out a way to sync my iPod Touch with Linux, let me know.  In the meantime, anyone have luck with VMWare/iTunes/iPod Touch?

---

### Post by dweazle on 2008-01-23
I'm having the same problem with my iPod touch. My iPod nano 1st gen works fine though.

It appears to be a problem with how VMware handles USB communication.

See this thread at VMware for more info and post a reply :)

[http://communities.vmware.com/thread/91715?tstart=0&start=120](http://communities.vmware.com/thread/91715?tstart=0&start=120)

---

### Post by rshel on 2008-01-25
> **strabes said:**
> Why are you using a virtual machine to sync your ipod? There are plenty of native linux programs that sync ipods. Off the top of my head, gtkpod (for gnome) & amarok (for kde) work easily.

Not the Gen6 Ipods.  Apple, in their slimy corporate greed, made it almost impossible to use with anything but ITunes.  May they burn in hell forever.

---

### Post by phillywize on 2008-02-04
> **rshel said:**
> Not the Gen6 Ipods.  Apple, in their slimy corporate greed, made it almost impossible to use with anything but ITunes.  May they burn in hell forever.

Well, it's not THAT bad...see here:

[http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)

Instructions on how to get Amarok, etc., to play nice with a 6g.  Or the other way around, I guess.  At any rate, to the extent Amarok, gtkpod, and the rest of the linux solutions support the iPod, they'll support the 6g.  6g support aside, I think itunes still does the best job of any of them.  Running windows in a VM so you can have iTunes makes complete sense to me in that regard; did it myself until I got a 6G...which for reasons that have less to do with apple and more to do with the state of usb support in virtual machines, doesn't sync with itunes in a virtual machine.

Here's a thread with some info on getting up to a 5.5g to work with iTunes 7.3 and windows 2k.  I know, crude, but it seems like the best I've been able to come up with.

[http://ubuntuforums.org/showthread.php?t=614208](http://ubuntuforums.org/showthread.php?t=614208)

I should add this in response to the opening post of this thread:  I've had no problems syncing from a samba share into a windows virtual machine.  Just be sure to permanently set a drive in windows so you can configure itunes to look for the itunes library in a consistent place.

---

### Post by spikenick on 2008-03-04
Those of you who keep recomending linux native programs, please go away and stop making pointless critics, and as the guy said they are troublesome and require fixes. Plus if you get it to work like me it cant do all the things needed for the new fancy ipods.

---

