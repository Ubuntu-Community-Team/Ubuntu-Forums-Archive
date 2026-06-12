---
title: "[SOLVED] Fix windows xp"
date: 2008-06-01
forum: General Help
---

### Post by potatoehead64 on 2008-06-01
Hi,

I have Unbuntu Gutsy installed on a separate partition on my hard drive to Windows XP. I rarely use XP these days, but still need it every now and again for some software.

The problem is that I believe XP has picked up a virus. I can't even boot it in safe mode. I'm aware that I could reinstall windows from scratch, but I've read on other forums that it could interfere with the MBR. I don't want to lose my current Ubuntu installation with all its related software.

Is there a way of running a virus cleaner from Linux/Ubuntu to clean the drive windows is installed on? 

If not, how can I fix windows using back up/recovery disks or kill the windows partition and fresh install without interfering with Grub/MBR?

NB. I have a "data only" partition on my HD where I store all files just in case a serious virus event occurred. 

Pls help.

Regards

Martin

---

### Post by shifty_powers on 2008-06-01
can you mount the windows hd in ubuntu?

if so, you can either download clamav from the repo's, or if you do a google, avg for linux is available as a deb.

ne aware, avg needs to be run as sudo to be updated ;)

---

### Post by lisati on 2008-06-01
AVG also have a free virus scanner for Linux that can scan your Windows partition. It can be downloaded from [http://free.grisoft.com]("http://free.grisoft.com"). Don't forget to add your normal Linux admin account to user group avg, otherwise you won't be able to download updates with the GUI.

EDIT: To mount your Windows partition, you might want to install the NTFS-3G package.

---

### Post by shifty_powers on 2008-06-01
had already mentioned avg ;) :P

---

### Post by vvvladut on 2008-06-01
So which one is better: AVG or ClamAV?

---

### Post by twright on 2008-06-01
i would say avg (but both are good)

---

### Post by NullHead on 2008-06-01
> **twright said:**
> i would say avg (but both are good)

I second that. I tried installing clamAV before and couldn't figure out its GUI :(

---

### Post by Joeb454 on 2008-06-01
I use AVG on my Windows partitions, and it works very well when it gets used (hardly ever).

Though I've never tried the Linux version, I'd imagine it's very similar

---

