---
title: "&lt;0&gt; Kernel Panic -- Not Syncing"
date: 2007-01-21
forum: General Help
---

### Post by Zylstra555 on 2007-01-21
First of all, I would like to say that I am not a Linux expert, and am much more familiar with Windows machines.

I am getting the error: <0> Kernel Panic -- Not Syncing while using a version of linux distribution called SLAX Linux.
I decided to download and run Ubuntu, since I assumed that it would probably work better. 
When I started Ubuntu, I could see the Splash start screen, and selected the regular Ubuntu start, it just freezes on the start after a while, and I can only assume its the same error. (Its covered up by the loading screen)

I have tried using: Live acpi=off and it did not work

This is a Intel III processor at 733MHz, 129MB RAM, and a 7GB Hard drive... its a gateway
I tried using a different processor, but had no luck

What causes this error and how do I fix it?

---Also, how well does WineHQ work on the Ubuntu Linux? Can it run the Sims and the Sims 2?

---

### Post by Zylstra555 on 2007-01-21
Also, is this a common error?

---

### Post by acu2005 on 2007-01-21
I also am having a syncing issue.  Mine is during installation and i'm trying to run 5.10 on an iMac g3.

---

### Post by Zylstra555 on 2007-01-22
I have been wondering how well Ubuntu works on Macs, I have a G3 iMac, does anyone know if those work well? Or if the Ubuntu for Macs is just as good for PC or not?

---

### Post by maddog39 on 2007-01-22
I have a PowerBook G4 with Ubuntu Edgy on it. Its pretty much just as good as Ubuntu for PC. Sorry I cant answer any of your other questions though.

---

### Post by durgin on 2007-01-23
I'm chiming in with exactly the same Kernel Panic - Not Synching problem.

I'm running an older Via P4PB with a P4 2.8, 1 GB, ATI Radeon 9000 Pro video card, and various IDE HDDs from 4 GB to 120 GB.  I've tried various Ubuntu, KBuntu, XBuntu disks, and network installs.  All sorts of installation variations.  I've tried noapic nalapic nosmp maxcpus=0 options all to no avail.  ALWAYS crapping out right after install selection & kernel loading, at this message.  Not an installation media or HDD problem.  

Suse 10.2 had a similar difficulty on this motherboard until I tried installation with the maxcpus=0 option, so that's a clue, for sure.  But that trick by itself does nothing with any Ubuntu variation.

I'm trying to make 3 more good P4 2.66's based on this test system, using either Kbuntu or Xbuntu, that I can donate to disabled friends.  But I need to be able to install, and know how to reproduce the right installation instructions.  Any clues would be appreciated.

---

### Post by Zylstra555 on 2007-01-23
Dang
I really want to get Ubuntu working on this computer since the only other computer capible of running it is my laptop, and I need that to be able to run my Wireless access.
But its not working](*,)

---

### Post by Zylstra555 on 2007-02-07
I did find out what the problem was. 

It turned out that my computers RAM was bad somewhere along the way, and this was causing Linux to go ahead and error-up

I just went into the BIOS and dissabled "Quick Self Test" so it would do the full test instead, and now it scans all its memory, preventing memory errors. 

This also made Windows stop crashing

I am glad, its working all right now.

---

