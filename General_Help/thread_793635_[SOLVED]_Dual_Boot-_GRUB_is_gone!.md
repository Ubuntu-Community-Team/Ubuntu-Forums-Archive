---
title: "[SOLVED] Dual Boot- GRUB is gone!"
date: 2008-05-13
forum: General Help
---

### Post by apple_and _linux on 2008-05-13
I have Ubuntu 7.04 dual-booting with Windows XP SP2.  I just reinstalled Windows (on the same partition) and now I cannot boot into Ubuntu because GRUB does not show up- it just boots automatically into Windows.  How can I fix this?  I can't read the Ubuntu drives from Windows, but I do have the Live CD.  Any help would be greatly appreciated- I really don't want to have to reinstall Feisty.  :(

---

### Post by adult swim on 2008-05-13
you dont need to reinstall ubuntu!  whenever you installed windows it overwrote you mbr with the windows bootloader.  this thread has a walkthrough of how to reinstall grub from your ubuntu live cd [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)

---

### Post by karuptdata on 2008-05-13
You may want to try the following..should get it going for you..

> 1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub "prompt", and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit


Source: [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by apple_and _linux on 2008-05-14
Thanks for your help- but it's not working.  Here is what I get:

```

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub> 


```

Getting kind of worried here...  I tried the mounting stuff which had been edited into the how-to.  Didn't fix it.

---

### Post by CC_machine on 2008-05-14
if nothing works, you could always install a second ubuntu - you would get your old ubuntu as a boot option when you boot.

tried "grub-install"? i honestly dont know what it does, I just remember hearing it. stuck on a school windows machine atm >.>

do "man grub-install" to see what it does ? meh.

---

### Post by jakon on 2008-05-14
Please post the output of
sfdisk -l /dev/sda
!

---

### Post by apple_and _linux on 2008-05-14
Here are the results for the aforementioned command.  I tried sda, but no such directory existed, so I switched it to hda and got this:
ubuntu@ubuntu:~$ sudo sfdisk -l /dev/hda
```

Disk /dev/hda: 39704 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 39704/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   1043    1044-   8385898+   7  HPFS/NTFS
/dev/hda2       1044    2490    1447   11623027+   5  Extended
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda3       2247    2490     244    1959930   82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5       1044+   2245    1202-   9655002   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,2,1)
```

A bit of explanation:
hda1=Windows XP
hda2=Ubuntu Feisty Fawn
hda3=Swap drive (obviously)
hda4 and hda5=I have no idea.  I have three more partitions on separate physical disk, but they didn't seem to show up here.
Oh, and I tried sudo grub-install and it gave me the help screen... :/ which wasn't much help because I don't know which disk is what, nor what the commands mean.

---

### Post by OzzyFrank on 2008-05-14
OK, while there is no reason this can't be sorted out, I am a bit confused as to some of the drive references. OK, GRUB tells you it found itself on **[COLOR="Blue"](hd0,5)[/COLOR]** and sfdisk reported there is a Linux partition at **[COLOR="Indigo"]/dev/hda5[/COLOR]**. Besides the fact you say your Ubuntu partition is the 2nd one, **[COLOR="Blue"](hd0,5)[/COLOR]** and **[COLOR="#4b0082"]/dev/hda5[/COLOR]** are not the same thing at all, even though they look it. If you notice the GRUB way of looking at things, **[COLOR="Indigo"]hda[/COLOR]** does not become **[COLOR="Blue"]hd1[/COLOR]**, but **[COLOR="#0000ff"]hd0[/COLOR]**... and instead of the first partition on any drive being **1**, it is **zero**... so [COLOR="Indigo"]**hda5**[/COLOR] should in GRUBspeak be **[COLOR="Blue"]hd0,4[/COLOR]** (as opposed to what most would expect to be **[COLOR="#0000ff"]hd1,5[/COLOR]**).

So maybe try:

grub> **[COLOR="#0000ff"]root (hd0,4)[/COLOR]**
grub> **[COLOR="#0000ff"]setup (hd0)[/COLOR]**

or if you are sure the Ubuntu partition is the second one:

grub> [COLOR="#0000ff"]**root (hd0,1)**[/COLOR]
grub> **[COLOR="#0000ff"]setup (hd0)[/COLOR]**

Hope this helps!

---

### Post by OzzyFrank on 2008-05-14
PS: This will **always** happen when you reinstall Windows... it has no concept of other operating systems and their bootloaders. It's up to you to decide whether Windows is just incredibly stupid next to Linux distros like Ubuntu, or just extremely arrogant, like the company that makes it (hehe). Once you get GRUB going again, write down these steps in an exercise book or something for later use, in case Windows needs reinstallation again.

Oh, and yes, while you can access Windows drives from Ubuntu, Windows won't even know your Ubuntu partition exists. You can search for and use **[COLOR="DarkRed"]Explore2fs[/COLOR]** (it's a standalone .exe you don't need to install, just run). It won't give you the same access as Ubuntu gives you to your Windows drive, but with it you can explore the partition and any files you need to access you save to your Windows drive and open from there (useless for trying to edit/fix anything on your Ubuntu partition, but good for grabbing things like files you downloaded while in Ubuntu).

---

