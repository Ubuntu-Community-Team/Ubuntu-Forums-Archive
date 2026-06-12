---
title: "Is it me, or is EVERYTHING slower on Breezy?"
date: 2005-10-29
forum: General Help
---

### Post by docmanny on 2005-10-29
I was running Hoary before, slow bootup, but everything else was OK.
With the Breezy upgrade, I have to wait like 5-10 seconds between clicking on icons and opening windows. I have the basic install without adding a lot of junk, so what's up??

---

### Post by matthew on 2005-10-29
I haven't had that experience at all and I've installed Breezy on four computers. All of them are faster than they were with Hoary.

---

### Post by Qrk on 2005-10-29
It could be an xorg problem. Xorg can take a lot of resources if it isn't configured right.

---

### Post by eyebrowman92 on 2005-10-29
breezy is faster for me too. do you have any partitions on your hard drive?

---

### Post by aysiu on 2005-10-29
I don't know if it's just you, but it doesn't seem as if most people are experiencing that.

---

### Post by Mosey on 2005-10-29
How exactly does one go about configuring xorg...

My computer has too few resources already...so i'd be interested in speeding things up a little.

---

### Post by SilentCacophony on 2005-10-29
[QUOTE=Mosey]How exactly does one go about configuring xorg...

My computer has too few resources already...so i'd be interested in speeding things up a little.[/QUOTE]

Open a terminal and enter:

**sudo dpkg-reconfigure xserver-xorg**

Then carefully consider each step. You may want to wirte that down in case you really make some bad choices and have to do it again. ;) Seriously, it's usually pretty painless.


As for the **OP,** may be worth a try to run that, too. Breezy has been pretty snappy for me.

---

### Post by dhess31 on 2005-10-29
It's extremely fast foe me, but then again I have a pretty beefy PC.  Do you have an older computer?  If so, you might need to use a lite-weight window manager instead of Gnome or KDE.

Don

---

### Post by az on 2005-10-29
The (last) preview release was a little slow because of some rendering issues, but that got worked out. Are you up-to-date?

---

### Post by docmanny on 2005-10-29
I used my old xorg.conf file and it seems to be comparable to Hoary now. Firefox was taking forever before.

I've got a P4-3.0 with 1GB RAM. Shouldn't take 10 seconds to open a window (except with Open Office...)

---

### Post by mustang on 2005-10-29
It's about as fast as Hoary was for me.

---

### Post by moopere on 2005-10-29
[QUOTE=docmanny]I was running Hoary before, slow bootup, but everything else was OK.
With the Breezy upgrade, I have to wait like 5-10 seconds between clicking on icons and opening windows. I have the basic install without adding a lot of junk, so what's up??[/QUOTE]

Its about as fast as Hoary for me (and about the same as Warty).  However, this is not to say that things are fast.  

In fact, the only place where Gnome is fast is on my 3GHz HT 512MB machine, on everything else, from a P1-166MHz -> P3 1GHz Gnome is really really slow.

I've been desperately trying to find something that works and works reasonably well.  KDE works pretty well on much lower end machines (not the P1, but anything 300-400Mhz with 256MB or more). however Kubuntu is/has suffered from any number of 'polish' issues, which is a seperate issue which I won't go into here.

What I've found rather interesting is that during my search for a responsive desktop environment I tried out XFCE.  Theres a lot to like with XFCE, and the Xubuntu group is trying to iron out a lot of the wrinkles that are left, however, the interesting bit for me is that XFCE, whilst definately lighter on RAM  does not actually come across as much more responsive to the user.

I wonder why this is?  Is GTK ultimately to blame for Gnome being so slow?

Hmm

Craig

---

### Post by munkymonkjr on 2005-10-30
i am getting hoary-like speeds. that is not all that fast, but not slow at all. as for firefox, i don't know but i think the developers screwed it up pretty bad. Install Epiphany or Opera and use taht....solves a lot of issues in terms of speed and stability.

---

### Post by docmanny on 2005-10-30
OK, so its pretty slow again this morning. Click on file folder, wait... about 5 seconds before a screen pops up and then a few more to list the contents of the folder.

Here's the partition setup: (lots of storage for pictures and home videos)

hda: 120 GB IDE
   hda1: Win2K
   hda2: Linux (not used)
   hda3: Fat32 for files mounted as /windisk

hdb: 300GB IDE
  one partition for /storage. Not accessed normally

sda: 200GB SATA (this is the boot drive)
  sda1: /boot-- 250 MB
  sda2: / -- 6GB
  sda3: extended
    sda5: /home --6GB
    sda6: /files-- for data storage -- 175GB
    sda7: /swap -1.5GB

Again, its a P4-3.0 with 1GB RAM. What's my problem??

---

### Post by Dracontopes on 2005-10-30
Is DMA enabled?

Maybe this will help: ```
gconf-editor
``` and look for reduced_resources (it's a key) and enable it... Don't know if it will make a BIG difference but it speeded things up a little on my rig.

---

### Post by WishMaster on 2005-10-30
The only things that goes slower in Breezy is Synaptic...
When I do a search, it takes much longer than in Hoary.

---

### Post by kazuya on 2005-11-08
I do not know if my problem is due me get ubuntu breezy too early at the experimental stage, but I have the same issue too. My bootime is like 5 minutes. And upon opening and trying open folders or anything it does feel a world slower. Should I ensure that I download the proper or most upto date breezy?

It is like the slowest linux OS I have ever installed. I installed knoppix on the same drive, and it was incredibly fast with kde 3.4, so something is off in my install or boot CD?

Even with xfce and kubuntu, it is a little faster. 

The ISO I downloaded was probably an experimental breezy, because I was posting in the development post section, could this be correct. I figured upon update, evrything should match what is out there and the test breezy should match the current breezy?

---

### Post by denisesballs on 2005-11-08
> Is it me, or is EVERYTHING slower on Breezy?

It's you. :)

---

### Post by jnk on 2005-11-08
[QUOTE=WishMaster]The only things that goes slower in Breezy is Synaptic...
When I do a search, it takes much longer than in Hoary.[/QUOTE]
Well, default in Hoary is to search "name" but in Breezy default is to search "name & description".

---

### Post by eyebrowman92 on 2005-11-08
[QUOTE=denisesballs]It's you. :)[/QUOTE]
i agree.;)

---

