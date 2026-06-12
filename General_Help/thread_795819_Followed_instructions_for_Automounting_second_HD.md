---
title: "Followed instructions for Automounting second HD"
date: 2008-05-15
forum: General Help
---

### Post by CaptMorgan on 2008-05-15
So I use a 500gb HD in my computer simply for storage
But some things like pictures are used for desktop background etc so I wanted to Automount the second disk so my background showed up on boot for example, so I followed the instructions on this page 

[http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3](http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3)

my drive is dev/sdb1 when I due sudo fdisk -l

so I go through the instructions and call name it MyFiles thinking it would be called that under Places, well it isnt there it is now /MyFiles

Is there a way I can undo all those steps?
1) My VM won't boot because I had a folder shared to /media/disk and now it just says inaccesible and its bumming me out (need for school)
2) I prefer it to be under places so I dont have to navigate to every time

Please help, thanks

---

### Post by EXCiD3 on 2008-05-15
Can't you edit the VM's share to look for /MyFiles?

Unfortunately I'm not exactly sure why it wont show up in the Places folder if you setup everything correctly. Post your fstab.

---

### Post by CaptMorgan on 2008-05-15
> **EXCiD3 said:**
> Can't you edit the VM's share to look for /MyFiles?

Unfortunately I'm not exactly sure why it wont show up in the Places folder if you setup everything correctly. Post your fstab.

here is my fstab from cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=87c20a1e-9039-4494-aa58-68fcc98f3e51 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=40f5e5be-ee98-4d7c-9982-44dbddd316b5 /home           ext3    relatime        0       2
# /dev/sda5
UUID=63ef8b30-0822-446c-93df-2d83035a8f67 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /MyFiles ext3 defaults 0 0
elcapitan@elcapitan:~$

---

### Post by EXCiD3 on 2008-05-15
If you remove the /dev/sdb1 line from your fstab this should revert everything back to normal, however im not sure whether or not the drive will still automount to /media/disk. If you are using Virtualbox, just try editing the share folder to /MyFiles instead of /media/disk, that way you wont need to change your fstab. I think you need to create the folder in /media in order for the place to show up in the Places menu, but im not sure. You could try creating a symbolic link to /MyFiles in your /medai folder by running this in terminal: ```
ln -s /MyFiles /media/MyFiles
```This creates a fake directory in /media that actually is /MyFiles. You could run the same command replacing /media/MyFiles with /media/disk and that would be another way of fixing your VM problem.

More on symbolic links: [http://kb.iu.edu/data/abbe.html](http://kb.iu.edu/data/abbe.html)

---

