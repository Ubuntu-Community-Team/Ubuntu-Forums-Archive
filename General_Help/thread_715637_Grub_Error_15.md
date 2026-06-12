---
title: "Grub Error 15"
date: 2008-03-05
forum: General Help
---

### Post by redenex on 2008-03-05
Hi guys, I am getting Grub Error 15. I found that if I can check my menu.lst file, there is a possible solution. I am on LIVE CD right now, Can someone help me mount my hard disk?

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    75409109    37704523+  83  Linux
/dev/hda2        75409110    78236549     1413720    5  Extended
/dev/hda5        75409173    78236549     1413688+  82  Linux swap / Solaris


[IMG]http://img147.imageshack.us/img147/5783/screenshotdiskfilebrowstl6.png[/IMG]

---

### Post by lswest on 2008-03-05
first off you have to make a mountpoint for it with ```
sudo mkdir /media/hda1
``` then you can mount it with ```
sudo mount /dev/hda1 /media/hda1
``` which will mount hda1 (the linux drive) into that mount folder, then you can browse to it like you usually do.  Btw, there is a space between "/dev/hda1" and "/media/hda1"

*note* you can name the mountpoint anything you want, i just went with hda1 since that's the devices name

---

### Post by redenex on 2008-03-05
Thank you for a quick reply. Ironically it displays only a folder named LOST and FOUND, I am unable to access anything else on the hda1. Any guidance?

> ubuntu@ubuntu:/media/hda1$ ls -al
total 8
drwxr-xr-x  3 root root 4096 2008-02-29 00:12 .
drwxr-xr-x  4 root root  120 2008-03-05 09:20 ..
drwx------ 19 root root 4096 2008-02-29 00:12 lost+found
ubuntu@ubuntu:/media/hda1$ 


---

