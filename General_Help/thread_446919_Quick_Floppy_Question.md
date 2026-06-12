---
title: "Quick Floppy Question"
date: 2007-05-17
forum: General Help
---

### Post by ComputerPsi on 2007-05-17
After some frustration, I figured out the Linux "mounts" the floppy by copying all the data from the floppy into the memory. Then you can change anything in the memory. When you unmount, the information gets written to the disk. This theoretically speeds up some floppy processing in some special cases. However I want to be able to directly read and write from and to the floppy. Do you know how that can be done?

Thank You,
ComputerPsi

---

### Post by vtel57 on 2007-05-17
I don't believe you can direct write to the floppy in the graphical interface. You can direct write to floppy using a command line editor such as VIM. I just tested this on my own system. When you save a test file to the floppy with VIM, it writes to the disk immediately.

EVERYTHING in GNU/LInux is seen by the OS as a file. Everything! Your modem is a file. Your hard drive partitions are each a file. Your floppy is also a file. In the graphic environment, you manipulate the file for your floppy as you read/write to it. However, it doesn't actually write to the disk until you unmount the device.

I think that's just the way it is... stand by for some opinions from others more versed in GNU/Linux mysteries, though.

Luck! :)

~Eric

---

### Post by vtel57 on 2007-05-17
By the way, you could try this:

Add "sync" to your fstab entry for your floppy...

/dev/fd0  	/media/floppy  	auto  	rw,noauto,user,sync  	0 0

What sync does:

**sync and async** How the input and output to the filesystem should be done. sync means it's done synchronously. If you look at the example fstab, you'll notice that this is the option used with the floppy. In plain English, this means that when you, for example, copy a file to the floppy, the changes are physically written to the floppy at the same time you issue the copy command.

The above is from:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I'm not sure if this will do what you're trying to do. On my Slackware system, I'm having mounting issues with my floppy, so I can't test for you right now. :(

---

### Post by heimo on 2007-05-18
> **vtel57 said:**
> 
Add "sync" to your fstab entry for your floppy...


I thought about recommending that too, until I saw this in mounts manual page:
> 
              The following  options
              apply  to  any  file system that is being mounted (but not every
              file system actually honors them - e.g., the sync  option  today
              has effect only for ext2, ext3 and ufs):


It's still worth trying. There's also command line command sync which flushes file system buffers.

---

### Post by vtel57 on 2007-05-18
AH! I knew there was a reason why sync might not work on a floppy. I just couldn't remember what it was. Thanks, heimo! Like you say, though... wouldn't hurt to try it. :)

---

### Post by ComputerPsi on 2007-05-18
Thank you for the responses.. Well I checked out /etc/fstab and whether or not the floppy was mounted, "/media/floppy" didn't appear in the file. Am I looking in the wrong area?

Thanks,
ComputerPsi

---

### Post by vtel57 on 2007-05-18
Can you post your fstab here, ComputerPsi? Just COPY/PASTE into the message area.

---

### Post by ComputerPsi on 2007-05-18
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

hope it helps..

---

### Post by vtel57 on 2007-05-18
That's interesting. No floppy entry in the fstab. What type of floppy is this? Is it an internal floppy or a USB-type floppy? I'm assuming that whatever it is, you are able to access it and read/write to it, currently. Right?

---

### Post by ComputerPsi on 2007-05-18
3.5 inch internal 1.44 MB floppy FAT12 formatted. I can write by mounting and unmounting the floppy. The fstab file contains no change since 2006..

-rw-r--r-- 1 root root 398 2006-05-30 20:49 /etc/fstab

---

### Post by heimo on 2007-05-18
Try mounting with fdmount and its -s flag.

---

### Post by vtel57 on 2007-05-18
A typical mount entry for fstab would look something like this:

```
/dev/fd0     /mnt/floppy      auto     rw,user,noauto,sync     0     0
```

Adding this to your fstab will allow you to mount the floppy from the graphic interface, as a user.

---

### Post by ComputerPsi on 2007-05-18
heimo: When I type in "fdmount -s" when it's unmounted, I get "fd0 doesn't exist." When I type in mounted, I get "it's already mounted."

vtel57: First of all, I had to enable rights to write to fstab.. I couldn't otherwise. Second, I put in your line when it was unmounted, Now I cannot mount it any more.. gives me some error.

---

### Post by ComputerPsi on 2007-05-18
Okay, I removed the line in fstab, and mounted. I tried changing something, but the floppy driver didn't do anything. I tried unmounting but I got the error again. The error is in Russian.. (My ubuntu was configured to the Russian language).. so I'll try translating..

Unable to unmount this drive

umount: mounted /dev/fd0 is conflicting with fstab

---

### Post by vtel57 on 2007-05-18
Hmm... I just looked at my fstab in Ubuntu (6.06). I don't have a floppy entry either. I'm not sure what method is used for mounting the floppy in Ubuntu. I'll have to do some research on it.

In the meantime,

```
 $ sudo gedit /etc/fstab
``` 

and remove the entry that I gave you.

---

### Post by vtel57 on 2007-05-18
> **ComputerPsi said:**
> Okay, I removed the line in fstab, and mounted. I tried changing something, but the floppy driver didn't do anything. I tried unmounting but I got the error again. The error is in Russian.. (My ubuntu was configured to the Russian language).. so I'll try translating..

Unable to unmount this drive

umount: mounted /dev/fd0 is conflicting with fstab

Reboot your machine.

---

### Post by ComputerPsi on 2007-05-18
I'm sorry.. I removed the line, then mounted, then put the line back in.

Still reboot?

---

### Post by vtel57 on 2007-05-18
I would reboot if you're still getting any mount errors after removing the line from fstab.

---

### Post by ComputerPsi on 2007-05-18
It can unmount without the line. It pretty strange how linux works with these type of things.. The main reason why I needed to write to the disk instantly is because I'm writing up an operating system and testing it on my other machine. At the moment the OS is small enough to fit on a floppy, which is why I use it to boot. Having to wait for the thing to mount really slows down the testing progress.. (Can't use Bochs at the moment..). I can write directly to a specific floppy sector, but things get a little sloppy when changing files in a FAT system.

---

### Post by vtel57 on 2007-05-19
Well, as long as everything is OK now. I wouldn't have wanted your system to be screwed up by anything that I suggested to you.

Here's a brief tutorial about the floppy drive and how it works in Linux.

[http://www.linuxheadquarters.com/howto/basic/floppy.shtml](http://www.linuxheadquarters.com/howto/basic/floppy.shtml)

Luck!

~Eric

---

