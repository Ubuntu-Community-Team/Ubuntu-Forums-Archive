---
title: "No sound in Gutsy"
date: 2007-10-15
forum: General Help
---

### Post by pack74743 on 2007-10-15
I am new to Ubuntu and Linux.  I have a Dell XPS 400 desktop and my sound card is a Creative SoundBlaster X-Fi.  Since installing 7.10 I get no sound whatsoever.  No sound when I disconnect from the sound card and connect to the regular computer mini-port and none through my headphones.

I get the following error messages when I open the volume control or attempt to test sounds:
 
  "audiotestsrc wave=sine freq=512 ! audioconvert !     audioresample ! gconfaudiosink: Failed to connect: Connection refused"

  "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

I have read several threads on this subject, and have tried some suggested fixes.  However, nothing has worked.  Unfortunately, I still need to be told both what to do _and_ how to do it.

Incidentally, I have had no sound issues at all in Windows.

Thank you,
pack

---

### Post by Pumalite on 2007-10-15
Do you have an Intel motherboard with integrated sound?

---

### Post by pack74743 on 2007-10-15
Here is what I have from a Belarc profile of my system:

Board: Dell Inc. 0FJ030
Serial Number: ..CN7082164MG10O.
Bus Clock: 800 megahertz
BIOS: Dell Inc. A05 05/30/2006

3200 megahertz Intel Pentium 4 (2 installed)
16 kilobyte primary memory cache
4096 kilobyte secondary memory cache

ATI Unified AVStream Driver
Creative SB X-Fi
Tunebite High-Speed Dubbing
Unimodem Half-Duplex Audio Device

---

### Post by Pumalite on 2007-10-15
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by pack74743 on 2007-10-15
Okay, I checked out that page and followed the suggestions there except for what I do not yet know how to do.  I do not know how to launch alsamixer, and I think I need to do that to be sure that nothing is muted.

---

### Post by Pumalite on 2007-10-15
At the Terminal:
alsamixer

---

### Post by pack74743 on 2007-10-15
~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

(Help please!)

---

### Post by Pumalite on 2007-10-15
Your kernel is not loading the module for your sound card. (not recognizing it)

---

### Post by pack74743 on 2007-10-15
So what do I do?  Will this be fixed via an update?  Should I just use windows and keep checking back for updates, or what?  Thanks.

---

### Post by pack74743 on 2007-10-15
I just tried the following fix from another thread:
Here's what I did for my 1520 with gutsy (taken from a solution I saw posted for a 1720). Note: I'm using the release candidate that came out on the 11th.

• Prerequisites
&#8728; sudo apt-get install libc6-dev
&#8728; sudo apt-get install patch

• The fix
&#8728; wget [ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2)
&#8728; tar xvpjf alsa-driver-1.0.15rc1.tar.bz2
&#8728; cd alsa-driver-1.0.15rc1
&#8728; ./configure --with-cards=hda-intel,emu10k1
&#8728; make
&#8728; sudo make install
&#8728; Reboot

At the end it told me that everything is muted by default.  So is there some place I can go to unmute now, or is it hopeless?

---

### Post by pack74743 on 2007-10-15
I just found the following in the ALSA project page in reference to my sound card:

"Sound Blaster X-Fi"
	
"UNKNOWN"

		"[Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time."

So, my question is, is there then no way that I can get sound with Ubuntu at this time?  Should I just defer using Ubuntu until this issue is resolved?  If there are other options except for buying another sound card, please tell me what they are.  This answer is important to me.

Thank you very much.

---

### Post by Pumalite on 2007-10-15
Have you looked at this thread?:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

---

### Post by pack74743 on 2007-10-15
Yes, I have now, but without success.  Thanks for your efforts to help anyway.  I'll check back at the ALSA project from time to time to see if my sound card gets supported sometime in the future.

pack  <end>

---

