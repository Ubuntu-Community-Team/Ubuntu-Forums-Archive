---
title: "I can't restore GRUB!"
date: 2008-02-12
forum: General Help
---

### Post by Repgahroll on 2008-02-12
Hello guys!

I was trying to setup grub in a floppy to install a multiboot in another HD for a friend.

I installed it in a floppy, and everything was OK, but when i was going to modify the device.map on floppy, i'd modified the one in my HD... i know that it was a giant error, but i thought that should be easy to undo.

My GRUB was the default one:

I have only one partition and the swap, so everything was on hd0,0.


When i try to run grub from the LiveCD, it always return a error...

After did the chroot to the system on HD, if i run **grub**, then **find /boot/grub/stage1** it returns an error (could not found), if i run **root (hd0,0)** nothing returns, and if i run **setup )hd0)** it returns the error 17(i guess, don't know exactly, tomorrow i'll edit this post including the exact error values). 
Alternatively, if i try to run the **grub-install** script, no matter what parameter i use, it always return an error.

Tomorrow i'll list the errors numbers exactly if i the problem still not solved.



[COLOR="Blue"][SIZE="4"]The following isn't important, so dont need to read, i think:[/SIZE]

My friend want to have a multiboot system on the same HD; basically:

DOS 6.22
Windows98
WindowsXP
Damn Small Linux

So, i said he that it should be possible using the GRUB from the Linux installation. Then i take the hardware to try to do it.

First of all, i parted the disc using Gparted LiveCD into 5 partitions:

1-Fat16  -prim.
2-Fat32  -prim.
3-Fat32  -prim.
--4-Ext2
   '-5-Linux-swap

After it, i installed the DOS 6.22, on the first partition without formatting.
Everything was working (just DOS)

Then i tried to install the Windows98, but when it reboot to continue the installation, the boot wasn't working anymore.

The same thing happens if instead of Windows98, i try to install XP after DOS.

So, i had the IDEA! of running GRUB from a floppy, to try to boot the half-installed systems:

Basically:

I will install XP first, and when it stop the installation to reboot, i'try to boot the partition using GRUB.
Then, i'll try to install 98 using the same mehtod, and then i'll try to install DOS hiding the other partitions using the GRUB parameters. And finally, i'll install DSL, and copy the menu.lst from floppy to the installed GRUB.

Microsoft Support said that was just installing the systems on the order from old to new, but don't work... if i install any windows on non-first partition, it wouldnt boot again after the reboot :(...[/COLOR]

