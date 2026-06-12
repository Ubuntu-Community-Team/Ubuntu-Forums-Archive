---
title: "Its Edgy alright..help!"
date: 2006-11-09
forum: General Help
---

### Post by gannic on 2006-11-09
I was running dapper on two PCs and it worked well. I decided to upgrade to Edgy on one PC when Grub stopped working one day.

I have a fresh install of edgy it is networking well, but it takes around 5-10 minutes to boot!

It worked fine once I got in until I started trying to fix the boot. It sort of still does except it says "HAL failed to initializet."

Other symptoms - wierd graphics on boot (black and white). Colour once you get to the log in screen.

I have an Athlon 64bit 3500 2x SATAII drives and an Nvidia GT graphics card. I am running the Edgy 64 bit version, installed from CD.

Any help would be appreciated, I dont want to go back to dapper unless I have to.

---

### Post by aidanr on 2006-11-09
[http://ubuntuforums.org/showthread.php?t=186497&highlight=hal+failed+to+initilise](http://ubuntuforums.org/showthread.php?t=186497&highlight=hal+failed+to+initilise)
[http://ubuntuforums.org/showthread.php?t=286334&highlight=grey+usplash](http://ubuntuforums.org/showthread.php?t=286334&highlight=grey+usplash)

^couple of threads to read through
first one seemed to be fixed by reinstalling hal with synaptic or editing the hal config file
didn't see any easy solutions for the second one
gl

---

### Post by gannic on 2006-11-11
Thanks, but while HAL etc is annoying, and the grey screen is ugly, 5-10 miunte boots are the real problem. It happens on all versions o Edgy with my hardware. Dapper was fine.

I appreciate the help.

---

### Post by aidanr on 2006-11-11
is there any one thing that seems to be taking long to load?

when grub loads, press escape, then "e" the edit the boot command and on the second line remove "splash" and "quiet", enter and then press "b" to boot
this disables the splash screen temporarily so you can read whats going on when it's booting up

---

### Post by gannic on 2006-11-11
Thanks for getting back to me.

I followed the intructions and can now see the problem...dont know what it means though.

Basically it keeps saying....

.....DriveReady SeekComplete error
.....uncorrectible error

And

....Unrecovered read error - auto reallocate failed

and

....translated ata stat/err

This lasts or about 10minutes then it boots

Any ideas?

---

### Post by aidanr on 2006-11-11
boot into recovery mode (escape when grub is loading and choose the second grub entry) and then run ```
fsck -p
```

"fsck" is file system check
```
man fsck
``` and ```
fsck --help
``` for more info
type reboot when you're finished


although those errors sound a bit more serious than file system corruption, so i'd strongly advise you to back up anything valueable you have on that drive now, just in case, and if your harddrives are s.m.a.r.t. enabled, look into setting up smartmontools to see if its starting to fail

---

### Post by gannic on 2006-11-11
Thanks again.

It seems to be that the trivial problems are unrelated.

Based on your comments, I decided to try unplugging the second drive and edgy boots up in about 30secs.

I think the other hard disk may be failing as you suggest, which would explain why that had stopped booting correctly in the first place. Its only about 3 months old, so I hadnt even considered that.

Anyway, it appears edgy is not at fault. It looks like a hardware issue.

This is off topic, but I dont suppose you know a way to install the 64 bit kernel along side the 32 bit in GRUB so I can switch between them?

Thanks for your eforts on my behalf, they have been extremely helpful.

---

### Post by aidanr on 2006-11-11
no problem:) 

as for the kernels question, i doubt you can do that, you'd have to dual boot the 32bit version with the 64bit version, as i'm guessing all the other programs on the machine are either 32bit or 64bit

i'm not 100% on that one though, maybe someone else can clarify

---

