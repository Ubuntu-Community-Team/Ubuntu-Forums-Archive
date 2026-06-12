---
title: "Ffile system check failed."
date: 2007-07-08
forum: General Help
---

### Post by kaj on 2007-07-08
I installed Dreamlinux on a one of my partitions in my triple-boot system, and after that I can't boot Ubuntu Feisty.
It tells me: fsck died with exit status 8. Please repair the file system manually.
I have tried with fsck and varius options, but it tells me, that nothing is wrong.

I installed the Dreamlinux without installing a boot-loader, as I would add it in my existing menu.lst in Ubuntu's bootloader, as I normally do, but anyhow I was unable to boot Ubuntu afterwards.

In teh maintenance shell, that is appearing, I am able to mount sda1 and sda5, and when I write halt, the boot-proces is resumed, and I can boot the system, but afterwards I can't mount the other partitions in teh system. It tells me, that they are not in fstab or mtab, but that is not true. My fstab has allways worked just fine, and it is not altered.

My partitions are as follows:
sda1:  ext2   /boot   Ubuntu 7.04
sda2: swap
sda3:  ext3    /           Ubuntu 7.04
sda5:  ext3    /home  Ubuntu 7.04
sda6:  ext3                Dreamlinux
sda7:  ext3                PCLinuxOS
sda8:  fat32               Data

And I can boot both Dreamlinux and PCLinuxOS, from witch I work right now.

I have searched this forum for a solution, and I can see, that others have had similar problems, but as far as I can see, they are not solved.

I would be very sorry, if I have to reinstall the whole system, when I think of all the trouble, I had with the settings and installation of special programs, not to mention the hell, I went through getting my Canon printer to work.

regard from Kaj
Denmark

---

### Post by rsnow on 2007-07-26
Same problem here. Apparently no one knows how to fix this. 

On some forums a company tech will occasionally drop in and help out. Does Ubuntu do this or are we strictly on our own?

Maybe we need to SHOUT - HELP!

---

### Post by louieb on 2007-07-26
I would guess the uuid id of your partitions has changed. Its a pain but to check
compare the uuids in /etc/fstab with the output of 
```
ls -l /dev/disk/by-uuid/
```

A partitions UUID is not suppose to change. Thats one of the reasons Ubuntu went to using them. But I've had them change on me.

---

### Post by neptune on 2007-10-20
> **louieb said:**
> I would guess the uuid id of your partitions has changed. Its a pain but to check
compare the uuids in /etc/fstab with the output of 
```
ls -l /dev/disk/by-uuid/
```

A partitions UUID is not suppose to change. Thats one of the reasons Ubuntu went to using them. But I've had them change on me.
So if thats the case, how do you fix the UUID being different?

---

### Post by neptune on 2007-10-21
Any what if the UUIDs are the same but problem still persists??
See my issue --> [http://ubuntuforums.org/showthread.php?t=583294](http://ubuntuforums.org/showthread.php?t=583294)

---