Thank you all very very much!:D and sorry my very bad english:(

---

### Post by pieisgood4589 on 2008-02-12
No, you're english is fine!  :)

Try this guide step-by-step [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

Worked for me :lolflag:

---

### Post by Repgahroll on 2008-02-12
Oh man, thank you very much for reading my post, but i already did these steps, and the grub couldnt find the stage1.

Is my english really fine? =/

Thanks!

---

### Post by Repgahroll on 2008-02-13
OK... i'll post some outputs:

**From DSL-N LiveCD**(/dev/hda1 mounted at /mnt/1, and chrootted into /mnt/1):

**grub-install --root-directory=/mnt/1 hd0**
returns: [COLOR="Red"]/mnt/1/boot/grub/stage1 not read correctly[/COLOR]

**(grub)grub>root (hd0,0)**
[COLOR="Red"]Error 21:selected disk does not exist[/COLOR]
the same command **without chroot**, returns "[COLOR="Red"]Filesystem type unknown[/COLOR]".

**From Ubuntu 7.10 LiveCD:**

**ubuntu@ubuntu:/mnt/1$ grub-install --root-directory=/mnt/1 hd0**
[COLOR="Red"]/dev/sda1 does not have any corresponding BIOS drive.[/COLOR]
(of course i'd mounted /dev/sda instead of hda as in DSL-N)
[B]
(grub)grub> root (hd0,0)[/B]

**grub> setup (hd0) **

[COLOR="Red"]Error 17: Cannot mount selected partition[/COLOR]


my **menu.lst **(/mnt/1/boot/grub/menu.lst)

```
default		0
timeout		30

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=facc0102-da89-4e4f-bdbd-6e60484cccee ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=facc0102-da89-4e4f-bdbd-6e60484cccee ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

my **device.map**

```
(hd0)	/dev/sda
```

Thanks

---

### Post by housam on 2008-02-13
Read [[COLOR="Red"]this guide [/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")it may help

---

### Post by Repgahroll on 2008-02-13
Automatically:
```

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /mnt/work 
root@ubuntu:~# mkdir /mnt/work/boot 
root@ubuntu:~# mount /dev/hda1 /mnt/work 
mount: special device /dev/hda1 does not exist
root@ubuntu:~# mount /dev/sda1 /mnt/work 
root@ubuntu:~# mount -o bind /dev /mnt/work/dev
root@ubuntu:~# mount -o bind /proc /mnt/work/proc
root@ubuntu:~# cp /proc/mounts /mnt/work/etc/mtab
root@ubuntu:~# chroot /mnt/work/ /bin/bash 
root@ubuntu:/# sudo /sbin/grub-install /dev/sda
You shouldn't call /sbin/grub-install. Please call /usr/sbin/grub-install instead!

Could not find device for /boot: Not found or not a block device.
root@ubuntu:/# sudo /usr/sbin/grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
[COLOR="Red"]The file /boot/grub/stage1 not read correctly.[/COLOR]
root@ubuntu:/# sudo mount /dev/sda1 /boot/
root@ubuntu:/# sudo /sbin/grub-install /dev/sda
You shouldn't call /sbin/grub-install. Please call /usr/sbin/grub-install instead!

Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
[COLOR="Red"]The file /boot/grub/stage1 not read correctly.[/COLOR]
```

Manually:

```

root@ubuntu:/# sudo /sbin/grub 
sudo: /sbin/grub: command not found
root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time.


grub> root (hd0,0)

grub> setup (hd0)

[COLOR="Red"]Error 17: Cannot mount selected partition[/COLOR]

grub> 

```


Thank you very much, but, as you could see, this way didn't work.
And now when i try to boot from HD, the GRUB displays the Error 17 before printing the menu on screen.(before it the error was printed after accessing a menu entry)

Thanks

---

### Post by housam on 2008-02-13
Try to use the [[COLOR="Red"]superGrub tool[/COLOR]]("http://supergrub.forjamari.linex.org/")

---

### Post by Repgahroll on 2008-02-13
:cry::cry::cry::cry:

dont work :cry:

i dont belive!... will i have to reinstall the whole system? I came to Linux world hoping that i would never again need to do such thing.

After some time trying to fix the problem using the supergrub cd, my system became totally mixed... now there's a /grub folder, and also all the /* folders now have a copy in /boot/grub:

Theres a:

/grub
/boot/grub/usr
/boot/grub/etc
/boot/grub/bin
....
and also a
/boot/grub/boot/grub

:(
Thanks

---

### Post by adrian15 on 2008-02-13
> **Repgahroll said:**
> Hello guys!

I was trying to setup grub in a floppy to install a multiboot in another HD for a friend.

I installed it in a floppy, and everything was OK, but when i was going to modify the device.map on floppy, i'd modified the one in my HD...


Device.map in the floppy is not useful. It does not read by grub.

Editing device.map inside your system should not cause you any problem unless there is a kernel update and then update-grub is run (update-grub runs device.map).
> **Repgahroll said:**
> 
After did the chroot to the system on HD, if i run **grub**, then **find /boot/grub/stage1** it returns an error (could not found),

Did you mounted with the bind option the /tmp, /dev and /sys folders before chrooting?

> **Repgahroll said:**
> 

[COLOR="Blue"]The following isn't important, so dont need to read, i think:

My friend want to have a multiboot system on the same HD; basically:

DOS 6.22
Windows98
WindowsXP
Damn Small Linux

[/COLOR]

You should use Super Grub Disk to hide both Windows98 and WindowsXP partitions before installing DOS 6.22.

You should use Super Grub Disk to hide both DOS 6.22 and Windows XP partitions before installing Windows98.

And idem for Windows XP.

Once you have installed the SOs being hidden one from another you can boot them with grub thanks to the hide and unhide commands that you will have to write into the menu.lst 
DOS/WINDOWS entries.

If you don't get to write the exact commands ask for more help I will write a menu.lst for your grub floppy.

> **Repgahroll said:**
> 
[COLOR="Blue"]

Microsoft Support said that was just installing the systems on the order from old to new, but don't work... if i install any windows on non-first partition, it wouldnt boot again after the reboot :(...[/COLOR]


With Microsoft default behaviour you always depend on data in the MSDOS partition to boot all the OSs which it is nonsense.

If you make each OS to think there is no other OS in the machine then you are happy.

adrian15

---

### Post by adrian15 on 2008-02-13
> **Repgahroll said:**
> :cry::cry::cry::cry:
dont work :cry:
i dont belive!... will i have to reinstall the whole system? I came to Linux world hoping that i would never again need to do such thing.

You can nearly always fix a Linux system without rebooting it but you should know how to do it. ;).
> **Repgahroll said:**
> 
After some time trying to fix the problem using the supergrub cd, my system became totally mixed... now there's a /grub folder, and also all the /* folders now have a copy in /boot/grub:

Theres a:

/grub
/boot/grub/usr
/boot/grub/etc
/boot/grub/bin
....
and also a
/boot/grub/boot/grub


Super Grub disk is not smart enough for changing folders or the fstab file so it is not Super Grub Disk fault. It seems to me that you mounted your / system from a live to /boot/grub or that you did a copy of the root system into /boot/grub or I actually do not know.

Do you still see that /boot/grub/etc,.. folders when rebooting your machine ?
Did you edited fstab perhaps?

Some questions:

1) Super Grub Disk -> Super Grub Disk (With help) -> Linux -> Fix Boot of Linux 
Does it fix your problem?

2) Super Grub Disk -> Super Grub Disk (With help) -> Linux -> Boot Linux -> Does it boot your system?

3) What were the commands that you issued to build your grub floppy disk? (I actually do not understand what you have done to loose your boot. Usually editing device.map should not give any problem unless an update-grub command is run).

adrian15

---

