---
title: "Palm Pilot Synchronization?"
date: 2006-12-29
forum: General Help
---

### Post by markguy12 on 2006-12-29
I'm new to Linux. It looks great, but before I jump in I need to know if there are any applications which synchronize with a Palm Pilot? I'm using the Keysuite of applications which are compatible with Microsoft Outlook. I'm not always near a PC or laptop, and having a PDA is essential. 
Anyone use a PDA (Palm OS) with a Linux desktop?
Thanks in advance.
Mark

---

### Post by mjrclark on 2006-12-29
Yes, Yes I do. A palm m515 via the usb hotsync cable. I use "KPilot Palm Pilot Tool" on kbuntu, which came as default,under menus->utitlities. If you are using normal Ubuntu with gnome, I beleive there is an equivalent programme.
Searching my package manager, gnome-pilot seems to be this, and from what I remember it works well. The only thing you might have trouble with is avantgo, which if you do not use, I would recommend, I have managed to break it in KPilot though.

---

### Post by megamania on 2006-12-29
> **markguy12 said:**
> I'm new to Linux. It looks great, but before I jump in I need to know if there are any applications which synchronize with a Palm Pilot? I'm using the Keysuite of applications which are compatible with Microsoft Outlook. I'm not always near a PC or laptop, and having a PDA is essential. 
Anyone use a PDA (Palm OS) with a Linux desktop?

There are several threads you may want to check out (try a simple search).

There are basically three choices in Gnome: Pilot-link, gPilot and jPilot.

jPilot is a clone of Palm Desktop for windows. It's easy to setup and to use, so it might be your first choice.

I just suggest you to backup your palm (on a sd card or on windows) before testing the syncing options in gnome/linux. 
For example, the first time I tried to sync in an attempt to restore my palm (i.e. copy from pc to palm), I accidentally erased all of the contents on my pc, because I assumed it would work like on windows, but it didn't. In ended up with a blank palm **and** a blank pc (it basically backed up my factory-reset palm to the pc, thus erasing my palm data on the pc). Fortunately, I always keep a backup copy of all of my data on a separate hard disk...

---

### Post by l951b951 on 2006-12-31
> **mjrclark said:**
> Yes, Yes I do. A palm m515 via the usb hotsync cable. I use "KPilot Palm Pilot Tool" on kbuntu, which came as default,under menus->utitlities. If you are using normal Ubuntu with gnome, I beleive there is an equivalent programme.
Searching my package manager, gnome-pilot seems to be this, and from what I remember it works well. The only thing you might have trouble with is avantgo, which if you do not use, I would recommend, I have managed to break it in KPilot though.

Maybe I'm doing something wrong then.
I'm new to Linux and I've installed Ubuntu on a used laptop.  I used synaptic to install kpilot, and kontact (actually most of the KDE organizing software).  However, my desktop is gnome.  When I use kpilot, it backs up all my databases, but I can't access them in kontact, korganizer, or anything.  I have tried changing the destination file of the conduits (not location) and nothing. I have tried importing and adding the "std" vcards but can't get any contacts in my kontact.  However the database files have been copied to my harddrive.  Am I wrong for using KDE software on a Gnome desktop or am I missing something obvious here as far as set up?

---

### Post by jeremy on 2006-12-31
There is a known problem with kpilot on edgy, hopefully it will be fixed soon.

---

### Post by jonrkc on 2007-01-20
It can be a new problem (since December) on Dapper, also. See

[http://www.ubuntuforums.org/showpost.php?p=2041155&postcount=30](http://www.ubuntuforums.org/showpost.php?p=2041155&postcount=30)

for my solution, and also others' posts there.

---

