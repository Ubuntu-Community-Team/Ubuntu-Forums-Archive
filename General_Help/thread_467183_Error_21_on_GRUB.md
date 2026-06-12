---
title: "Error 21 on GRUB"
date: 2007-06-07
forum: General Help
---

### Post by Vargas on 2007-06-07
[SIZE="2"]Hey everyone.
This is my first post and already I need some help. :oops:
Right now, I have my home PC partitioned in two; Windows Vista Ultimate and Ubuntu 7.
Two Days ago, I reimaged my work PC.
I brought my HDD to work to backup some stuff; I connected it here with a USB-to-IDE cable and everything worked fine.
When I went back home, I connected everything back but I got this when I boot:

[B]Grub Loading Stage 1.5
Grub Loading please wait....
Error 21[/B]

And then, nothing... 	](*,)
Any ideas?
I know the MBR must be busted but I don't know how to fix it from the Ubuntu7 LiveCD
At this point; I cannot even get into Windows...

Thanks to all in advance.[/SIZE]

---

### Post by confused57 on 2007-06-07
Here's how to install grub, using the live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Mounting your root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If reinstalling grub doesn't work, you might want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and after mounting your root partition(see the guide for the exact entry you need to use):
```
gedit /boot/grub/menu.lst
```

---

### Post by ajgreeny on 2007-06-07
Found all this quite easily.

Error 21 : Selected disk does not exist. This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 
 Google on: grub error 21
 See: 

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)
 [http://www.mepis.org/node/5782](http://www.mepis.org/node/5782)
 [http://www.linuxquestions.org/questions/showthread.php?threadid=338856](http://www.linuxquestions.org/questions/showthread.php?threadid=338856)



I wonder if this is something to do with the sda/hda problem that was around for some time a while back, but which I thought had been sorted.



To reinstall grub with the live CD follow this:-



Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.  If it still ends up at the same error 21, then you may need to edit the /boot/grub/menu.lst file using the live CD to take account of the incorrect nomenclature of the partition on which the various OSs are installed.  From the live CD try **sudo fdisk -l** to find out where everything really is.




Good luck, I hope it all works again.

---

### Post by Vargas on 2007-06-08
> **confused57 said:**
> Here's how to install grub, using the live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Mounting your root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If reinstalling grub doesn't work, you might want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and after mounting your root partition(see the guide for the exact entry you need to use):
```
gedit /boot/grub/menu.lst
```

Thanks for all the advice. So here's what happened:

Someone gave me this link: (Essentially the same on the other links)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And step by step:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.
- DONE

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

Here's what came up:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   165421304    82710621    7  HPFS/NTFS
/dev/hda2       165421305   165630149      104422+  83  Linux
/dev/hda3       165630150   390716864   112543357+  8e  Linux LVM
```

3. Type "grub" which makes a GRUB prompt appear.
DONE

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.
```

grub> find /boot/grub/stage1

Error 15: File not found
```


5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit". 


So nothing...
And in case you're thinking my C:\ drive is not being recognized by the BIOS... it is... I can even mount it when on the Live CD...
Any thoughts?

---

### Post by confused57 on 2007-06-08
If you have access to another pc, you might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Here's a description & possible solutions to grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

You might want to mount your Ubuntu root partition from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda2 /media/ubuntu
```

then post the output of:
```
gedit /media/ubuntu/boot/grub/menu.lst
```

Did you happen to change the jumper settings on the hard drive when you installed in the USB case?

---

### Post by Vargas on 2007-06-11
Well, this is embarrassing... :oops:

Here's what happened:

I have two HDD's: 1 IDE (where Vista and Ubuntu are)
and one SATA (for music/video storage, nothing else)

After battling until 1AM I saw that the SATA drive's power cable was disconnected.
I plugged it in and... yes; everything worked again!!

PLEASE CALL ME NEWBIE, ROOKIE or anything of the sort...
But the truth is that I AM a rookie in the matters of Linux
I guess it's because of things like this that we TRULY learn, huh?

Still, thanks for all the help guys!! I REALLY appreciate it.

---

### Post by deadlikeoscar on 2007-06-11
There's nothing wrong with being a newbie as long as you have a good attitude and are willing to learn.;) Glad you got it sorted out.

---

