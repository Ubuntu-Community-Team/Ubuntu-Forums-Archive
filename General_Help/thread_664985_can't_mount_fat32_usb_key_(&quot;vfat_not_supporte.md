---
title: "can't mount fat32 usb key (&quot;vfat not supported&quot;)"
date: 2008-01-11
forum: General Help
---

### Post by pressed on 2008-01-11
I have two usb keys (usb drives, thumb drives, pen drives, memory sticks) and neither of them will mount in ubuntu gutsy. when i put either one in i get the message:
 > The volume '$USB_DRIVE' uses the *vfat* file system which is not supported by your system. 

one is an OCZ rally, the other is an old lenovo drive. this strikes me as strange, since a google of "vfat file system" implies that linux has supported it for a long time now.

i have disabled the 'usefree' option as suggested in [this]("http://ubuntuforums.org/showthread.php?t=582045&highlight=%5BSOLVED%5D+vfat+usb") thread, and i have gone through all the other posts i could find on the forum but none reported a similar error message.

here are some potentially relevant details:
- these keys *can* be used successfully in windows machines, and they were carefully ejected before removal. 
- i had an issue where my external hard drive wasn't being recognised either except after a reboot, but fixed it by rebooting and then properly ejecting the drive. the usb drives still dont work. (its probably not relevant.)

---

### Post by geraldm on 2008-01-11
Linux does support the vfat filesystem, but there must be a module that understands that in your system.  Mine has it, and here is the file config option in which I selected it:
```

 grep 'VFAT' /boot/config-`uname -r` 
 ls /lib/modules/`uname -r`/kernel/fs/vfat

```
which returns:
CONFIG_VFAT_FS=m
vfat.ko

You may need to rebuild your kernel with the option for VFAT_FS if you do not have it; otherwise you may just need to load that module before plugging in the dongle.

Gerald

---

### Post by pressed on 2008-01-11
I'm sorry, but how do i do those things?

---

### Post by strabes on 2008-01-11
Open a terminal and paste them in. (by just highlighting them with a triple click and middle clicking in the terminal). For more information, check out these pages:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

---

### Post by pressed on 2008-01-12
Thanks strabes. The commands geraldm gave return the same values for me as he gave in his reply. But I don't know how to "rebuild your kernel with the option for VFAT_FS if you do not have it; or "load that module before plugging in the dongle." Also, would I be able to have the module be loaded when the dongle is plugged in?

---

### Post by pressed on 2008-01-15
could anyone tell me how to safely rebuild my kernel? i've already broken my OS a few times....

---

### Post by geraldm on 2008-01-15
Pressed:
You should be able to get by without rebuilding the kernel because you said that the commands that I showed here return values the same as the values I posted.  Just load the vfat module.
```

sudo modprobe vfat
lsmod | grep vfat -

```
The above code should show two lines, confirming that vfat.ko module is loaded.
Then plug in the dongle.

Gerald

---

### Post by pressed on 2008-01-15
hmm... although i confirmed (again) that your commands in #2 return the same values, i'm afraid that code doesn't work. I get:
```
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/fs/fat/fat.ko': No such file or directory
FATAL: Error inserting vfat (/lib/modules/2.6.22-14-generic/kernel/fs/vfat/vfat.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

does this mean i need to take the kernel option? thanks very much for your help

---

### Post by catgal on 2008-03-10
hi all

I have the same problem , maybe worse actually,  as  no vfat.ko  exists in   /lib/modules/2.6.22-14-16-generic/kernel/fs 

it discovers USB flash, it used to mount them ok also.
I was impressed by the stability so far of 7.10 (xubuntu).  What is the next step to try ? 

any hints as to how  I rebuild the kernel with VFAT option?

( as to the cause of the problem: might it be that i mounted some image files of type vfat (FAT 16 actually, superfloppy  type) with mount -o loop? ) At the time the mounting seemed ok, I mean files and directory structure was ok. I had a couple crashes (coming from hibernation). ACPI probably not very robust on packard bell Easynote E1 series laptop?  [  i had to do  couple fsck as read only and answer [y] many times not really knowing actually much about the corections]  .... 

a kernel module for a filesystem can desapear from fsck fixing ? is that the only way

time to learn a bit about syslogs  any tips?


cheers
gina

(btw i also used  dd  :)  only writing to files so far, so cant be that esoteric problem (i hope) . for the moment no possibility to get data out of laptop:( sigh..... only CD burnig? or can I try to format a usb flash some other way? ext from other windows machine  it's possible?

---

### Post by pressed on 2008-03-11
Hey catgal,

Just for the record, I resolved my problem by backing up my home folder and reinstalling Ubuntu. Not a very clever solution, but it worked... Automatix2 helps make setup easier :(

---

### Post by catgal on 2008-03-11
hello 

thanx:) but, well,  i think reintalling should be the last resort, no?.

How long it takes to reinstall?, for me xubuntu install and reformat took about 40min.

Apart from the vfat.ko dissapearing xubuntu seems pretty stable so
maybe fixable? 

 I found ext2IFS to try in the meantime, for getting data in and out.

cheers

---

