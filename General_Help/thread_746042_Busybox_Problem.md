---
title: "Busybox Problem"
date: 2008-04-05
forum: General Help
---

### Post by Nai Paws on 2008-04-05
My partner has installed Kubuntu on her PC and to start with it booted up just fine. After a couple of boot ups her PC started going through the booting up part but then went into a Busybox screen. It boots up fine in recovery mode. Weve had a  search on the forums but neither of us are particuarly knowledgeable of linux, and dont get what she is meant to do. 

Could anyone possibly explain to us what she might have to do, and is there anything we can do / post that might help you guys find out whats up with her PC? :)

Basic Specs:

Motherboard: ASUS K8N-E Deluxe. Socket 7 54
Processor: Amd Athalon 64 3000+
Memory: 1gig
Graphics: XFX Nvidia GeForce FX5700 LW (256mb ram)
Sound: Creative Audigy 2

Drives: Western Digital Caviar 800 (80gig - win xp sp2)
           Western Digital Caviar 1200 (120 gig - Kubuntu : Herdy Heron)

CD RW: Teac CD-W516eb
DVD RW: NEC DVD-RW ND-3550A

Thanks for any replys given :)

---

### Post by Wenchkin on 2008-04-05
Hey all,

I'm the newbie partner of Nai ;)

The Hardy Heron install is pretty new (I think it's been booted up less than 3 times) and I was still at the "playing around" stage so haven't messed around adding much so far.  

In other words it's no huge problem to re-install Kubuntu, but I didn't want to take that route if there was an easier fix staring me in the face lol.

I selected the second safe boot up option at startup (the first one seems to just stop for some reason), then I tried the first option of fixing drivers on the next menu and from there continued the normal boot.  Everything displayed fine and seemed to be working ok.  

Not sure if the above is of any help, but would appreciate any advice.

Wenchy

---

### Post by pointone on 2008-04-05
Right before the BusyBox prompt appears, an error message should be displayed explaining why the boot failed and BusyBox was loaded. Please post this error message.

---

### Post by Wenchkin on 2008-04-05
> **pointone said:**
> Right before the BusyBox prompt appears, an error message should be displayed explaining why the boot failed and BusyBox was loaded. Please post this error message.

Ok, when I pick the first option for booting normally I get the Kubuntu splash screen for a few minutes, then it drops to the BusyBox with no messages displayed.

If I try the first safe mode boot it pauses mid way through but eventually I get this message before the BusyBox dialogue.

"Check roote = bootarg cat /proc/cmdline or missing modules, devices: cat/proc/modules Is /dev
ALERT! /dev/disk/by-uuid/fb4d6f67-698d-47f0-bb6a-a5a982d36df9 does not exist. Dropping to a shell!"

I haven't looked up the ID of the drive it's referring to, but the NTFS windoze drive wasn't mounted yet and I hadn't touched any drivers etc for the CD and DVD drives either.  

Wenchy

---

### Post by Nai Paws on 2008-04-06
Could this be a fix to the problem? 

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/201673](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/201673)

Can someone confirm before we start doing this to her PC please :)

---

### Post by pointone on 2008-04-06
That bug clearly states it only affects Hardy Heron (8.04). Are you running a beta version of Ubuntu?

The error message is hinting that the root boot argument is incorrect. Try this instead: 

When the GRUB menu opens during boot, select the Ubuntu option and press "e" to edit the command line arguments passed to the system. A new list should appear; select the "kernel" line and press "e" again.

A prompt should appear with a bunch already typed in. Find the part that says "root=UUID=########-####-####-####-############" and change it to read "root=/dev/sdaX" where, /dev/sdaX is your root partition (i.e., /dev/sda1).

---

### Post by jbmckee on 2008-04-08
I had a similar problem of getting dumped into BusyBox.  I solved it by moving my installation from my D drive to my C drive.  Then it booted properly.

---

