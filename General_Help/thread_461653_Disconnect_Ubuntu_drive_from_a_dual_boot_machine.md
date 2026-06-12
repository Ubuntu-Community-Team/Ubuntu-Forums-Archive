---
title: "Disconnect Ubuntu drive from a dual boot machine"
date: 2007-06-01
forum: General Help
---

### Post by pypsnyder on 2007-06-01
Hi and good evening,

I'm new to Ubuntu and even newer here at this forum.  I'm a very basic user of Linux and don't really know much about it, nor for that matter Windows.  Recently out of curiosity I installed Ubuntu 7.04 Feisty Fawn and I have begun to like it, but I now have two others I want to try before I settle down with a particular flavor of linux.  The other two I want to try out is Kubuntu and PCLinuxOS.

Here's my problem ...

I have two drives on my PC one with Windows and the other with Ubuntu.  I made the one with Ubuntu as the master drive and the one with Windows as the slave drive  (I think).  At any rate, when I disconnect the Ubuntu drive the computer won't boot, period.  I know everything is fine because when I connect the Ubuntu drive back, I was able to boot either Windows or Ubuntu just fine.

Here is what I want to do ...
I want to disconnect the Ubuntu drive and make that machine Windows only.
Install the Ubuntu drive on another CPU that my friend has loaned me and test drive the other two Linux distro's as pure linux machines.

Could someone out there help me with simple step by step instructions please.

Thanks very much.

---

### Post by hellmet on 2007-06-01
If you'll not be using the ubuntu drive on the windows machine again, then to make Windows boot, you'll first have to make the Windows HDD the master. Then put the XP cd, and recover the MBR. 

To do this, press R at the first screen.
You'll get a prompt. Select the windows partition number.
type FIXMBR. Say yes. Reboot.

You can use the Ubuntu drive on another CPU (?? Hope you meant another computer.)
as usual. Just format the thing during installation of either of the OSs.

---

### Post by pypsnyder on 2007-06-02
> **hellmet said:**
> If you'll not be using the ubuntu drive on the windows machine again, then to make Windows boot, you'll first have to make the Windows HDD the master. Then put the XP cd, and recover the MBR. 

To do this, press R at the first screen.
You'll get a prompt. Select the windows partition number.
type FIXMBR. Say yes. Reboot.

You can use the Ubuntu drive on another CPU (?? Hope you meant another computer.)
as usual. Just format the thing during installation of either of the OSs.

Thanks very much for the quick response.  I'm presuming that you mean OEM CD that came with my computer.  I have that and I'll give it a shot.

Yes I plan on using the Ubuntu drive [separate physical hard drive] on an other machine

---

### Post by griffithc on 2007-06-02
Yes, I had this problem when once I wanted to return to a single Windows partition. When you booted with both systems operating did you get a choice of Ubundu or Windows? If so, then to return to a Windows only install, you will need to restore the master boot record (MBR).

On the first screen of the Windows Setup program, select "R" and on the next screen, select "K" to run the Recovery Console. Enter thecommand: fixmbr 

Reboot. If you still have probelms, return to the recovery console and type  fixboot c:

---

### Post by pypsnyder on 2007-06-02
Problem SOLVED!

Thanks very much for the helpful hints.  Problem solved.  I now have two machines one with Windows and the other Linux.  I'm trying out PCLinuxOS and will eventually have Kubuntu.

---

### Post by hellmet on 2007-06-03
Great going.. nice to know that you've solved the problem :) ..tc

---

### Post by griffithc on 2007-06-03
Great! Good luck, Pypsnyder. :D

---

