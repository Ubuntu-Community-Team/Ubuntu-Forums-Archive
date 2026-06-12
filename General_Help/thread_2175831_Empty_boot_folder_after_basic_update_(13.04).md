---
title: "Empty boot folder after basic update (13.04)"
date: 2013-09-21
forum: General Help
---

### Post by MasterRolfe on 2013-09-21
I'm running Ubuntu 13.04.  I let Sotware Updater do it's thing last night, and when I woke up this morning, it told me that the boot folder was full, and couldn't finish something.  I pressed OK, and nothing else happened.  I decided to check it out later and shut down.

When I restarted, all I got was a blank screen.  After a forced restart, it now asks me if I want to boot Ubuntu, Ubuntu (Advanced Options) or the System Settings of the laptop.  Both the Ubuntu options land me at a screen with some text at the top saying it's launching, but it goes no further.

I still have the Flash Drive I used to install Ubuntu (I only installed a month or two ago), so I used that to boot into the "Try Ubuntu" feature. Remembering the error about the boot folder, I went to look at it and found it not full (like the error said), but now completely empty (My file browser was set to show hiden files, so there weren't any of those either).

I tried to copy the contents of the bootable flash's boot folder into the empty boot folder (thought it was worth a shot).  No dice.  I tried to used Boot Repair.   Still no luck.

Does anyone know how I might fix my empty boot folder?  It now has the same contents as the flash drive's boot folder.  If I'm going to have to reinstall Ubuntu, is there any way I can copy my Home folder to a flash before?  I tried but it wouldn't even let me see the contents, let alone copy them.

---

### Post by Impavidus on 2013-09-21
You have a separate boot partition. When normally booting this boot partition is mounted at /boot. When booting from a live usb it's not automatically mounted. You mounted the root partition of your installed system using the live usb, but not the boot partition, so the /boot directory appeared empty.

You can delete the files you copied to the /boot directory using your live usb and mount the boot partition. Show us what's in there.

Full boot partitions are a common problem, but usually they don't put the computer in an unbootable state. I understand it doesn't boot when you try the default entry or when you try advanced options &#8594; recovery mode. Have you tried an older kernel?

---

### Post by MasterRolfe on 2013-09-22
Here's what's in the boot partion.  I think I did it right:

> ubuntu@ubuntu:/media/ubuntu/fd5b465a-47dc-4e2a-99be-cecb08a148dd/mnt$ ls -R
.:
Boot  EFI  Microsoft  ubuntu

./Boot:
bootx64.efi  bootx64.efi.grb

./EFI:
Boot  Microsoft  ubuntu

./EFI/Boot:
bootx64.efi  bootx64.efi.grb

./EFI/Microsoft:
Boot

./EFI/Microsoft/Boot:
bootmgfw.efi  bootmgfw.efi.grb  bootx64.efi  bootx64.efi.grb

./EFI/ubuntu:
grub.cfg  grubx64.efi  shimx64.efi

./Microsoft:
Boot

./Microsoft/Boot:
bootmgfw.efi  bootmgfw.efi.grb  bootx64.efi  bootx64.efi.grb

./ubuntu:
shimx64.efi



I'm not sure what's meant to be in there, or what isn't.

I tried the oldest kernel option available, in recovery mode. Still no luck.

Someone suggested I reinstall grub, so I'm going to give that a look.

---

### Post by MasterRolfe on 2013-09-22
I've now tried all the kernel recovery modes available in the Advanced menu.  None of them work.  I've listed them below:

> 
Ubuntu, with Linux 3.8.0-30-generic (recovery mode)
Ubuntu, with Linux 3.8.0-29-generic (recovery mode)
Ubuntu, with Linux 3.8.0-27-generic (recovery mode)
Ubuntu, with Linux 3.8.0-26-generic (recovery mode)
Ubuntu, with Linux 3.8.0-19-generic (recovery mode)


All of them take me to a screen that looks like this:

> Loading Linux 3.8.0-30-generic ...
_


And then goes no further.

I tried to run Boot Repair.  It tells me it's successful, but it hasn't fixed anything.  It gives the following info: [http://paste.ubuntu.com/6141306/](http://paste.ubuntu.com/6141306/).  Not sure if that means anything to anyone?

---

### Post by Impavidus on 2013-09-22
This is an EFI system. I don't really know about these. You'll have to wait for someone else to help you.

---

### Post by MasterRolfe on 2013-09-22
Cool.  Thanks for your help!

---

### Post by MasterRolfe on 2013-09-22
So I read up a bit on EFI, and disabled my laptop's Secure Boot feature, which got me a step further.  Now when choosing Ubuntu in the Grub menu, I get to BusyBox.  Being new to this, I don't know what to tell BusyBox to do.

---

### Post by MasterRolfe on 2013-09-22
I've been trying to reinstall Grub2.  I found this thread ([http://ubuntuforums.org/showthread.php?t=1561735&page=2](http://ubuntuforums.org/showthread.php?t=1561735&page=2)) and particularly this instruction:

> Originally Posted by **hhoyt**                     [URL="http://ubuntuforums.org/showthread.php?p=9789138#post9789138"][IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]

[/URL]possibly best to reinstall grub2.
boot your install disk.

from root

1) blkid
< find the partition you installed ubuntu on
2) mount /dev/sdax /mnt      <<< where x is partion #  containing ubuntu and 'a' assumes this is your first hard drive (if have  > 1)
3) mount --bind /sys /mnt/sys
4) mount --bind /dev /mnt/dev
5) mount --bind /proc /mnt/proc
6) chroot /mnt
7)update-grub 
8) grub-install /dev/sda    <assumes the you want grub to be installed on your first hard drive ('a')
9) reboot



