---
title: "[Lubuntu 14.04] Can't boot after latest updates"
date: 2014-11-25
forum: General Help
---

### Post by jim1944 on 2014-11-25
After having software updater install the latest updates, I closed all windows, and allowed software updater to restart. On restart all I got was a "grub>" command prompt. When I typed "exit" I got "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

I can run the Lubuntu 14.04 CD and see, via gparted, that the Lubuntu partition (ext4) is there. I performed a check on the partition and it showed no errors. I mounted the partition and poked around and everythying seems to be OK. I can access my home directory and there is a /boot dierctory and the partition is marked "boot" in gparted.

There is no other operating system installed on the machine. I installed Lubuntu recently but have gone through a couple of software update cycles without incident.

Grub has never presented a boot menu when I boot up. It simply boots into Lubuntu. I would have expected it to present a menu containing the older kernels.

The current content of /boot is:
```
lubuntu@lubuntu:/media/lubuntu/cb100808-f296-4250-863f-65adf9e8572c/boot$ ls -l
total 84316
-rw-r--r-- 1 root root  1166929 Jul 15 05:06 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  1168764 Oct 28 14:43 abi-3.13.0-39-generic
-rw-r--r-- 1 root root  1168726 Nov 13 19:03 abi-3.13.0-40-generic
-rw-r--r-- 1 root root   169732 Jul 15 05:06 config-3.13.0-32-generic
-rw-r--r-- 1 root root   169782 Oct 28 14:43 config-3.13.0-39-generic
-rw-r--r-- 1 root root   169815 Nov 13 19:03 config-3.13.0-40-generic
drwxr-xr-x 5 root root     4096 Nov 25 01:51 grub
-rw-r--r-- 1 root root 18715080 Nov 20 20:36 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 18734121 Nov 20 21:18 initrd.img-3.13.0-39-generic
-rw-r--r-- 1 root root 18732730 Nov 25 01:51 initrd.img-3.13.0-40-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  2693057 Jul 15 05:06 System.map-3.13.0-32-generic
-rw------- 1 root root  2697539 Oct 28 14:43 System.map-3.13.0-39-generic
-rw------- 1 root root  2697648 Nov 13 19:03 System.map-3.13.0-40-generic
-rw-r--r-- 1 root root  5820336 Jul 22 23:09 vmlinuz-3.13.0-32-generic
-rw------- 1 root root  5828720 Oct 28 14:43 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  5830128 Nov 13 19:03 vmlinuz-3.13.0-40-generic
lubuntu@lubuntu:/media/lubuntu/cb100808-f296-4250-863f-65adf9e8572c/boot$ 
```

Based on this I would expect a boot menu allowing me to boot 3.13.0.32/39/40 but what do I know?

Any ideas how to fix things?

Thanks
Jim

---

### Post by slickymaster on 2014-11-25
It could be simply a failure of the GRUB 2 bootloader. You could try [reinstalling it]("https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System").

---

### Post by jim1944 on 2014-11-25
After a little futzing (technical term) around, this is what worked: In a terminal window from the live CD:
```
lubuntu@lubuntu:~$ sudo mount /dev/sda1 /mnt
lubuntu@lubuntu:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
lubuntu@lubuntu:~$ sudo chroot /mnt
root@lubuntu:/# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
root@lubuntu:/# update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@lubuntu:/#
```

The "update-grub" step was necessary.

Thanks stickymaster for your help.

JIm

---

### Post by yancek on 2014-11-25
I would think that update-grub would be run after a new kernel is installed but apparently not.  I'd watch the next time you do an update and if you get a new kernel watch to see if update-grub is run and run it manually if not.  I have other Linux systems which remove earlier kernels but from what I have see here this is not the case with Ubuntu as I've seen posts with users having 20+ kernels.

---

### Post by slickymaster on 2014-11-25
> **jim1944 said:**
> <---snip-->

Thanks stickymaster for your help.

JIm

You're welcome. Glad you got it fixed.

---

### Post by vasa1 on 2014-11-25
> **yancek said:**
> I would think that update-grub would be run after a new kernel is installed but apparently not.  I'd watch the next time you do an update and if you get a new kernel watch to see if update-grub is run and run it manually if not. ...
@yancek, [here is some old output]("http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988") from when an new kernel was being installed. No explicit update-grub. I think it's pretty much the same even now. And **sudo apt-get autoremove** offers to remove most older kernels for me.

---

