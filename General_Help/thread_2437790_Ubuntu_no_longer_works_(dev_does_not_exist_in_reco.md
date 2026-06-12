---
title: "Ubuntu no longer works (dev does not exist in recovery mode)"
date: 2020-02-29
forum: General Help
---

### Post by Budoc on 2020-02-29
Hello,

I have an old Samsung laptop running 14.04, which I was planning on upgrading to a newer LTS soon. Since earlier today it has stopped loading Ubuntu. I get the Samsung boot screen and then the grub menu. If I select ubuntu I get a blank purple screen and nothing happens. If I select the newest kernel in recovery mode, I get amongst other messages: ALERT! /dev/disk/by-uuid/6a1f44ea-14fe-4ee6-b108-5e331825-111c does not exist. Dropping to a shell!

How can I fix my computer and get back into Ubuntu?  I have obtained another computer so I can burn live CDs should I need to! 

Thank you so much for your help in advance

---

### Post by mörgæs on 2020-02-29
14.04 has been unsupported since april 2019. It's anyone's guess whether or not your OS has been attacked during the latest two years.

I suggest a clean install of a supported release right away. After that change all passwords which have been used in 14.04.

---

### Post by DuckHook on 2020-02-29
> **Budoc said:**
> &#8230;old Samsung laptop&#8230;
&#8230;ALERT! /dev/disk/by-uuid/6a1f44ea-14fe-4ee6-b108-5e331825-111c does not exist. Dropping to a shell!&#8230;
Purely an educated guess, but given age and error message, I would suspect that your HDD is failing/has failed. We have no idea of your partition layout, but at least one partition is corrupted. Obviously, this is common in old machines.
> &#8230;I have obtained another computer so I can burn live CDs should I need to!
[LIST=1]
[*]Yes, you will need to. If you have all of your important data backed up, then it's simply the minor bother of buying a new HDD/SSD, installing a new up-to-date OS, and restoring the lost data. Do not use 14.04. It is years past EoL and no one here can help you with it.
[*]If you have no backups and must recover lost data, then it's much more problematic. I'm no data recovery expert, so help must be requested from more qualified forum members, but you must not use the bad disk for *anything* until you recover the data off of it. Do not write to it, or read from it. Accessing it in any way will diminish your chances of data recovery until you recover as much as you can with data recovery software.
[*]It is safe to boot up from a LiveUSB/CD so long as you don't mount or read/write the bad HDD.
[/LIST]

---

### Post by Budoc on 2020-02-29
Thank you all for your responses. I've found a livecd for 16.04. Is there any way I can fix my system with that? I was due to upgrade my os, but an unforseen illness prevented that.

Is there any way of sharing screenshots here? Gparted can see my partitions, but I cannot link it to the error message I saw. 

If I can just get ubuntu back, I'd be most thankful. My wife uses the computer and some of her work is on there.

---

### Post by Budoc on 2020-02-29
I'm in a livecd session now with 16.04, this thread [https://ubuntuforums.org/showthread.php?t=2327903]("https://ubuntuforums.org/showthread.php?t=2327903") suggested I look at:

sudo blkid -c /dev/null -o list

here's the output:

> ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device                              fs_type       label          mount point                             UUID
----------------------------------------------------------------------------------------------------------------------------------------------
/dev/loop0                          squashfs                     /rofs                                   
/dev/sda1                           ntfs          Windows RE tools (not mounted)                         1E4E97C44E97935F
/dev/sda2                           vfat          SYSTEM         (not mounted)                           BA9A-A331
/dev/sda3                                                        (not mounted)                           
/dev/sda4                           ntfs                         (not mounted)                           4C369D27369D12D6
/dev/sda5                           ntfs          SAMSUNG_REC2   (not mounted)                           04D6A2FDD6A2EE5C
/dev/sda6                           vfat          SAMSUNG_REC    (not mounted)                           00A1-C78B
/dev/sda7                           swap                         [SWAP]                                  e3d8eb7a-ceb1-46cf-bca6-24b640488575
/dev/sda8                           ext4                         (not mounted)                           6a1f44ea-14fe-4ee6-b108-5e331825111c
/dev/sda9                           ext4                         (not mounted)                           92978cb8-65c3-42ac-a303-719e3d663c3f
/dev/sr0                            iso9660       Ubuntu 16.04.6 LTS amd64 /cdrom                        2019-02-27-09-57-36-00


the missing dev is sda8 which I think is /

I hope this helps!

---

### Post by CatKiller on 2020-02-29
> **Budoc said:**
> ALERT! /dev/disk/by-uuid/6a1f44ea-14fe-4ee6-b108-5e331825-111c does not exist.

> **Budoc said:**
> /dev/sda8                           ext4                         (not  mounted)                           6a1f44ea-14fe-4ee6-b108-5e331825111c

These are not the same. It could be a transcription error if you wrote it out by hand, or a typo if you'd been fiddling with fstab or grub, or the drive could be broken.

> **Budoc said:**
> If I can just get ubuntu back, I'd be most thankful. My wife uses the computer and some of her work is on there.

You should be able to mount the partitions from a live USB and copy the data that you want to preserve to somewhere else. Making routine backups is a sensible precaution for the future.

---

### Post by Budoc on 2020-02-29
> **CatKiller said:**
> These are not the same. It could be a transcription error if you wrote it out by hand, or a typo if you'd been fiddling with fstab or grub, or the drive could be broken.



You should be able to mount the partitions from a live USB and copy the data that you want to preserve to somewhere else. Making routine backups is a sensible precaution for the future.

Sorry, it's a typo  - I copied out the recovery mode entry by hand! I've not fiddled with grub or fstab at all.

I'm usually good at backups - a hospital stay has knocked my rhythm.

---

### Post by DuckHook on 2020-02-29
> **Budoc said:**
> …
If I can just get ubuntu back, I'd be most thankful. My wife uses the computer and some of her work is on there.
An oldish, but still decent link to valid recovery instructions: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Realistically, you cannot expect to "get Ubuntu back". Best to set lower expectations. If you can recover your critical data, consider yourself fortunate and move on from there. After recovery, you will likely need a new HDD and a new install, this time, as current as possible. Note that even Xenial (16.06) expires next year—and if it's a flavour like Lubuntu rather than Ubuntu-plain-vanilla, it has already exceeded its best-before date.

---

### Post by Budoc on 2020-02-29
Thank you. I shall take a look tomorrow. I think that my stuff should be backed up to an external drive as of a few months ago. My wife may have emailed her recent document to herself.

I don't want to show bad etiquette, but would it be worth me posting anything in the installations sub-forum, in case it's a grub problem? 

Sorry about all the questions, I'm a bit panicked and it's quite stressful taking it all in!

---

### Post by CelticWarrior on 2020-02-29
It's not a Grub problem, it's something wrong with sda8. 

You may try, in a live session, to run ```
fsck -fy /dev/sda8
```

but don't keep your hopes high.

---

### Post by DuckHook on 2020-02-29
> **Budoc said:**
> …I don't want to show bad etiquette, but would it be worth me posting anything in the installations sub-forum, in case it's a grub problem?…
If you have good reason to believe that it is a separate issue, then it is no problem at all to post a separate topic. In fact, that would be considered *good* netiquette. However, before doing any sort of exploring or testing of such theories, you must do a backup of your current HDD. Otherwise, you risk corrupting data that would otherwise be recoverable. The usual practice is to take out the questionable drive, make a dd copy to a known good drive, then do your recovery/experimentation on the known good drive.
> Sorry about all the questions, I'm a bit panicked and it's quite stressful taking it all in!
No need for apologies. The forums exist to help those in need. I must again stress that I am not the best resource for data recovery. But the forums are full of historical threads that deal with this unfortunately common topic, so they will be of use to you.

---

