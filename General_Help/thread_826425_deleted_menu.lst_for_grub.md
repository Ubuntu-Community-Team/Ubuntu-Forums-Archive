---
title: "deleted menu.lst for grub"
date: 2008-06-11
forum: General Help
---

### Post by Luke has no name on 2008-06-11
Can I rebuild?

---

### Post by Yuki_Nagato on 2008-06-11
[http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst")

Give this a shot.

It is a pretty much standard GRUB menu.lst file.  You will need to customize it with your specific kernal image and such, but merely copying and pasting the edited file into /boot/grub will fix the problem.

---

### Post by louieb on 2008-06-11
I'm sure you can but I haven't had to build a menu from scratch. 
The [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") would probably do it.
From the man pages of update-grub: looks like it will do it to.
> 
File: *manpages*,  Node: update-grub,  Up: (dir)

update-grub(8)                                                  update-grub(8)

NAME
       update-grub - program to generate GRUB's menu.lst file




---

### Post by Anduu on 2008-06-11
I would try reinstalling grub first...it should regenerate the menu.lst

---

### Post by fusionisthefuture on 2008-09-22
hi guys, 

im trying something for fun... i want to install grub onto a usb flash drive with 3 partitions.  on the first, which is 40 MB, i have grub, just the command line, without the menu.lst.  on the second, i want to have pendrivelinux.com's live cd version of ophcrack, and on the third i want to have whatever iso of whatever linux i want to install next (oh it will be ubuntu, dont worry), so that i dont have to keep burning cds.  

my first question is what exactly is needed to boot live cd kernels.  do i need all that UUID crap thats in all the ubuntu entries?  i have the ophcrack folder ready to go, if i put it on a ready-to-boot usb drive, it will run just fine, i just want to put it on its own partition, and have grub point to it.  

thanks ahead,
-fitf

---

### Post by x1a4 on 2008-09-22
> **Luke has no name said:**
> Can I rebuild?
```
sudo /sbin/update-grub
```

---

### Post by fusionisthefuture on 2008-09-22
well see, i cant yet boot to any of the operating systems that are on the flash drive, so i dont have a terminal to type in.

p.s. i tried the super grub disk for usb, and it booted and just sat there and said GRUB_______

im pretty sure i already know teh answer to this is no, but if i cd to a directory, like my usb drive, then do the update grub, will it do it for my root filesystem, or only that directory?  
thanks,
-fitf
p.s. lol i just realized the above wasnt a reply to me. aha

---

### Post by fusionisthefuture on 2008-09-24
well, i sort of figured this out.  

so far ive gotten this to work with both the ophcrack and mythbuntu live cds that ive tried, but not with an alt install of hardy.  i can boot the kernel alright, but once it loads and starts the install, it tries to mount the cdrom, which is of course not there.  thats not so bad, once it fails you can skip that part, but the next part tries to find a preseed file, located on the cdrom in the /preseed directory.  im not sure what to do about this.  the isolinux.cfg file, that i used to create my grub entry has an entry for this ```
file=/cdrom/preseed/something (i cant see it right now)
```
i tried using that as a kernel option, and deleting the /cdrom directory so it was just ```
file=/preseed/something
```
but the installer cant find the file, and it is there.  i think it might be looking in one of the other partitions on my usb flash drive.  

the layout of the drive is such:  
2+ GB partition at the front of the drive
1 GB partition in the middle, labeled boot, with grub and ophcrack on it.
700 MB partition at the end, for an ubuntu live cd (or possibly alt install)

---

