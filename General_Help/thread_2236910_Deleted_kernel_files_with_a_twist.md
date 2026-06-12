---
title: "Deleted kernel files with a twist"
date: 2014-07-29
forum: General Help
---

### Post by skav2407 on 2014-07-29
I have done a bit of research and I haven't come across a deleted kernel problem like mine.  I have a separate boot partition (sda1).  Ubuntu is installed on a separate partition and that is causing me some trouble. The partition that ubuntu is on is also encrypted.   I have been trying to fix things by booting up a livecd.

i tried this

sudo -s
mount /dev/sda1 /mnt/boot
mount /dev/mapper/ubuntu--vg-root /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt

From there I have tried a few different things:

Apt-get install linux-image-generic

and

Update-initramfs -u-k 3.13.0-30-generic

and update-grub2

Nothing I've done has worked.  I downloaded the linux boot repair disk but that didn't work either.  I even tried supergrubdisk2 without any luck. I'm not a pro buy any means with the command line so any help is appreciated.  Thanks.

---

### Post by skav2407 on 2014-07-30
I should also note that when I get to the desktop on the liveCD I can see the encrypted drive.  When I click on it it asked me for the decryption password and when I enter it I am able to see everything in the drive.  I can also see the boot drive in the file manager.  I played around with it more this morning and I no longer get a complete failure to boot up.  Ubuntu looks like it is loading the kernel but them it says it cannot find the boot drive.  It drops me down to a prompt but everything is frozen and I can't type anything in.  Any ideas?

Thanks.

---

### Post by skav2407 on 2014-07-30
I think I have the deletd kernel problem fixed the problem is my system won't boot up now.  It starts up, I get to grub and select the kernel.  I see "Ubuntu" and the 4 dots moving and then about 3-4 minutes later is drops out to a busybox message and the prompt says "initramfs".  There is a blinking cursor like you can type something but nothing works.

I ran the Linux boot-repair disk.  That didn't change anything. The output is here.  [http://paste.ubuntu.com/7904895/](http://paste.ubuntu.com/7904895/)

At the very bottom I see this:

fsck: fsck.crypto_LUKS: not found
fsck: error 2 while executing fsck.crypto_LUKS for /dev/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 -> Error code 32

Boot successfully repaired.

You can now reboot your computer.

I'm guessing that is my problem?

---

### Post by skav2407 on 2014-07-30
I think the problem is with update-initramfs  I get the following:

root@ubuntu:/# update-initramfs -u -k 3.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
depmod: WARNING: could not open /tmp/mkinitramfs_SAtRkJ/lib/modules/3.13.0-32-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_SAtRkJ/lib/modules/3.13.0-32-generic/modules.builtin: No such file or directory

Any ideas?

---

### Post by Impavidus on 2014-07-30
> **skav2407 said:**
> I have done a bit of research and I haven't come across a deleted kernel problem like mine.  I have a separate boot partition (sda1).  Ubuntu is installed on a separate partition and that is causing me some trouble. The partition that ubuntu is on is also encrypted.   I have been trying to fix things by booting up a livecd.

i tried this

sudo -s
[B]mount /dev/sda1 /mnt/boot
mount /dev/mapper/ubuntu--vg-root /mnt[/B]
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt

From there I have tried a few different things:

**apt-get install linux-image-generic**

and

Update-initramfs -u-k 3.13.0-30-generic

and update-grub2

Nothing I've done has worked.  I downloaded the linux boot repair disk but that didn't work either.  I even tried supergrubdisk2 without any luck. I'm not a pro buy any means with the command line so any help is appreciated.  Thanks.

If you deleted the kernel, this is the right track to solve it. However, the first two lines I highlighted should be swapped. In your version, first the boot partition is mounted at /mnt/boot, and then the root partition is mounted at /mnt, hiding the real boot partition and presenting its own, unused, boot directory. Or you just swapped them in your post and did it right, I can't tell.

The last line I highlighted instructs apt-get to install linux-image-generic. This doesn't do anything as it is already registered as installed. Furthermore, it's a metapackage. The real kernel is in linux-image-<some version>. So the right command to use there is```
apt-get --reinstall install linux-image-<some version>
```For example, if you are on 14.04 on a default install, use```
apt-get --reinstall install linux-image-3.13.0-32-generic
```

---

### Post by skav2407 on 2014-07-30
Thank You Impavidus!  I did figure out that those were swapped, I'm sorry I didn't update that sooner.  I do think that I have the kernel installed now but I'm just having a problem getting it to read the encrypted drive.  In post 4 I can't seem to get initramfs past those errors to recognize the drive at startup.  I've done a lot of research and I've seen some similiar problems and I think I'm on the right path but I just can't get past those errors.  Thank you so much for your help though!

---

### Post by paulbussmann on 2014-09-02
I also faced issues with modules.order .

My steps where:
1. Freshly install Ubuntu 14.04.1 LTS amd_x64
2. Install packages samba, ssh, g++, eclipse-cdt
3. Copied 3rd-party Kernel module sources to the host (they did fine for older Ubuntu installations)
4. Compiling the module is fine, but make modules_install fails! At Terminal:

paul@PBN-1-Ubuntu:~/my_module_sources$ sudo make modules_install
make -C /lib/modules/3.13.0-32-generic/build M= modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
cp: cannot stat â/usr/src/linux-headers-3.13.0-32-generic/modules.orderâ: No such file or directory
make[1]: *** [_modinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [modules_install] Error 2

Seems Ubuntu 14.04.1 LTS amd_x64 default installation of /usr/src/linux-headers-3.13.0-32-generic is incomplete.

Looks odd, because modules.order is available in another folder "/lib/modules/3.13.0-32-generic/".
After copying everything that was claimed to to be missing (modules.order, modules.builtin, firmware, ...) from "/lib/modules/3.13.0-32-generic/" to "/usr/src/linux-headers-3.13.0-32-generic/", "make modules_install" did not return any error, but "modprobe <module-name>" still fails. 
What are the needed steps to fix this packaging bug from Ubuntu 14.04.1 LTS without screwing up the system?

---

