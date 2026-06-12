---
title: "HELP Kubuntu destroyed by trojan"
date: 2007-01-02
forum: General Help
---

### Post by larryalk on 2007-01-02
My perfectly working Kubuntu 6.06 Dapper Drake system will not boot any more after I made the mistake of copying an email web page and going to an eBay site that claimed to have a search result I had been looking for.

A dumb mistake I have warned my wife about a dozen times!

While on the site using first Opera then Firefox in KDE the entire system started going wanky.  Even terminal programs ceased to respond.

Then a blue 3"x2" logo started popping up with something that could be a dragon and the word Sceptre which I think is a known trojan.

Nothing will boot and somewhere in the process I reset the cmos and now it won't even respond to a keyboard DEL to get into the BIOS.

I think _that_ box AMD is kaput so I tried some others.

With hda in another AMD box I can boot to a terminal but cannot get into X - possibly because of the difference in video cards.

In another Intel box the boot process Grub starts and i get only the first three blue lines and the process then stalls forever:
1.  Loading essential drivers        X
2.  Mounting root file system
3.  Waiting for root file system    Stalls here

If I can't fix the existing system I have two options:
1.  Find a box that will work and install Breezy onto a new drive, then copy over home and upgrade.
2.  or install Breezy again and copy over a USB backup drive that is about 10 days old.

I've also tried to load AVG Antivirus but the available Ubuntu versions seem to require Gnome or KDE running - right now I'm terminal bound.

I was hoping to wait until the Feisty Fawn to upgrade.

Can anyone give me some pointers on how to get out of this mess?  Something perhaps to reset Grub?  I'm used to LILO and don't know much Grub.  Should I do anything with the MBR?  

I just feel so dumb :-(

Larryalk
Written on my ham radion Windows slow machine

---

### Post by bulldog on 2007-01-02
Where you logged in as root?,otherwise there couldn't be much harm done.

**EDIT:**
If you have an USB keyboard and you reset the CMOS it's quite possible it disabled the USB support.
If you can connect another keyboard [wired] you can most likely enter the BIOS again,and correct the settings.
Can't imagine your BIOS is destroyed by a trojan.

---

### Post by happy-and-lost on 2007-01-02
A Linux virus... that sounds very unlikely. You'd have to give something root permissions for it do do that sort of damage. If your CMOS is screwed, you'd be best taking it to a computer repair person, I don't think you can do much for a broken CMOS yourself...

---

### Post by Bastanteroma on 2007-01-08
Could something like this be caused not by a Linux virus but a opera exploit?

Something similar happened to me.  I asked Ymail to scan an attachment I suspected was a virus, thinking I ought to be safe in Linux.  Firefox froze, and when I rebooted there was a strange noise during the BIOS screen before the OS begins to load.  Then when I tried to enter my password I got a warning saying that my keyboard was inaccessible, potentially because of a malicious program. 

Same thing after another reboot, fixed after I entered the BIOS settings and reset them.

So maybe not a Linux trojan, but a vulnerability of another sort.

---