Which worked for a few people.  However, at step 6 "chroot /mnt" I get:

> chroot: failed to run command ‘/bin/bash’: No such file or directory

Any ideas anyone?

---

### Post by Extremesheep on 2013-11-23
I'm troubleshooting something similar (13.04 update botching bootloader) to you although my computer behaves differently. This [Howto]("http://ubuntuforums.org/showthread.php?t=1581099") has a similar "chroot" proceedure to what you were following.  My "chroot" succeeds but then fails to use "apt-get".  I think mine fails at least partially because "/usr" has gone missing.

This is a guess but could you try this to see if any of the folders aren't there?  I don't know if 12.04 and 13.04 are directly comparable but "/usr" is definitely missing in one of mine.  There are other differences as well.

Root on working xubuntu 12.04
```
ls /
bin    boot    cdrom    dev    etc    home    initrd.img    initrd.img.old    lib    lost+found    media    mnt    opt    proc    root    run    sbin    selinux    srv    sys    tmp    usr    var    vmlinuz    vmlinuz.old
```

Mounted root on non-booting xubuntu 13.04 run on live CD
```
ls /mnt/temp
bin    boot     BootInfo    boot-sav    cdrom    dev    etc    home    initrd.img     initrd.img.old    lib    lib64    lost+found    proc    root    run     sbin    srv    sys    tmp    var    vmlinuz    vmlinuz.old
```

Even if this is just an example of disk corruption causing errors, it  seems strange to me that a routine mainenance patch would botch the computer to this extent.

---

### Post by steeldriver on 2013-11-23
^^^ that suggests that in *your* case, your original install had a separate /usr partition - which you will need to mount within the /mnt/temp of your chroot. You can probably figure it out by looking at the original fstab (i.e. /mnt/temp/etc/fstab).

What were your actual symptoms? the 'black screen' of the OP is often a problem with graphics driver incompatibility with an updated kernel I think

---

### Post by Extremesheep on 2013-11-24
Should I be putting this in a new thread?  I don't want to hijack his thread but I do think mine fits the description in the thread title.

[SIZE=2]**What were my symptoms?**[/SIZE]
I'm going entirely from memory here.  Also, I'm gonna use /mnt instead of /mnt/temp as the mounting location.

  I have a dual boot Win 7/Xubuntu 13.04 machine.  After installing the updates and resetting, it went directly to the grub command line without a menu.  Then I ran a live CD and ran this [Boot Repair]("http://ubuntuforums.org/showthread.php?p=10871917") script.  Here is the most recent [boot info]("http://paste.ubuntu.com/6462076/") output from this script.  After the boot repair, my computer would boot directly into Windows without showing the grub menu.

Pulled the live CD back up and after mounting the partition, "ls /mnt/boot" would result in input/output errors which is apparently a filesystem issue.  So, I ran this command on my partition which is apparently the method to fix filesystem issues.  It fixed a lot of issues.  There wasn't a count, but maybe a 1000 issues.  When running the command manually, most of the errors I saw were inode mismatches I think.

Note:  The manual said not to use flag "-a" which automatically fixes all issues.  Apparently, "-y" is a better flag to use but I don't know why.  I do know I didn't want to hit enter 1000 times to fix the filesystem.
```

sudo umount /dev/sda6
sudo fsck -Vy /dev/sda6

```

Now, the "ls /mnt/boot" command didn't produce input/output errors.  I tried running this command from the [HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099") page:

```

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

It reported that it found FlexNet in the /boot sector.  [This page]("http://www.leonardomiliani.com/2013/linux-e-flexnet-sul-settore-xx/?lang=en") seems like it had a reasonable solution which was to erase the single offending sector.  Then the grub-install should work.  Then when I ran grub-install, it failed for some reason.  I don't remember.  I used Boot Repair to get my computer working again.

**[SIZE=2]Your other questions:[/SIZE]**
I don't believe I had /usr on a separate partition.  If I manually look at /mnt/etc/fstab, it comes out garbled or in binary.  I pasted below my /mnt/etc/fstab.bak which I had from somewhere.  Boot info up above also has more info about my boot settings.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=0630da02-2f1e-454d-b6b6-85528b256814 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eee21ffe-d1da-4bb2-91f9-a4d370498169 none            swap    sw              0       0

```

---

### Post by Extremesheep on 2013-11-24
Actually, my issue may not fit in this thread anymore since my /boot folder now isn't empty.  It still won't boot though.

---

### Post by steeldriver on 2013-11-24
well having a "garbled or in binary" /etc/fstab would certainly prevent booting (or at least, prevent mounting your root filesystem) - or did you have some kind of whole disk encryption? not sure to what extent boot info can handle that

---

### Post by Extremesheep on 2013-11-24
No, I don't use disk encryption.  I just ran these commands from a live CD.  Then I ran Boot Repair again.  Here is my updated [boot info]("http://paste.ubuntu.com/6471418/").

```

sudo mount /dev/sda6 /mnt
cd /mnt/etc
sudo cp grub.bak grub

```

---

