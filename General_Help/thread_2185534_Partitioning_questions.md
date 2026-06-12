---
title: "Partitioning questions"
date: 2013-11-03
forum: General Help
---

### Post by grak90 on 2013-11-03
Hello there,

I needed to ask for help since I wanted to assign more space to my ext4 partition without losing data.

So the thing is I wanted to resize/move the partitions to expand sda1 (ext4) by getting memory from sda4 (ntfs, no OS inside).

Problem comes when the partitions are apart one from another, which means I would have to move the partitions until the ext4 and ntfs are one next to another.

Would this cause the system not to boot? I've been reading that if I move my ext4 partition, grub wont select the correct HDD sector and thus wont even boot. Furthermore, if I also move the "System Reserved" partition, which seems to be holding windows boot, it would become unbootable too right?


So, by having a look at this screenshot:

[IMG]http://i21.photobucket.com/albums/b264/takiush/instantaacutenea1_zpse368a7a1.png[/IMG]

Would you say it is possible to assign any more space to my ext4 partition without losing any data? Without making my system unbootable?

Thanks for all your help, I'm not sure if this question belongs to this forum, I just didnt know where to put it.

---

### Post by TheFu on 2013-11-03
Make a 100%, perfect, know-it-works backup.  Do not do anything else before you complete this.

Changing the order of partitions can turn out very badly for Windows. Moving Windows partitions can force a reinstall. With Linux, we have the expertise to move anything almost anywhere and recover. This will require use of non-GUI tools, however. How comfortable are you with grub_install?

Instead - just make more room for sda4 and leave sda1 alone.

Using Windows, reduce the size of sda3 by the amount you want. There are lots of how-tos on the internet if Windows is stubborn. DO NOT use gparted.  Verify that Windows boots when you are all done.

Using gparted, expand the sda4 partition into the newly created area between sda4 and sda3.

BTW, you are using all 4 primary partitions. Not an issue today, but ....  Ask about that when you are ready - usually it is easiest to accomplish during a HDD swap.

Last, it would be more helpful to copy/paste the output from **sudo parted -l** (wrapped in _code_ tags) rather than using GUI stuff that is less exact. Characters are more efficient too. ;)

---

### Post by Impavidus on 2013-11-03
I would solve the problem in a radically different way.

First of all, is this the only disk in the computer? If not, tell what's on the other disk (**sudo parted -l** will tell automatically) and ignore the rest of this post. I don't see a swap partition. A swap partition isn't stricktly necessary, but usually recommended.

I would use Windows to make backups of all files from sda4 on sda3. There's plenty of space. Also back up all important files to an external disk, just in case something goes wrong (i.e., you delete the wrong partition. Shouldn't really happen, but it's best to have them backed up anyway.).

Then boot from a live disk, delete sda4, create an extended partition where sda4 used to be and create inside the extended partition some more partitions. In fact, you can even do it from your installed Ubuntu system, without using a live disk. Make one ext4 partition, one ntfs partition for shared data between Windows and Ubuntu and a small swap partition (unless you don't want one). Then move your /home directory to the new ext4 partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). If you follow those instructions it can't really go wrong, even in case of a power failure. When using sda1 only for system files, 22GB should be large enough. The files you backed up to sda3 can be copied back to the new ntfs partition. You may want to edit fstab to mount the shared ntfs partition automatically. If you create a swap partition, add it to your fstab too.

Using this strategy you don't have to move large amounts of data on your disk (i.e., it's fast) and it should never put your computer in an unbootable state or cause data loss, even in case of a power failure.

---

### Post by coffeecat on 2013-11-03
It's hard to tell because the text in your screenshot is so tiny, but your sda2 partition looks to be the boot partition for Windows (probably 7?) on sda3. If so, you would be unwise to move it. I can't remember the precise details, but the problem is something about Windows boot files referencing the absolute location on disc of the boot sector of that partition rather than the relative location. If you move it, you are in danger of making Windows unbootable.

---

### Post by Bucky Ball on 2013-11-03
Yea, just a tip. Please attach large pics rather than inserting them in the body of your posts. 'Go Advanced' and use the paperclip icon. Spare a thought for those with slow connections and vision issues.

I can't read that either, so don't have much to say. ;)

---

### Post by grak90 on 2013-11-03
Here is what "sudo parted -l" shows:

"Modelo: ATA TOSHIBA MK6476GS (scsi)
Disco /dev/sda: 640GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos


Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  24,1GB  24,1GB  primary  ext4
 2      24,1GB  24,2GB  105MB   primary  ntfs                 arranque
 3      24,2GB  332GB   308GB   primary  ntfs
 4      332GB   640GB   308GB   primary  ntfs"


And here I will atach the screenshot, I didnt notice it was so blurry lol

Oh and I only got one hard drive.

So as far as I got, best option I see is to erase sda4 (no important stuff there, I can format without backing up anything), reformat it into ext4 and move /home there.

Now Ive got a couple of questions about this:

Is it really that important to have a swap partition? I've got 4gb ram.

Supposing I finally move /home to the new ext4 partition, will the 22gb be surely enough for linux system files?


It just keeps uploading the image with less resolution it was made with. 

Heres the direct link: [http://i21.photobucket.com/albums/b264/takiush/instantaacutenea1_zpse368a7a1.png~original](http://i21.photobucket.com/albums/b264/takiush/instantaacutenea1_zpse368a7a1.png~original)

---

### Post by TheFu on 2013-11-03
Sounds like a good plan.

Having -some- swap  is important, so that when memory becomes tight, the machine slows down instead of crashing.  Some desktop apps are terrible about RAM use, so it is easy to use up all that you have.  On servers with extremely well-known workloads, swap can be ignored, provided RAM is always greater than need.  On a desktop, I always have -some- swap.  

How are you backing up without another HDD?  Even a cheap 500G USB drive could be enough. Think I got one 3 weeks ago for $45.
[I]
Every hard drive will fail - and it will **never** be at a convenient time.[/I]

---

### Post by coffeecat on 2013-11-03
> **grak90 said:**
> 
It just keeps uploading the image with less resolution it was made with. 

Heres the direct link: [http://i21.photobucket.com/albums/b264/takiush/instantaacutenea1_zpse368a7a1.png~original](http://i21.photobucket.com/albums/b264/takiush/instantaacutenea1_zpse368a7a1.png~original)

There's a 1024x768 limit on images uploaded to the forum. It will resize anything bigger, but 1024x768 should be sufficient. Part of the problem is that you have set a very small font in your desktop settings. Most people's uploaded gparted screenshots are entirely readable.

In fact, photobucket has reduced the size of your image even more than the forum software! It's more difficult to see on Photobucket.

---

### Post by grak90 on 2013-11-03
I finally made it !

I made two partitions from sda4, one is a big ext4 partition in which I migrated my /home folder. The other is a 4001mb swap partition which I activated from fstab.

Thank you so much for your precious time, it really helped me out =)

---

### Post by Bucky Ball on 2013-11-03
Good news. Could you mark thread as 'solved' to help others, please? ;)

---

