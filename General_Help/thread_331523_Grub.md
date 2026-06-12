---
title: "Grub"
date: 2007-01-04
forum: General Help
---

### Post by CCBalla10 on 2007-01-04
Ok guys...after months of happy use with 6.10 I have finally messed it up.  Tried to install a grub image to make Ubuntu more custom.  Well...now when I turn on the laptop it says failed to read grub image from blah blah blah...then it says press any key to continue.  when I press any key it loads the original grub screen, but when I choose any option (whether XP or Ubuntu) it restarts the comp and I have to start over.  I have also tried to press C for command line to edit my grub file, but it also restarts the comp.  Any way to fix this?

---

### Post by scrooge_74 on 2007-01-04
Maybe boot from a live CD, mount your disk and undo what ever you did.

Good luck

---

### Post by smoker on 2007-01-04
have a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)

hope this helps

---

### Post by CCBalla10 on 2007-01-04
^Smoker

I would use that guide if I could get to the command line.... and how would I mount my live cd?

---

### Post by smoker on 2007-01-04
change your computer to boot from cd first, then insert the live-cd, it should auto-run then.

---

### Post by CCBalla10 on 2007-01-05
Ok now that I've gotten the Live CD to start up...how do I change files to my already existing system?

---

### Post by scrooge_74 on 2007-01-05
mount the drive and then sudo in to change the files

---

### Post by CCBalla10 on 2007-01-05
so how do I mount the drive? sorry never done this before

---

### Post by bulldog on 2007-01-05
> **CCBalla10 said:**
> Ok now that I've gotten the Live CD to start up...how do I change files to my already existing system?

Can you give the output of```
cat /boot/grub
```
Keep in mind you have mounted your install so you need to put some extra folders [mount point and your hda?]in front of /boot.

---

### Post by CCBalla10 on 2007-01-05
so when i type cat /boot/grub in the terminal...it returns cat: /boot/grub: No such file or directory

...no idea what to do

---

### Post by CCBalla10 on 2007-01-05
Let me go more into detail.  I need to edit my /boot/grub/menu.lst file on my system.  Any way to do this using the Live CD?

---

### Post by CCBalla10 on 2007-01-05
^Bump! sorry i need this fixed...go back to college monday and need it for classes

---

### Post by oswallt on 2007-01-05
I can't help you with the rest, but here's how to mount your file system from the liveCD:

After booting into the liveCD, you need to find out where your linux partition is.  Open a terminal (from the Applications menu, it's under Accessories) and type in:
```
sudo sfdisk -l
```
After you type in your password you should see something like this:
```
   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hdc1          0+  11854   11855-  95225256   83  Linux
/dev/hdc2   *  11855   14404    2550   20482875    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hdc3      14405   14592     188    1510110    5  Extended
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hdc4          0       -       0          0    0  Empty
/dev/hdc5      14405+  14592     188-   1510078+  82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)

```
Find the system called Linux (in my case it's the first line, /dev/hdc1) and mount it with the command:
```
sudo mount /dev/hdc1 /media
```
Of course, substitute /dev/hdc1 for wherever your Linux system is.  After that your system is in the folder: media
Then it's just one more line to edit the file you want:
```
sudo gedit /media/boot/grub/menu.lst
```
Hope that helps.

---

### Post by CCBalla10 on 2007-01-06
^Oswallt

We are getting very close...Thank you for your post, but still have a problem.  Here is my output

ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/hda: 7296 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   1274    1275-  10241406    7  HPFS/NTFS
/dev/hda2       1275    7294    6020   48355650    5  Extended
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5       1275+   7256    5982-  48050383+  83  Linux
/dev/hda6       7257+   7294      38-    305203+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/hda5 media
mount: mount point media does not exist


So it says mount point media doesn't exist...is there a another mount point I can use?  Instead of media

---

### Post by CCBalla10 on 2007-01-06
SOLVED!!!!!!!!!!!!

Thank you Oswallt!!!!!!!!!!!!!!!!!!!!!

What i did was at the point where i mounted...i went to my home folder on my Live CD and created a directory called Media... then i did sudo mount /dev/hda5 ~/Media and BOOM found my filesystem.  Thank you guys so much for your input.  Now i have my comp back for school!!!!

---

