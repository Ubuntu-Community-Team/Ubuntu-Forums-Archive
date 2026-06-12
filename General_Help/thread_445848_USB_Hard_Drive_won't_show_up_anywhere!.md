---
title: "USB Hard Drive won't show up anywhere!"
date: 2007-05-16
forum: General Help
---

### Post by giallofever on 2007-05-16
I have an external usb hard drive (NTFS) with my LIFE on it. It worked fine but could not get write access to it. So I installed NTFS through Automatix2 and I still could not get write access. So I started reading around forums and messing around trying different commands through terminal. No luck. I was turning it off/on the whole time hoping for write access after I tried something without unmounting it as I though it would auto unmount. I found out later that was a no no. Well to get to the problem, I unmounted it properly the last time, then did a clean install of Feisty on my "internal" hard drive, then when I turn my usb external drive on, it wouldn't automount. So I went and looked for it in media, no go either. It doesn't seem to even recognize it at all. Any ideas?

Here is my $ sudo mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I know there are other commands you probably want me to show but I don't remember them. I have searched 2 days straight with no sleep (seriously!) on every forum site I can find, and everybody is talking about NTFS write access or unable to mount a drive that shows up in $ sudo mount. I don't see my drive of "LIFE" anywhere. I need this data badly.
Thanks in advance guys, these forums are lifesavers, err, I mean... painkillers for headaches. :)

---

### Post by th3rmite on 2007-05-16
With the hard drive plugged in run 

```
lsusb
```

Does the drive show up there?

---

### Post by giallofever on 2007-05-16
Nope.

Results from $ lsusb:

Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000  

The power light comes on, I here a clicking and the blue access light flickers for a split second then silence, nothing else.

---

### Post by giallofever on 2007-05-17
Turning it on would automount it. I assumed I could turn it off too. Would turning it off and on without right clicking and selecting "unmount drive" cause corruption?

---

### Post by giallofever on 2007-05-17
Ahhh... new information! I was fortunate my dad brought his PC over, he had just installed Ubuntu 6.10, clean install. I plugged it in and BAM, there it was, auto mount (I didn't try to write to it though, just wanted to see if it worked.) Apparently all the terminal typing I was trying to get NTFS access might of screwed things up a bit. Is there any way of undoing in the terminal without really remembering ALL the things I did. If not I would even go as far as a sort of "clean install." Is there a way to reinstall Feisty just replacing the OS without touching any of the Home data? Because I have a lot of downloads on this drive I don't want to lose.

---

### Post by pebo on 2007-05-17
> **giallofever said:**
> Is there a way to reinstall Feisty just replacing the OS without touching any of the Home data? Because I have a lot of downloads on this drive I don't want to lose.Do you have a seperate /home partition? If you do you needn't format it when you re-install and your data will be untouched. If not back up your data (which you should do in any case :)) and copy it to the new install. 
It's a good idea to have a seperate /home partition for this reason.

---

### Post by Kouki on 2007-05-18
> **th3rmite said:**
> With the hard drive plugged in run 

```
lsusb
```

Does the drive show up there?

I'm having a similar problem but mine does show up when I run the above.  The external seagate drive used to work fine on dapper and was just there without installing anything.  Now I've gone to feisty it doesn't seem to appear anywhere.  However running the above command shows it (2nd on the list):

Bus 008 Device 003: ID 07c4:a604 Datafab Systems, Inc. 
Bus 008 Device 002: ID 0bc2:0503 Seagate RSS LLC 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:6025 Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  

Now what would I have to make it show on the desctop or on computer like it used to :confused:

---

### Post by dcymbal on 2007-05-20
I just wanted to report a similar problem since upgrading to Feisty.  I've had an external Seagate USB drive that I have been using with Ubuntu since 4.10 with no problems.  After the upgrade to Feisty, it will no longer automount.  I can see it in lsusb, I see dmesg show it detected, and if I manually mount the drive it works fine -- it just won't automount!  I have another external USB drive that automounts fine.  This is consistent between the two drives.  I compared the dmesg output of when I attach the "good" drive vs. the "bad" and I don't see any differences.  It is not the end of the world since I can mount manually, but disappointing when something that was working without issue goes south after an upgrade.  I have been meaning to try and debug it further, but have not had the time.....

---

### Post by cliffordcurry on 2007-05-22
I am having the same problem too with a seagate 320GB. It seems that the drive is mounted and appears everywhere ( in terminal when prompted, and in device manager hardware lists) but not on the desktop where I can access it. I recently made a clean install from EE to FF after encountering the same problem after an upgrade, thinking that that would prove to be the solution, but no. In EE the drive automounted every time...

---

### Post by cliffordcurry on 2007-06-05
If anyone is interested I finally managed to automatically mount my external usb drive  by installing Automatix read/write NTFS and FAT 32 mounter. It was that easy.

---

