---
title: "GRUB Error 18 - Doesn't Follow Usual Pattern"
date: 2007-08-14
forum: General Help
---

### Post by everythingsused on 2007-08-14
When I turned my computer on this morning I encountered :

```
Error 18: Selected cylinder exceeds maximum supported by BIOS
```

As I understand, this error means that the kernel is stored in a place on the harddisk that the BIOS doesn't think should exist. It's an older computer with a much larger disk than it is supposed to have so that would make sense except that 1) it is not a dual boot, so the kernel should be on the front of the disk and 2) it's been booting for almost a year without any problem. I can mount the disk from an Ubuntu live CD, so I'm sure that's not the problem.

I've read that a good solution to this is to create a boot partition to store the kernel in. I have no problem doing that, but I wanted to make sure there wasn't any other problem before I attempt it. Is it possible for the computer to suddenly decide to relocate the kernel storage location to a place the BIOS can't find? (I doubt it, but that's the only thing I can think of). And, is there anything else anyone knows of that can cause this error? 


The computer is a Thinkpad I-Series 1300 and it's currently running Debian Etch on a 30 GB harddisk. 

Thanks!

EDIT: Actually, I take the back the part about me being sure the drive is okay. I can access some folders fine, but on some I just get ```
Input/output error
```

Could that be a sign that the drive is going on me? Or is it just a limitation of booting from a live CD?

---

### Post by dannyboy79 on 2007-08-14
based on what you've stated it soiunds like your drive is dieing and fast. Since the Ubuntu booted with where the kernel is for a year, and you didn't change any bios settings, and then you got this out of the blue, then I would have to say your drive is dieing for sure. You can always run a
sudo fsck /dev/hdx
(x = the letter you want to check)
you can do this from the live cd just make sure it's not mounted. OR you can download Seatools from seagates website and it will do a check on the drive also. Good luck

I would save your data off of it immediately though, use ddrescue which will copy it bit for bit and ignore any errors.

---

### Post by rbmorse on 2007-08-14
I would agree with that diagnosis.  Most current production disks do a recovery feature called "sector sparing."  When internal diagnositcs detect a bad sector(s), as much of the data in the sector(s) as possible is/are rewritten to reserved sector(s) on another part of the drive and the file allocation table updated accordingly.  This is done within the disk controller and is transparent to the operating system. 

If you had a sector below the BIOS' magic dividing line go bad, the controller could easily have moved the data out of reach. If the data involved is the boot sector or other  boot code, the result would be as you reported. 

With modern IDE drives, as soon as you see signs that sectors are failing it is time to backup the drive as soon as practical and remove it from service.

---

### Post by dannyboy79 on 2007-08-14
hence why I use smartmontools. I actually found out that my mythtv dedicated hard drive for storing livetv and storing the recordings was changing parameters frequently per emails I was getting. See below:
Device: /dev/sda, 1111 Offline uncorrectable sectors
Device: /dev/sda, 800 Currently unreadable (pending) sectors

Although the number was staying constant. Meaning I would get this email almost every day, it's been about 1 month with smartmontools installed. Then I download the Western Digital diagnostic tools for testing the drive (required to provide code for free warrenty replacement) and sure enough, the drive failed it's test. So smartmontools saved me plenty of recordings that I would have lost without it.

Here's a great guide for setting it up: [http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

---

### Post by everythingsused on 2007-08-14
Thanks for your replies.

fsck confirmed that the disk is pretty messed up as you suggested. Luckily, this is a secondary computer so I didn't have that much I needed to recover. 

I think it's pretty interesting though that Error 18 is the first sign I got of it, so thanks for the explanation. 

And thanks for the smartmontools link, I'll have to check that out.

---

