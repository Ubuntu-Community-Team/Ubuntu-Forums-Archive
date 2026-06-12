---
title: "Kernel Panic - not syncing:"
date: 2016-09-13
forum: General Help
---

### Post by NertSkull on 2016-09-13
I can't boot my computer do to a kernel panic.  I don't think its a hardware issue as I'm currently writing this in my dual booted windows partition.

I've never had a kernel panic before and don't know what to do/what can be done. But its my work computer and would really like to get it up and running (I have file backups, but I'd like to not have to re-install/restore everything).

I don't know if this is related/the cause. But right before it crashed and then wouldn't boot, I was installing the latest version of skype. It didn't finish the installation but froze. When rebooting, I got this message.

Attached is a picture of the screen. I've tried booting into old kernels, and into recovery mode. Each time it goes to kernel panic.

It looks like it might have something to do with libjson-c.so.2.  Is that something I can install/fix/update even though I can't get into my machine? Maybe a live CD?

Any help would be appreciated.

---

### Post by Bashing-om on 2016-09-13
NertSkull; Yuk ..

Yeah, I can accept that the attempted install of skype broke the system.
What method/source did you use to attempt this install of skype ? 
Be aware that Microsoft bought skype, and I can believe that MS is not to well directed to maintain skype for linux.

Looking at the error we find:
[http://packages.ubuntu.com/trusty-updates/i386/libjson-c2/filelist](http://packages.ubuntu.com/trusty-updates/i386/libjson-c2/filelist)
such that " libjson.so.2" is a part of the package and is required ( libjson-c2 ).
So we need to look at the status ;
As you can not boot into the install, we need to find another means to access the system.

As you have been around a bit, are you familiar with a full CHange Root routine from the liveDVD ?
A CHange Root might be worth a try and from there not only have a looksee, but repair the damage ?

[INDENT][INDENT]possible, but .....
[/INDENT][/INDENT]

---

### Post by NertSkull on 2016-09-13
I got it straight from the skype website. Their debian package download. 

I believe I've done a chroot before. I make life complicated by using LUKS full disk encryption. And I've had to mount my encrypted filesystem in a live CD environment before. Its been a while, but I have notes on how I did in the past somewhere.  So I, in theory, can find a way to get a chroot environment I believe.

If I do that, can I just replace the libjson.so file?  Can I just simply download the file and replace the one in /lib/i386-linux...?  Or do I need to actually re-install a package somehow?

---

### Post by Bashing-om on 2016-09-13
NertSkull; Great .

Glad you have some familiarity with what we need to do, as with encryption, I sure do not .

If and when you can gain access to the system;
what returns:
```

dpkg -l  libjson-c2
ls -al /lib/i386-linux-gnu/libjson-c.so.2
ls -al /lib/i386-linux-gnu/libjson-c.so.2.0.0

```
see too what we can find for directions to un-install skype .. ??
As a thought, perhaps stay with the version of skype that is tested in the software repo ?

Poke and prod 'til
[INDENT][INDENT][INDENT]we find a way forward
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-09-13
I think you will find that the version of skype that you get from the skype website is exactly the same version that is available in the canonical-partner repos; it is just so much simpler to install skype direct from the repos as it takes care of the i386.bin and any libraries that are needed.

---

### Post by NertSkull on 2016-09-14
Success!!  I was able to get my system to boot again by re-installing the libjson-c package in a chroot environment using a LiveCDThanks for pushing me in the right direction Bashing-om

---

### Post by Bashing-om on 2016-09-14
NertSkull; Great !

Glad it worked out and in the end was an easy fix .

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

