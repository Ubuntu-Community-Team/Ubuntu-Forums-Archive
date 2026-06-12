---
title: "Partition table is a mess. Need to get files of HD but having trouble mounting."
date: 2007-02-05
forum: General Help
---

### Post by RegularX on 2007-02-05
EDIT: i'm using 6.10 if that matters.

so my HD is mess and i can no longer boot up windows (i was trying to install ubuntu along side windows and ran into all kinds of problems that lead me here). 

so now i need to get at my data, burn it to a DVD or put it on my flash drive (or if i can network with my mac boot move it to that directly without the use of the flash drive), but i have a problem. i can't mount my HD so that i can get access to it.

when i give the command "sudo mount -w -t ntfs /dev/sda2 /mnt/" the HD gets mounted but only root has access to it. i can see my files from the terminal. but as soon as i go back to the GUI i'm locked out from seeing them since i'm no longer the root user. further more, it is always mounted as read only (despite the use of the -w option).

so now i have 3 questions:
1. is there a way that i can log into ubuntu as root (and thus making this all a lot easier)?
2. if i can't log in as root is there a way to mount my HD so that the group (or owner) is set to 'admin' (or one of the other groups i belong to)?
3. how can i mount it as read/write so i can pull some data off it?

also, any help on networking my PC with my macbook using ubuntu (i'm not to versed in networking) would be greatly appreciated.

thanks in advanced for any and all help.

---

### Post by jd65pl on 2007-02-05
try staring a root user version of nautilus using the command below. Note be careful as you will have root access to system files, try to avoid editing any files just copy from one location to another as you could quite easy end up with a borked system

```
gksudo nautilus
```

---

### Post by SyvanX on 2007-02-05
Try this command

```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda2 /mnt/
```

that should allow non-root users to access the ntfs partition.

---

### Post by RegularX on 2007-02-05
thanks i'll give that a shot. the system is pretty much shot as it is, so i'm not too worried about doing anything. i don't plan on even mounting my backup partition drive (so i can quickly run a windows recovery) so nothing in that will be edited either.

my only concern now, however, is if i move the files to my macbook (which also runs on unix) will the files all have user root (or in the case of OS X wheel) as owner and groups as well? then i'll have to go through this whole song and dance again when i try to move the files from my macbook to my USB drive to my PC.

---

### Post by barney_1 on 2007-02-05
I would not recommend re-installing anything!!  You might be able to repair your partition table and avert that kind of nonsense.

First off, backup everything that you can!  This way you won't lose any more than you already have.  I take it from your first post that this is what you are doing.

I accidentally deleted my partition table in December when trying to change the partition table of a thumb drive.  It freaked me out and I thought a full re-install was going to be coming but that wasn't the case.  I was able to use a partition recover tool to get it back.  When I rebooted, nothing but a blinking cursor.  Ah, but I realized, grub didn't load.  I reinstalled grub by hand and voila, my system was back to normal.

I'm not certain now exactly what I did.  I know I started with help from this post:

[http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html](http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html)

and tried to use "gpart" (different from gparted) to guess the partition table.  This didn't get it exactly right. I kept searching.

My salvation is in the universe repositories.  I installed "testdisk"
```
sudo apt-get install testdisk
```

I ran the program:
```
sudo testdisk
```

Select your drive, it will sniff out the record.  Follow the onscreen prompts.  If you think it has it right, you can get it to write the partition table to the disk.  You will need to restart and then resore grub by hand in order to get boot choices.  I used post #2 from this thread for that:
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

