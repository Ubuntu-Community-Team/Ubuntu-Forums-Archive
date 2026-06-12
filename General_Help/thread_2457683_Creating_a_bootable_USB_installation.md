---
title: "Creating a bootable USB installation"
date: 2021-02-06
forum: General Help
---

### Post by GeordieJedi on 2021-02-06
Hi there guys

I was looking for some help with an issue, please.

Background (& What I'd like to achive):

I currently have a a USB stick with a version of Puppy linux on it, that has 2 partiions on it -
1. The OS drive
2. A storage partiion

Puppy is installed onto the stick, and I can modify files, add / remove programmes and plug-ins for
browsers, etc, etc.

And it also have the (very useful) ability to copy itself into RAM to make it much faster


What I'd like to achive:
I'd like to do the same with Ubuntu -

1. OS partiion (with the ability to copy the OS  and/or the FS (Filesystem) into RAM
to make it much quicker to use

2. A data partiion to store my files


Q 1. How would I go about doing this ?

Q 2. I'd obvously also need to make sure that the USB stick is bootable from itself,
and allow me to use it with any PC that allows booting from USB.


TIA for any help and advice

---

### Post by Unguidedone on 2021-02-06
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

for the file partition you can have another drive with LUKs setup for privacy of the files but your intent here is not to have any persistence of files.

It loads everything into ram, a small amount of ram wont be very useful so shoot for 16 to 64 gigs of ram so you have a bit of space to work with.  Also ram is cheap so it does not matter as much anymore.

there is a lot of ram disk distros to choose from too 
[https://en.wikipedia.org/wiki/List_of_Linux_distributions_that_run_from_RAM](https://en.wikipedia.org/wiki/List_of_Linux_distributions_that_run_from_RAM)

---

### Post by guiverc on 2021-02-06
I would use `mkusb`  ([https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)) which both has persistence, and since [v11]("https://help.ubuntu.com/community/mkusb/v11") has a 'toram' option

Sorry, I'm not an expert in using it; I just use it  (*usually for writing daily ISO's to media for QA-testing; so rarely use persistence except where needed for specific testing*).

It's covered rather extensively on this site, eg. [https://ubuntuforums.org/showthread.php?t=1958073&highlight=mkusb](https://ubuntuforums.org/showthread.php?t=1958073&highlight=mkusb)

---

### Post by C.S.Cameron on 2021-02-06
Running a Persistent Live USB made using mkusb would probably be the most similar to your Puppy setup.
They both use a persistent partition.
All Ubuntu runs mostly in RAM, if the computer has enough RAM.
Ubuntu needs a lot more RAM than Puppy though.
Xubuntu seems to run fully in RAM.
I have not tried running mkusb in Puppy, it might work with a Ubuntu based Puppy like tahr64.
You can install mkusb into a Ubuntu based Live or Persistent USB and use that to create the persistent USB.
A mkusb install also has a option to create a NTFS data partition, so that you can use it for data on Linux and Windows computers. NTFS partitions have been known to fragment over time.
A USB made using mkusb, (with defaults), will boot on both BIOS and UEFI mode computers.

---

### Post by HermanAB on 2021-02-07
If your concern is speed, but you still want to use Ubuntu - add more RAM to your machine and use XFCE, not Gnome.

If your concern is raw speed and Ubuntu be damned, install Slackware or OpenBSD.  Those two are orders of magnitude faster than Ubuntu. The reason is quite complicated, but mainly due to the way file authentication security is handled - Slackware and OpenBSD are much more efficient in this regard.  The difference is quite shocking.

---

### Post by GeordieJedi on 2021-02-11
Thank you all for your help and advice so far. It's much apprecaited.

I "only" have 8 GB of RAM, So it looks like trying to put a full fat Ubuntu install into RAM would be tricky.

So it looks like my options are -

1. Install Ubuntu to USB (full install) not a "live-cd" style (and use XFCE or similar for the DE)
with a seperate data partition 

2. Use Puppy linux, and again, use a seperate partiion for data storage.

---

### Post by C.S.Cameron on 2021-02-12
If your Puppy install boots using GRUB2, you can boot a Xubuntu ISO file and compare the two OS side by side.

For example See: [https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782](https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782) 

Xubuntu and Puppy use different methods to implement persistence, using a "writable" file for Xubuntu should work next to Puppy okay.

---

