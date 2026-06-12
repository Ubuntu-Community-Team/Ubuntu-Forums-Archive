---
title: "Ubuntu 7.10 boot help (complete noob!)"
date: 2008-03-12
forum: General Help
---

### Post by marados on 2008-03-12
Ok, so, here's my story:

I was using Windows XP for around five years before it finally died on me. It was a faulty driver I think - I couldn't boot it up, Even with the windows CD, I couldn't get to recovery console - it'd crash prior to that.

So I got my hands on an Ubuntu boot disk, and booted up from there - I then decided to install Ubuntu (and I've decided that when I've got my computer up and running properly, I'll have a dual boot system of Ubuntu and XP I like it so much ^_^; ).

So the whole idea of a package manager was new to me. I first started looking for a few codecs and a swf player, and found what I was looking for (I downloaded Gnash). I was then told that it was advised that I should download some updates, so I decided to do so. The file was quite big, so I decided that I'd go and watch some TV and whatnot in the meantime. When I came back at around the time I thought the package had downloaded, I came to my computer rebooting. This sort of panicked me a bit, but I decided that the updates had downloaded and the system automatically rebooted to install them, or something to that extent. When the system booted up, I was prompted to input my username and password as normal, and I did so. However, the computer at that stage hung in a limbo - that beige screen where I can see the mouse, but the desktop hasn't loaded. I decided that it was simply taking a bit longer to boot up because of the new software.

I waited it out, and came back in half an hour to find that it was still in limbo. I then rationalised that if hadn't booted up yet, it wasn't going to any time soon. I decided to reboot the PC, and when it got to GRUB, I was presented with the error message:

Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Or something to that extent. I've searched around, and have found some info on the problem, but it simply doesn't make any sense to me.

Would anybody be able to help me fix the problem, while keeping in mind I'm green in the absolute sense? I'm typing from the live-CD boot.

Thanks in advance.

---

### Post by phiphedog on 2008-03-12
Can you post your /etc/fstab file and your /boot/grub/menu.list file so we can see what's going on.

---

### Post by kesman on 2008-03-12
Can you access your existing files trough the liveCD? If you can, browse yourself to /boot/grub and check if there's a backup of menu.lst -file from time BEFORE the updates you made.
I think that some update has altered your original menu.lst, and is now forcing the grub boot loader to load the linux kernel from wrong place(block 0,0) I think. If the backup exists, check the working path to the kernel from there, and edit the current menu.lst -file to corresponding values. If there's no backup, let me know, there gotta be a solution to this :)

---

### Post by marados on 2008-03-12
Ok, the menu.lst file reads:

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a69f5320-e092-492e-abac-3fd8554d80c0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a69f5320-e092-492e-abac-3fd8554d80c0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


I don't think there's a backup (or one that I can see)

And the /etc/fstab is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a69f5320-e092-492e-abac-3fd8554d80c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f5d78306-1e75-4f8a-9559-457daebd4b3a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by phiphedog on 2008-03-12
If Ubuntu is installed on the first partition of the disk then this looks ok and it is possible the install is corrupted.

Firstly check if the partition is bootable. You can do this by loading qtparted and setting the root partition to active. Reboot and test.

```
sudo apt-get install qtparted
```

```
sudo qtparted
```

If this is not the first partition then, like kesman suggested, you need to change the (hd0,0) in you /boot/grub/menu.list.  Try (hd0,1). Reboot and test.

---

### Post by kesman on 2008-03-12
Try changing the root (hd0,0) to root (hd0,1) instead. This may help.

---

### Post by marados on 2008-03-12
Thanks for the advice, I'll give both solutions a try.

If I was to change root(0,0) to root(0,1), would I replace all instances of root(0,0) with it? Or just a specific part?

---

### Post by phiphedog on 2008-03-12
all instances. there should be 3

here's mine

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b13a299f-5931-456e-a02a-dddb9be9b603 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b13a299f-5931-456e-a02a-dddb9be9b603 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

---

### Post by marados on 2008-03-12
Ok, thanks. I'll give that a whirl in a bit and get back to you guys.

---

### Post by marados on 2008-03-12
I tried both methods, but I'm having trouble with them:

I first tried the qpartition, as phiphedog suggested - this seemed to work (and the partition was active) but in the terminal, I got the message:

```
Error: The file system was not cleanly unmounted! You should run e2fsk.
 Modifying an unclean file system could cause severe corruption.
```

So yeah, that doesn't seem to bode too well =\

I also tried to change the root (hd0,0) to (hd0,1), but was presented with:

```
Could not save the file /media/disk/boot/grub/menu.lst.
You do not have the permissions necessary to save the file.
 Please check that you typed the location correctly and try again.
```

In the text editor. 

I'm at a loss here. Any more advice? Thanks for your help so far, guys.

---

### Post by kesman on 2008-03-12
I thought that the liveCD user was superior when editing the files. Well, try with
```

sudo nano /media/disk/boot/grub/menu.lst

```
maybe this allows you to do it

---

### Post by marados on 2008-03-12
That seems to have done the trick! 

Now it's time to put the boot to the test.

---

### Post by marados on 2008-03-12
It didn't fix the problem, sadly. =( 

It said that it couldn't find the boot partition when I changed it to 0,1, and I was told to press any key. Pressing a key got me to a drop down menu with three selections (kernel, kernel recovery mode, and memtest), but none of these worked when I selected them and hit enter - it couldn't find it, and I was directed to the menu again.

Any advice? Think I should try and do a "e2fsck"?

---

### Post by phiphedog on 2008-03-13
If it's a fresh install then I wouldn't muck around. I'd just reinstall Ubuntu.

if not...

load up the Live CD and post the output of this command so we can have a look at the disks in your system

```
sudo fdisk -lu
```

---

### Post by phiphedog on 2008-03-13
or you could try re-configuring GRUB with these instructions if you have a single boot system. If you dual boot, then post the results of     **sudo fdisk -lu**   as requested in my last post and well take it from there.

Allright, let's configure GRUB.

Boot from the live cd and open a command prompt

Type in the following comands
```

sudo umount /dev/sda1
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
 
```

These steps should have mounted your hard disk so GRUB can recognise it.

Now we'll load up GRUB and set it up to boot from the correct partition

```

sudo grub
find /boot/grub/stage1
(The above command will list the partitions that it finds the GRUB files on. It'll give you 
something like (hd0,1). Whatever numbers it gives you here you will add in the next command)

root (hd0,1)
setup (hd0)
quit

```

Reboot and test.

---

