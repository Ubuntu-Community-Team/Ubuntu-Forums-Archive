---
title: "Windows partition"
date: 2007-03-30
forum: General Help
---

### Post by bastardo on 2007-03-30
Hi there,

I'm getting paranoic, yesterday I was cleaning my disk...and I guess I destroyed windows partition. :( 
When I boot and choose Windows OS, nothing happens. I have to enter a key to go back to GRUB.

[http://i9.tinypic.com/4dnn1pf.png](http://i9.tinypic.com/4dnn1pf.png)

I choose activate but I get no successful. Any ideas? Format? 

Thanks and sorry for the poor english.

---

### Post by bastardo on 2007-03-30
This is what I get @ GRUB:

[img]http://i10.tinypic.com/2wn5yr6.jpg[/img]

---

### Post by x1a4 on 2007-03-30
Hi,

GRUB doesn't seem to recognize the file system, and there appears to be an issue with XP's boot loader.  Do you have windows installed on an NTFS partition?  

Please post the output of 

*cat /etc/fstab*

---

### Post by bastardo on 2007-03-31
> **x1a4 said:**
> Hi,

GRUB doesn't seem to recognize the file system, and there appears to be an issue with XP's boot loader.  Do you have windows installed on an NTFS partition?  

Please post the output of 

*cat /etc/fstab*

Yes, it's on an NTFS partition.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs notail          0       1
/dev/hda6       /home           reiserfs defaults        0       2
/dev/hda1       /mp3            vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /p2p            vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



Thanks

---

### Post by x1a4 on 2007-03-31
My bad.  I meant _/boot/grub/menu.lst_.

Sorry. 

Although you might want to add your windows partition to _/etc/fstab_ so you'll have it mounted when you boot Ubuntu.

---

### Post by bastardo on 2007-03-31
> **x1a4 said:**
> My bad.  I meant _/boot/grub/menu.lst_.

Sorry. 

Although you might want to add your windows partition to _/etc/fstab_ so you'll have it mounted when you boot Ubuntu.

And how do I make that? Sorry...I'm kinda noob...

---

### Post by Dream. on 2007-03-31
Have a look here... pretty easy  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


 Judging by the look of your output of cat **/etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda5 / reiserfs notail 0 1
/dev/hda6 /home reiserfs defaults 0 2
**/dev/hda1 /mp3 vfat defaults,utf8,umask=007,gid=46 0 1**
**/dev/hda2 /p2p vfat defaults,utf8,umask=007,gid=46 0 1**
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

**vfat** means its on a **fat32** filesystem not **ntfs**, see highlighted lines above

---

### Post by bastardo on 2007-03-31
> **Dream. said:**
> Have a look here... pretty easy  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


 Judging by the look of your output of cat **/etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda5 / reiserfs notail 0 1
/dev/hda6 /home reiserfs defaults 0 2
**/dev/hda1 /mp3 vfat defaults,utf8,umask=007,gid=46 0 1**
**/dev/hda2 /p2p vfat defaults,utf8,umask=007,gid=46 0 1**
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

**vfat** means its on a **fat32** filesystem not **ntfs**, see highlighted lines above

Thanks! I made like the link you posted says...and now Windows appears be mounted!

[IMG]http://i3.tinypic.com/29cp3wj.jpg[/IMG]

But when I reboot and go to GRUB and choose Windows, the error still there :confused: :confused: 

[img]http://i10.tinypic.com/2wn5yr6.jpg[/img]

What more can I do? :confused:

---

### Post by Dream. on 2007-03-31
Are you sure windows is still on the drive? If you followed the instructions on the link properly then it should boot fine. Maybe go through the procedure again to make sure.

If it still doesnt work you may have to reinstall windows. (If you dont want to lose your files use the " leave current file system intact" option when you reinstall)

You will have to reload your grub after you reload windows, I had a similar problem you can find out what you need to know here...  [http://www.ubuntuforums.org/showthread.php?t=396221](http://www.ubuntuforums.org/showthread.php?t=396221)

**Read all of the above thread you will find what you need to know.**

---

### Post by bastardo on 2007-03-31
> **Dream. said:**
> Are you sure windows is still on the drive? If you followed the instructions on the link properly then it should boot fine. Maybe go through the procedure again to make sure.

If it still doesnt work you may have to reinstall windows. (If you dont want to lose your files use the " leave current file system intact" option when you reinstall)

You will have to reload your grub after you reload windows, I had a similar problem you can find out what you need to know here...  [http://www.ubuntuforums.org/showthread.php?t=396221](http://www.ubuntuforums.org/showthread.php?t=396221)

**Read all of the above thread you will find what you need to know.**

Yep, still there...take a look:

[IMG]http://i7.tinypic.com/2cyk1fl.jpg[/IMG]

I'll read your thread...thanks again!

---

### Post by bastardo on 2007-03-31
I can't even boot windows cd...nothing happens...he goes straight to GRUB! :confused:

---

### Post by Maestro23 on 2007-03-31
> **bastardo said:**
> I can't even boot windows cd...nothing happens...he goes straight to GRUB! :confused:

You have the CD drive as the first boot option in you BIOS right?

---

### Post by Dream. on 2007-03-31
You need to change your boot device priority in the bios to cdrom instead of harddrive. Maybe google on how to do this for your pc. (usually F2 or delete to get into bios)

Also I would try and run a repair of windows and only use the "leave current file system intact" option if you dont get an option to repair.

I have not tried to repair or reinstall windows with linux partitions on the same harddrive so I dont know if it will create any further problems for you. Maybe do a search of these forums to see if anyone else has had problems arise with the procedure.

---

### Post by bastardo on 2007-03-31
> **Maestro23 said:**
> You have the CD drive as the first boot option in you BIOS right?

Yes.

[IMG]http://i5.tinypic.com/2w3xqvk.jpg[/IMG]

---

### Post by bastardo on 2007-03-31
> **Dream. said:**
> You need to change your boot device priority in the bios to cdrom instead of harddrive. Maybe google on how to do this for your pc. (usually F2 or delete to get into bios)

Also I would try and run a repair of windows and only use the "leave current file system intact" option if you dont get an option to repair.

I have not tried to repair or reinstall windows with linux partitions on the same harddrive so I dont know if it will create any further problems for you. Maybe do a search of these forums to see if anyone else has had problems arise with the procedure.

Thanks...that's not a problem for me...not a lot of information @ windows partition...I'm getting desperate with this computer lol...I just want that he boot up the windows cd.

---

### Post by Dream. on 2007-03-31
[QUOTE=bastardo;2383817]Thanks! I made like the link you posted says...and now Windows appears be mounted!

[IMG]http://i3.tinypic.com/29cp3wj.jpg[/IMG]

It Looks like the partition there is is number 3, but in your boot error screenshot you have the following code..

```
root(hd0,0)
```

Try this code instead before you run the xp disk

```
root(hd0,2)
```

You will have to edit the fstab file again (and yes it should be 2 not 3)

---

### Post by Maestro23 on 2007-03-31
Judging from that screenshot, the CD is #3 in the boot order behind the HDD.  That is why the Windows CD is not booting.  You need to move the CD up to the #1 position.

---

