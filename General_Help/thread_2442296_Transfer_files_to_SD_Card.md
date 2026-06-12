---
title: "Transfer files to SD Card"
date: 2020-05-02
forum: General Help
---

### Post by spudleguy on 2020-05-02
I am using Ubuntu Studio (20.04). I am trying to backup some music files to a SD card. It is formatted in ExFat but I have installed the package 'fuse exfat utilities'. When I copy the files and then try to paste to the card the Paste link is not highlighted. Am I mistaken that the 'exfat utilities' package allows to write to exfat or do I need additional software to allow this? Thanks.

---

### Post by ActionParsnip on 2020-05-02
Is the card going into a device or are you just using it as a backup storage?

---

### Post by kurt18947 on 2020-05-02
I haven't messed with exfat in quite some time. When I did use it I installed 2 packages, exfat-utils and exfat-fuse. It did work at the time.

---

### Post by spudleguy on 2020-05-02
I installed using these two commands:

sudo apt install exfat-utils

sudo apt install exfat-fuse

there is no problem reading the card, only transferring files to it or writing a file to it.

---

### Post by CelticWarrior on 2020-05-02
OK, but the question above is still relevant:
> Is the card going into a [other] device or are you just using it as a backup storage? 				

If it is NOT to be used with other OSes then there's no point in using exFAT. Just format it as EXT4.

---

### Post by SeijiSensei on 2020-05-02
Does it have a write-protect switch, and if so, is it enabled?

---

### Post by CelticWarrior on 2020-05-02
> **SeijiSensei said:**
> Does it have a write-protect switch, and if so, is it enabled?

Also a very pertinent question. ;)

---

### Post by spudleguy on 2020-05-02
The write protect switch is NOT locked. And yes it is just for backup. EXT4 is not readable by Windows (still a necessity) .

---

### Post by CelticWarrior on 2020-05-03
> **spudleguy said:**
> The write protect switch is NOT locked. And yes it is just for backup. EXT4 is not readable by Windows (still a necessity) .

If so, NTFS has better support. There's no advantage in using exFAT.

---

### Post by speedflash on 2020-05-03
Install this two programs and thank me later "exfat-utils and exfat-fuse"

---

### Post by tea for one on 2020-05-04
> **spudleguy said:**
> The write protect switch is NOT locked. And yes it is just for backup. EXT4 is not readable by Windows (still a necessity) .

The last time the SD card was used in Windows, did you **safely remove** it?

Do you have the necessary permissions to read and write to the card?

Some new PCs have UEFI settings for devices (usb, sd, video etc).
Do you have any settings in your firmware set up screens for the SD card reader such as:-

Disable
Read only
Read/write

---

### Post by spudleguy on 2020-05-04
As for the settings, I don't know, I will have to check, the card was  brand new. I did place it in a Win 10 machine and since it had no data  on it I just removed it. And I did mention earlier that I originally installed "exfat-utils and exfat-fuse".

---

### Post by spudleguy on 2020-05-04
I was able to read and write to the SD card on another machine also with Ubuntu Studio 20.04. I also discovered other issues with the original machine: When running my preferred music player (Audacious) it wouldn't acknowledge the external hard drive where my music files were stored. But on the 2nd machine, no problem. So there must be a setting in the BIOS or other primary setting or hardware that is the problem.

---

### Post by tea for one on 2020-05-04
It's becoming a little confusing.

One of your PCs is fine - SD cards and external hard drives are recognised with both read/write.

Your **difficult** PC does not recognise the SD card nor an external drive?

Is that a fair synopsis?

---

### Post by spudleguy on 2020-05-04
Yes. I will say the 'good' laptop had 20.04 installed on the 2nd day that  20.04 was available, the 'bad' one I installed it just the day before I  started this thread (3 days ago).
The 'bad' laptop is a Fujitsu AH530.
The 'good' one is HP Elitebook 2170P.
Both were Windows 7, the Elitebook has had Ubuntu Studio 19.10 installed (primary-no Windows) for quite sometime, 20.04 was a complete install, not an upgrade. The Fujitsu was just installed (also no Windows)
It could be the laptop with the problems, I don't know.

---

### Post by tea for one on 2020-05-04
Thanks for the info.

Your difficult Fujitsu laptop is around 10 years old - is that correct?

Given the fact that external drives and SD cards are both giving you problems on the same device, the runes point towards failing hardware...........?

Anyway, just to explore a little further, if I were in your position, I would download an ISO of Ubuntu either 18.04 or 20.04 or **preferably** Xubuntu 18.04 or 20.04, burn a usb stick and run a **live** session.
During the live session, then you can test both your SD card reader and external drive. 

Keep the power cord plugged in so that you can eliminate battery problems.

Let's see what transpires.

---

### Post by spudleguy on 2020-05-04
Thanks, tea for one, I will and I'll let you know.

---

### Post by TheFu on 2020-05-04
With 20.04, snap packages are much more common.  snaps usually constrain access to areas outside the HOME.  I would check if any software having trouble accessing storage outisde HOME was a snap install.
**snap list** is the command.

---

