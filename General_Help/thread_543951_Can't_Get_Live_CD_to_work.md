---
title: "Can't Get Live CD to work"
date: 2007-09-05
forum: General Help
---

### Post by zajacattack on 2007-09-05
Hello, I just received my Ubuntu 7.04 CD. I tried to boot from it. I selected "Start or Install Ubuntu" at the boot menu. Then, the Ubuntu logo with a progress bar showed up for thirty seconds or so. Then, I started getting error messages. These were:

Buffer I/O error in device hdc, logical block 0
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 1
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 2
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 3
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 4
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 5
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 6
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 7
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 0
hdc: device is not ready for command
Buffer I/O error in device hdc, logical block 1
hdc: device is not ready for command

Then it kept repeating "hdc: drive is not ready for command" over and over.  So, as you can see, my boot fails. I am running a PC with a Pentium 4 1.8 Ghz processor, 256 MB of RAM, and am booting from a CD-RW drive. Can someone help me get the live CD working? I just want to try Ubuntu, not install from the alternate desktop CD. Isn't there a boot option I can use? By the way, I am already using the boot options "noapic" and "nolapic".

---

### Post by merlinus on 2007-09-05
Try it, if possible, in a different cd drive.

-merlin

---

### Post by zajacattack on 2007-09-05
I only have one CD drive. Is there anything else I can do? Someone said to just let it keep doing that for a while, is that true, or is there something else I can do?

---

### Post by gigaferz on 2007-09-07
i remember seeing that before.....it was on my laptop,,none of the "buntus"worked...

just make sure your md5 sum is right,, and also burn the cd at aslower speed...and once is ready there is an option below to check the cd  for defects..(?)

---

### Post by zajacattack on 2007-09-08
I didn't burn my own CD, I got a free one from ShipIt. Do I need to make the CD-ROM drive the master? In the CMOS, the hard drive is the primary master, there is no primary slave, the CD drive is the secondary master, and there is no secondary slave. Can I adjust this to make it work?

---

### Post by oilchangeguy on 2007-09-08
> **zajacattack said:**
> I didn't burn my own CD, I got a free one from ShipIt. Do I need to make the CD-ROM drive the master? In the CMOS, the hard drive is the primary master, there is no primary slave, the CD drive is the secondary master, and there is no secondary slave. Can I adjust this to make it work?

doing this will make no difference. there is some other issue, that needs to be resolved. possibly a ram issue. 256 is the bare min. and if the computers got onboard video, some of that 256 is going to video.

---

### Post by merlinus on 2007-09-08
xubuntu live cd will work, but you will either have to download it or order a cd.

Still, to ensure that this is not a problem with your hardware, try it on another computer.  A friend, neighbor, or even the public library.

-merlin

---

### Post by Sef on 2007-09-08
> I didn't burn my own CD, I got a free one from ShipIt.

Even ones from Shipit can be bad.

---

### Post by zajacattack on 2007-09-09
OK, I can't check the CD for defects because the same error messages come up. So, are you saying there is absolutely no way around this for the live CD to work? I even let it sit for over an hour until it got up to

[   3000-something] hdc: drive not ready for command

It's just really getting annoying because I need this live CD to work, and I don't want to install (my hard disk is low on free space)! Please, someone help me!

---

### Post by merlinus on 2007-09-09
Did you try the cd on another machine to see if you get the same errors?

---

### Post by zajacattack on 2007-09-09
Well, I was gonna see if one of my friends would let me try it on there machines tomorrow. But I was wondering if there was something I could try until then.

---

### Post by zajacattack on 2007-09-10
OK, I'm pretty sure this is a problem on my part because, were it the CD, the CD would be able to check itself for defects, but I get the same error messages when I select "Check CD for Defects". I have an Atapi CD-RW drive. Is there a boot option for this or is there something in my BIOS I could try? Or, is this an issue because I have 256 MB of RAM and 32 MB is going to on-board video? And, if so, is there something I could use to boot from the CD and use less RAM ("Safe graphics mode", etc.)? Or does my Ubuntu CD just hate my computer?

---

### Post by ethan961 on 2007-09-10
I'm having the same problem trying to install Fedora.
I have never had a problem with this drive before.
(I am not asking for help. I am simply stating my experiences.)
You probably have a bad disc, although your drive might simply not like the disc, if possible.
Does anyone know if there is a way to check the md5sum of the disc against an md5sum file that you download from an ubuntu server?
Ethan

---

### Post by zajacattack on 2007-09-14
OK, so this is probably a bad CD, right? I ordered three more off of shipit, hopefully one of them will work.

---

