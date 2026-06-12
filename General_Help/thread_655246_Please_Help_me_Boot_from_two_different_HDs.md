---
title: "Please Help me Boot from two different HDs"
date: 2008-01-01
forum: General Help
---

### Post by Scarath on 2008-01-01
Hi

Here is the situation, atm i am dual booting Deb and XP on 1 HD, i have just install Slackware on another and wish to add this new OS to the GRUB loader.

I have read some of the other posts on these forums on this subject but none have solved my problem[ [COLOR="Blue"]this one[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=508525")addresses some of the issues but did not resolve the trouble for me, so please give me advice :D

[[COLOR="Blue"]This thead[/COLOR] ]("http://forums.fedoraforum.org/showthread.php?t=176019")has the method i have been following which hasnt worked so far.

Just so you know what else i've read on the subject i checked out [[COLOR="Blue"]this thread[/COLOR]]("http://www.linuxforums.org/forum/slackware-linux-help/95610-adding-slackware-grub.html") but again, the way their HDs are labled seems to be different to mine ...

Here is my fdisk -l

```
 Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf744f744

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hdb2            3188        7011    30716280   83  Linux
/dev/hdb3            7012        7476     3735112+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b8f9b8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e5b3e5a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       12158    97659103+  83  Linux
/dev/hdd2           24298       24319      176715   82  Linux swap / Solaris
/dev/hdd3           12159       23100    87891615   83  Linux

Partition table entries are not in disk order
 
```

Slack is installed on HDD.

This is my grub list:
```

title           Debian GNU/Linux, kernel 2.6.18-5-486
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.18-5-486 root=/dev/hdb2 ro
initrd          /boot/initrd.img-2.6.18-5-486
savedefault

title           Debian GNU/Linux, kernel 2.6.18-5-486 (single-user mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.18-5-486 root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.18-5-486
savedefault

title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

And here is what i added to the bottom to try to get it to work ... but i fail cos my logic must be messed up or im not reading the other threads correctly
.
```

title           Slack
map             (hdd) (hdb)
map             (hdb) (hdd)
kernel          /boot/vmlinuz-2.6.21-5 root=/dev/hdd1 ro
initrd          /boot/initrd.img-2.6.21-5
savedefault

```

Shoudl the above be more like: (hd0) (hd1) as in other posts on the subject.

Thanks in advance :D

---

### Post by chewearn on 2008-01-01
Try replace:
map             (hdd) (hdb)
map             (hdb) (hdd)

with
root            (hd1,0)

---

### Post by Scarath on 2008-01-01
> **AstalaVista said:**
> Try replace:
map             (hdd) (hdb)
map             (hdb) (hdd)

with
root            (hd1,0)

thanks, that get the thing looking but tried it and it says:

 booting 'slack' 

root (hd1,0)
filesystem type unknown, partition type 0x82
kernel /boot/vmlinuz-2.6.21-5 root=/dev/hdd1 ro

and gives me an 

error 17 cannot find file type thing

I think maybe my file path is wrong ... ?

The problem is i cant get into HDD from my current install because it says i dont have the permissions, even when im root and even when i 'chown' the dev >.<

---

### Post by chewearn on 2008-01-01
Ok, I'm not familiar with slackware, maybe the linux kernel is not in the boot partition.  One possibility is it's in hdd3; then you change the line 
kernel          /boot/vmlinuz-2.6.21-5 root=/dev/hdd1 ro

to:
kernel          /boot/vmlinuz-2.6.21-5 root=/dev/hdd3 ro


Another approach, if slackware installed it's own bootloader: grub, lilo, or something else? in hdd1; you might be able to chainload this way:

title          slack
rootnoverify (hd1,0) 
chainloader +1

---

### Post by Scarath on 2008-01-01
> **AstalaVista said:**
> Ok, I'm not familiar with slackware, maybe the linux kernel is not in the boot partition.  One possibility is it's in hdd3; then you change the line 
kernel          /boot/vmlinuz-2.6.21-5 root=/dev/hdd1 ro

to:
kernel          /boot/vmlinuz-2.6.21-5 root=/dev/hdd3 ro


Another approach, if slackware installed it's own bootloader: grub, lilo, or something else? in hdd1; you might be able to chainload this way:

title          slack
rootnoverify (hd1,0) 
chainloader +1

now i get it, with slackware u have to 'make' you own initrd, fun eh? lol

I have been trying but i think the easiest option will be to reinstall slackware with lilo and do the chainloader +1 thing

I didnt install it the first time because i thought i wouldnt need it >.< 

Thanks for the advice

I shall post back if it works or doesnt as the case may be

---

### Post by Scarath on 2008-01-01
is there any problem with using both ext3 and ext2 to boot different OSs on the same system?

---

### Post by chewearn on 2008-01-01
> **Scarath said:**
> is there any problem with using both ext3 and ext2 to boot different OSs on the same system?

I don't think there should be a problem; though I can't say that with 100% certainty.

I do know the chainload thing should work; I have done that for a system with ubuntu and lfs.

---

### Post by Scarath on 2008-01-01
hmmm well i gave up :D i think when i re-install everything on my new HD (my old HD is dying) i'll install windows then slak then deb. And hopefully GRUB shud do all the work for me ... i hope

---

### Post by confused57 on 2008-01-01
I usually use chainloading to boot other distros, however, I wasn't able to install lilo to the Slackware root partition...I was able to boot Slack with:
```
title           Slackware12.0 on /dev/sda6 vmlinuz
root            (hd1,5)
kernel          /boot/vmlinuz root=/dev/sda6 ro
boot
```

Your entry may need "root (hd2,0)", without quotes, or possibly "root (hd1,0)"

Once I was able to boot into Slack, I installed grub, installing to the root partition...then I was able to use chainloading.

---

