---
title: "IO error, bad sector, hardware, freezing, noisy computer, etc"
date: 2014-03-11
forum: General Help
---

### Post by bjngchn on 2014-03-11
I will ask many questions, which may or may not be related... If I get input/output error,  is there something wrong with the harddisk, or can it be caused by something else? If it is caused by a bad sector, can't I just disable that sector to avoid such errors? ........ If a new computer gives such errors, does this mean there is a physical damage, or the computer is sold as new but is not new? ... How can we check if a computer is really new, and not something returned by another customer because of problems?......... If computer freezes for no reasons (such as emptying trash which has a few files of average size), what can we do about it? If we turn it off mechanically (like removing batteries, or pressing start button continuously) sectors may get  damaged. If we don't do this, it may get heated and worse may happen..... In an encrypted computer, if there is mounting error about a partition, but computer works nevertheless, does this mean encryption doesn't work? Can things which should normally happen in an encrypted way, happen in uncerypted way instead? ...... If unmounting a flashdisk with command line doesn't work, what can we do about it? .......... These questions may look unrelated, but maybe such problems are all caused by bad disk, so I ask everything at once. One more thing: If I'm not running any special program, but computer gets noisy and becomes hot can thee be a hardware thing running outside user control, such as a keylogger, wireless emitter, installed by seller or BB. Last question is theoretical, I'm not saying it is likely....And one more: how can we know whether a flash disk doesn't do bad things. it has some exe files, should we remove them?

---

### Post by 3rdalbum on 2014-03-11
This is too long and varied a post for most people to answer comprehensively. Consider asking each question separately.

Input Output Error is usually associated with a bad disk. Check the SMART Statistics in Disk Utility to see if there are any warnings. Bad sectors are remapped automatically but once you get more than a few it means your disk is no longer usable. Freezes can indicate bad RAM, a bad graphics driver or sometimes a failing hard disk.

---

### Post by Impavidus on 2014-03-12
Last night I was to tired to attempt answering this post, but I'll give it a try now.

**I/O errors** usually indicate a bad hard drive, although it couls also mean a loose connector or bad cable between the drive and the mobo. Most likely it's a hardware error. The drive should automatically remap bad sectors once a write to them is attempted. Occasionally hard drives have some production errors, leading to remapped sectors. This is no reason for concern, as long as the number of remapped sectors doesn't increase rapidly after some use. You can use the disks utility to check the **smart status** of the hard drive. It can give you the number of remapped sectors, the time the drive has been running, the number of start/stop cycles and other data. This may indicate whether it's a new drive or an old one. Emptying the trash involves writing to disk, so a freeze may indicate a bad hard drive. There are other possibilities too, like a loose ram stick or even having loads of items in trash may make deletion slower.

Mechanically turning off the computer may cause hardware damage, although disks should be reasonably safe, as the heads are retracted (by springs, IIRC from an old drive I once disassembled) before the disk spins down whenever power is removed. File system damage is likely, so it's best to avoid it. Instead, try [raising elephants]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses"). If the cooling systems of your computer are properly working it shouldn't overheat. Worst case is that the processor automatically trottles down and eventually shuts off to reduce power consumption and heating. If there is a failure mounting a partition and the computer works nonetheless, the partition that failed to mount was not vital to the system. It's possible that any writes to an encrypted partition that failed to mount end up in the directory on an unencrypted partition that was meant to be it's mount point.

If you can't unmount a flash drive, read the error message. Maybe some files on it are still open. If the computer gets hot for no apparent reason, run **top**. It will show you which processes are running. Furthermore, it could be a graphics driver problem, that prevents your graphics card from going into idle mode. It's very unlikely, although not entirely impossible, that it's malware, especially if you installed the system yourself. Flash disks don't do bad things by themselves. Executables on them are not automatically executed (unless you enable it) and furthermore, Linux cannot even execute .exe files, which are designed for Windows. Don't be afraid of the autorun.exe that would automatically install malware on Win XP as soon as the usb drive was inserted.

Sorry if this post is a bit difficult to read, but you asked so many things in one post...

---

### Post by bjngchn on 2014-03-14
Wow. this is almost a complete answer with useful info, and easy to read. Thanks for your time..

---

