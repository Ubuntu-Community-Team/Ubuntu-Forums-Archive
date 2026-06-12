---
title: "NTFS mount problems"
date: 2008-03-13
forum: General Help
---

### Post by IainAdams on 2008-03-13
I am trying to help a friend gain access to his harddrive after windows failed load. I am trying to use the Live CD to mount the windows drive and copy all the required information onto an external HD.

At first I used my feisty CD. I inserted it and it loaded fine. I was able to mount windows and my external HD and read from it. However was unable to copy to my external HD. This is because it is NTFS format and feisty does not support it.

So, I decided to try the gutsy Live CD, however now I am getting opposite problems. My external HD mounts fine and I am able to create folders etc on it. However the windows drive fails to mount complaining 

ntfs_attr_pread : ntfs_pread failed: Input/Output error
failed to read NTFS $Bitmap: Input/Output error

Now this could be because the hard drive is damaged but somehow it managed to mount in feisty and I could read files. Does anybody know a way that I can access the data from the Live CD and copy it to my external HD.

Thanks alot

Iain Adams

---

### Post by taurus on 2008-03-13
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

Or have you tried booting his machine with Fiesty LiveCD and see if you can still mount that windows partition?

---

### Post by Kaisshau on 2008-03-15
I have the same problem... My NTFS drive is not working as well, and the output from the terminal is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb25e438f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1147     9213246   27  Unknown
/dev/sda2   *        1148        7889    54155115    6  FAT16
/dev/sda3            7890       14593    53849880    7  HPFS/NTFS


Please help me.

---

### Post by mikewhatever on 2008-03-15
Taurus must have had something in mind, but technically, Ubuntu Live CD is not a data recovery tool. Use photorec or testdisk instead.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Kaisshau on 2008-03-15
How do you get testdisk to work? I tried running it and this is what I get:

ubuntu@ubuntu:~$ testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
You will have to enable component called 'universe'
bash: testdisk: command not found
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ 

Please help me.

---

### Post by froy02 on 2008-03-15
Install testdisk using synaptics package manager.  
Open synaptics, go to Settings ->Repositoties ->Ubuntu software then put a check mark on Community maintain Open Source software (universe).  Then find 'testdisk and install it from synaptics.

---

### Post by louieb on 2008-03-15
My two favorite Live CD's for copying from a hard drive to an external drive doing just that.
[Puppy Linux]("http://www.puppylinux.com/") small download , runs fast
[Knoppix Linux]("http://www.knoppix.net/")  600+MB download, lots of tools.

TestDisk is also on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by Kaisshau on 2008-03-15
Ran Testdisk, and I still get the same error. Although, in Testdisk, I was able to marginally access my HD, but I couldn't copy or go past the first level (C:\).

Please Help Me.

---