### Post by lswest on 2008-03-05
Hmmm, looks to me like your root filesystem is gone, but i could be wrong.  if you open gparted, how much space does it say is being used by the partition, if it's only a few MB, then chances are you're going to have to re-install Ubuntu.  However, if GParted says that there is more space being used on there, then there's something wrong with the way we mounted it.  you could try re-mounting it using this command again ```
sudo mount -t ext3 /dev/hda1 /media/hda1
```  (unmount it first with ```
sudo umount /media/hda1
``` else it won't work) And the difference between that and the last command is that you specify it's an ext3 partition, which might solve any read errors it has.

---

### Post by redenex on 2008-03-06
Here is the GPartedLive results:
> /dev/hda1   ext3   35.96 GB   29.07 GB(used)   6.89 GB(unused)
/dev/hda2   extended   1.35GB
/dev/hda5   linux-swap   1.35GB

Looks hopeful, I assume.




Here is a little background of what really went wrong. I  had to install Ubuntu on my cousin's hard disk. Since he had lot of data that needed to be backed-up, I connected his disk onto my computer, transfered everything. And after installation, I was copying back the back-up data, when the system froze. Once I tried restart, it gave me a Grub Error 2. I ran  e2fsck -C0 -f -v /dev/hda1  I had to fix lot of inodes etc etc, after which it started giving the Grub Error 15.:confused::(:KS

---

### Post by lswest on 2008-03-06
ah, that looks to me like the GRUB was re-written onto the other HDD, meaning you'll have to reinstall grub using either [super grub disk]("http://supergrub.forjamari.linex.org/?section=download") or using a liveCD [see this howto]("http://ubuntuforums.org/showthread.php?t=224351")

and a word of warning, installing Ubuntu on a hard disk in a computer apart from the one it will be installed on is not a good idea, as it will install drivers and set up the configuration for the system it's being installed on, not the computer you want it to be running on later.  Also, if the liveCD doesn't want to boot on a computer, you can always try the alternate CD.  (i assume this is why you installed Ubuntu on his disk from your PC, but if i mis-understood, fell free to correct me)

and secondly, you might want to check the partition for errors from GParted or the Ubuntu LiveCD again, since if there are errors on the disk you will only see the lost + found folders (i believe)

---

### Post by redenex on 2008-03-06
Here is the result from Super Grub Disk.

> select file /grub/stage1 /boot/grub/stage1
Error 15: File Not Found
Booting "NOT" lucky
pause  SGD has NOT succeeded


And no, I did not install on my cousin's hard drive on my computer. I connected that disk onto mine, just to restore back-up data.:popcorn:

---

### Post by redenex on 2008-03-06
> grub> find /boot/grub/stage1

This gives Error:15 File Not Found. :(

---

### Post by lswest on 2008-03-06
do you have the partition mounted while you're running the find command?

---

### Post by redenex on 2008-03-07
I am re-trying everything.


> ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/root
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo grub
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 



Any suggestions?

---

### Post by lswest on 2008-03-07
what do you get if you enter ```
cd /boot/grub/
ls -l
``` in the terminal of the liveCD?

---

### Post by redenex on 2008-03-08
> ubuntu@ubuntu:~$ sudo mkdir /media/hda1
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/hda1
ubuntu@ubuntu:~$ cd /boot/grub/
bash: cd: /boot/grub/: No such file or directory


Not listing /boot/grub/

---

### Post by redenex on 2008-03-08
Another try:

> ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -v /dev/hda1
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
                                                                               
  137791 inodes used (2.92%)
    4325 non-contiguous inodes (3.1%)
         # of inodes with ind/dind/tind blocks: 10402/2821/0
 7620518 blocks used (80.84%)
       1 bad block
       1 large file

  106606 regular files
   12393 directories
    1222 character device files
    4547 block device files
       3 fifos
     405 links
   13010 symbolic links (12417 fast symbolic links)
       1 socket
--------
  138187 files


---

### Post by lswest on 2008-03-08
hmm, what if you try (after mounting it) ```
cd /media/hda1/boot/grub/
ls
```

---

### Post by redenex on 2008-03-08
No luck yet.

> ubuntu@ubuntu:~$ sudo mkdir /media/hda1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /media/hda1
ubuntu@ubuntu:~$ cd /media/hda1/boot/grub/
bash: cd: /media/hda1/boot/grub/: No such file or directory
ubuntu@ubuntu:~$ 


---

### Post by lswest on 2008-03-08
what's the output of ```
cd /media/hda1
ls -la
```

---

### Post by redenex on 2008-03-09
Here it is:

> 
ubuntu@ubuntu:~$ sudo mkdir /media/hda1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /media/hda1
ubuntu@ubuntu:~$ cd /media/hda1
ubuntu@ubuntu:/media/hda1$ ls -la
total 16
drwxr-xr-x  5 root root 4096 2008-03-07 05:46 .
drwxr-xr-x  3 root root   80 2008-03-09 09:02 ..
drwxr-xr-x  2 root root 4096 2008-03-07 05:46 dev
drwx------ 19 root root 4096 2008-02-29 00:12 lost+found
drwxr-xr-x  2 root root 4096 2008-03-07 05:46 proc


---

### Post by redenex on 2008-03-09
An interesting find. I got access to Lost+Found folder. I see lot of stuff listed there, including some of the crucial data I have. I also see the GRUB folder listed which also has the menu.lst.

[IMG]http://img401.imageshack.us/img401/7007/screenshotdt1.png[/IMG]
[IMG]http://img401.imageshack.us/img401/4813/screenshot1el6.png[/IMG]

---

### Post by redenex on 2008-03-09
Hello lswest, thank you for all the time, effort, help and guidance. For now, I believe it is futile from my part to try to make this work. I am so glad that I got back every single file from the lost+found folder. I have copied it all to the new hard drive. I am going to reformat the old one and re-install once more.

Thanks again, have a rocking day! :guitar::KS

---

### Post by lswest on 2008-03-09
No problem, sorry i couldn't fix it for ya, but at least you can keep your files ^^

---

