---
title: "Run Live-CD while using flash drive for package installation"
date: 2015-09-12
forum: General Help
---

### Post by eric89 on 2015-09-12
The title basically says it all.
After my hard drive died on me, I decided to install Ubuntu to my 32GB thumb drive. Sadly, it is agonizingly slow, due to transfer rates from the drive to the processor. 
I've realized that loading up the Live-CD is much faster, and of course, I can't install anything (wine for example). I have installed Google Chrome, but I'm not sure where or how it was installed, as I assume the Live-CD is read-only.

My question is, can I continue to boot using the Live-CD, and somehow tell it to use my thumb drive for installations, packages, updates etc at the same time?.

Thanks in advance :)

---

### Post by v3.xx on 2015-09-12
> **eric89 said:**
> 
My question is, can I continue to boot using the Live-CD, and somehow tell it to use my thumb drive for installations, packages, updates etc at the same time?.


Packages/updates go to different locations in the filesystem.  Your thumb drive will not be able to do this.

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

---

### Post by eric89 on 2015-09-12
Ok, thanks for the info :)

---

### Post by sudodus on 2015-09-13
You can do that, by making a persistent live system.

1. Start gparted from the CD/DVD
2. Create a partition in the pendrive.
3. Create an **ext2** file system in the partition
4. Add the label **casper-rw** to the partition
5. Reboot and at the boot menu, you add the boot option (word) **persistent**
6. Continue the boot process, and when booted, the computer should have grabbed the casper-rw partition for persistence.

-o-

But I think it is more straight-forward to have it all in the pendrive. Create a persistent live drive with [mkusb](https://help.ubuntu.com/community/mkusb), that will do all these things automatically.

If the USB pendrive is slow, there are ways to improve things.

1. Get a faster pendrive. Often the flash memory hardware is limiting the speed. So a fast USB 3 pendrive will be faster also via the computers USB 2 ports. See [this link](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085).

2. Add the boot option **toram** (if you have a lot of RAM). This makes the boot slower, but after that the whole operating system is in RAM, and it will be fast.

3. Use a flavour of Ubuntu with a lighter desktop environment. Xubuntu and Ubuntu MATE are medium light, Lubuntu is ultra light while standard Ubuntu and Kubuntu are fancy but need a lot of CPU/GPU horsepower and RAM to work well.

---

### Post by eric89 on 2015-09-13
Ok, I gave that a shot. I formatted the swap partition on the thumb drive as ext2, and added the label you mentioned. When I went to boot from the USB, it never gave me an option to enter in "persistent", it just booted right to the login screen. I only have 4GB of PC2 ram (old machine), so I didn't try the 2nd option. And yeah, it's a slow drive plugged into an old usb2 port. 

Thanks

---

### Post by sudodus on 2015-09-13
BIOS boot (via syslinux)

Early after booting there are two small symbols at the bottom of the screen. Press a key, when you see them, and you will get to a menu, where you can press F6 to edit the 'linux line' and add boot options at the end (in this case **persistent** and maybe **toram**). See this link for details,

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

UEFI boot (via grub)

This boot looks and works differently. At the grub menu: Press e to edit the 'linux line'. Add boot options at the end (in this case **persistent** and maybe **toram**).

---

### Post by sudodus on 2015-09-13
Grub example:

mkusb's template for the menuentry. You must have the correct file name and path (change ubuntu.iso)

```
menuentry "ubuntu.iso - persistent live" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso quiet splash persistent -- persistent
 initrd (loop)/casper/initrd.lz
}
```

---

### Post by eric89 on 2015-09-13
I booted from the Live-CD, which is the only time I see those characters on the bottom of the screen. Entered persistent at the end of the long boot line, the boot took longer but went right into live desktop instead of going to ubiquity. 

I'm downloading lubuntu now and will try creating the pendrive using mkusb. thanks for the grub lines :)

---

### Post by sudodus on 2015-09-13
> the boot took longer but went right into live desktop instead of going to ubiquity.

I think it works. Try to do something (for example browse the internet, or use the terminal window and write some command or save a file).

Check that it persists after reboot. The most evident case is to check if a file is still there.

---

### Post by eric89 on 2015-09-13
Alright I started from scratch. I formatted the USB entirely and made an ext2 casper-rw partition using the whole drive. Going to reboot a few times and check to see if persistence is working. Fingers crossed.

**EDIT** - I just realized that I'll probably need to reinstall Ubuntu onto the thumb drive before this will work. Sigh...

---

### Post by eric89 on 2015-09-13
Ok, things are running much better now, booted the live-cd and added the **toram** option and things are flying. However, I'm not sure if it will be persistent. I reinstalled ubuntu on the thumb drive, and also turned off swap and made it the ext2 casper-rw section. I usually just keep my computer on all the time. The only thing I've "installed" is google chrome. Still not sure if it will allow me to install other programs, via software center, all i really want is WINE.

Attached is a picture of system monitor, gparted, and disks utilities. Everything looks good, but I don't know if it's using the casper-rw section of my thumb drive or just creating it's own 1.0GB section, as it looks under the /dev/sda/loop bit.

Thanks for all your help :)

---

### Post by sudodus on 2015-09-14
1. Have you checked if a file that you create will persist alias still be there after reboot?

2. Which tool did you use to create the current system in the pendrive?

3. You can run these commands in order to indicate what is used for persistence.

```
df -h
sudo lsblk -fm
```

Please post the output of both commands within [noparse]```
tags
```[/noparse].

---

### Post by eric89 on 2015-09-14
output of df -h
```
 ubuntu@ubuntu:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
/cow            1.7G  340M  1.4G  21% /
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           338M  1.2M  337M   1% /run
/dev/shm        1.1G 1006M   50M  96% /cdrom
/dev/loop0      963M  963M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           1.7G  1.2M  1.7G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.7G   27M  1.7G   2% /run/shm
none            100M   76K  100M   1% /run/user
/dev/sda5       3.4G  6.0M  3.2G   1% /media/ubuntu/casper-rw
/dev/sda1        26G  5.3G   19G  23% /media/ubuntu/f412d62a-191a-47a1-b513-537321e064d5
/dev/sr0       1006M 1006M     0 100% /media/ubuntu/Ubuntu 14.04.3 LTS amd64

```

output of sudo lsblk -fm
```
 ubuntu@ubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL            MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                         sda     29.1G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4                      /media/ubu &#9500;&#9472;sda1  25.7G root  disk  brw-rw----
&#9500;&#9472;sda2                                      &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 ext2     casper-rw        /media/ubu &#9492;&#9472;sda5   3.4G root  disk  brw-rw----
sr0    iso9660  Ubuntu 14.04.3 LTS amd64
                                 /media/ubu sr0     1006M root  cdrom brw-rw----
loop0  squashfs                  /rofs      loop0  962.1M root  disk  brw-rw----

```

I used ubiquity to install ubuntu back onto the thumb drive. I'll check to see if a file stays after reboot using toram now :)

EDIT -- I saved a text document to the desktop before rebooting and it was not there when I loaded the system back up.

**Also, running in persistent mode seems to be more stable than toram mode. No lockups or weird mouse behavior when using persistent.

---

### Post by sudodus on 2015-09-14
> **eric89 said:**
> output of df -h
```
 ubuntu@ubuntu:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
[COLOR="#FF0000"]/cow            1.7G  340M  1.4G  21% /[/COLOR]
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           338M  1.2M  337M   1% /run
/dev/shm        1.1G 1006M   50M  96% /cdrom
/dev/loop0      963M  963M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           1.7G  1.2M  1.7G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.7G   27M  1.7G   2% /run/shm
none            100M   76K  100M   1% /run/user
[COLOR="#FF0000"]/dev/sda5       3.4G  6.0M  3.2G   1% /media/ubuntu/casper-rw[/COLOR]
/dev/sda1        26G  5.3G   19G  23% /media/ubuntu/f412d62a-191a-47a1-b513-537321e064d5
/dev/sr0       1006M 1006M     0 100% /media/ubuntu/Ubuntu 14.04.3 LTS amd64

```

output of sudo lsblk -fm
```
 ubuntu@ubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL            MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                         sda     29.1G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4                      /media/ubu &#9500;&#9472;sda1  25.7G root  disk  brw-rw----
&#9500;&#9472;sda2                                      &#9500;&#9472;sda2     1K root  disk  brw-rw----
[COLOR="#FF0000"]&#9492;&#9472;sda5 ext2     casper-rw        /media/ubu &#9492;&#9472;sda5   3.4G root  disk  brw-rw----[/COLOR]
sr0    iso9660  Ubuntu 14.04.3 LTS amd64
                                 /media/ubu sr0     1006M root  cdrom brw-rw----
loop0  squashfs                  /rofs      loop0  962.1M root  disk  brw-rw----

```

I used ubiquity to install ubuntu back onto the thumb drive. I'll check to see if a file stays after reboot using toram now :)

EDIT -- I saved a text document to the desktop before rebooting and it was not there when I loaded the system back up.

**Also, running in persistent mode seems to be more stable than toram mode. No lockups or weird mouse behavior when using persistent.

The [COLOR="#FF0000"]red lines[/COLOR] should match and they don't, so the casper-rw partition is not used.

You must use the boot option persistent to get persistence, toram has another function (to use a ramdrive). They are independent of each other, so you can use both of them, persistent to get persistence and toram to get the whole operating system to RAM, which makes it faster (except at boot).

This works in a persistent live system made by mkusb (I add toram to the 'linux' command line in the grub menu, persistent is already there).

Edit: I don't know why it does not work for you. Maybe some minor detail is wrong, and you would get it right the next time. When you know how it should be to work, you can edit some files instead of the grub menus, so that it will use the selected boot options automatically.

---

### Post by eric89 on 2015-09-14
Ah ha, I figured something out. If I boot into persistent mode then the output of df -h = 
```
 ubuntu@ubuntu:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
/cow            3.4G  609M  2.6G  19% /
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           338M  1.2M  337M   1% /run
/dev/sr0       1006M 1006M     0 100% /cdrom
/dev/loop0      963M  963M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           1.7G  1.2M  1.7G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.7G   85M  1.6G   5% /run/shm
none            100M   72K  100M   1% /run/user
/dev/sda5       3.4G  609M  2.6G  19% /media/ubuntu/casper-rw
/dev/sda1        26G  5.3G   19G  23% /media/ubuntu/f412d62a-191a-47a1-b513-537321e064d5

```

so they match when using persistent, but not toram. Hmm, I can't say I know exactly why that is, But it seems now that casper-rw is being used. :)

---

### Post by sudodus on 2015-09-14
Yes, now it looks like you have persistence :-) You can test that things (files, tweaks etc) survive (are still there) after reboot.

You need the boot option persistent. You can add the boot option toram (which makes the system faster). These two boot options are independent of each other, they do their job alone or together, but they will not do the job of the other boot option. If you want persistence and a fast system you should use ***both*** boot options.

---

### Post by eric89 on 2015-09-14
I tried using both options, either by typing "toram persistent" or "persistent toram", and both times I was brought to a login screen which required username and password. I tried my  credentials from the USB installation, and that didn't work.

On a side note, before rebooting, i had started to install updates, well, the linux kernel update failed, and then it moved onto some other thing, needless to say, I was frustrated and didn't bother letting it finish. Maybe that's why the live-cd boot option is giving me a strange login screen... my fault.

Right now, im booted from the USB key only, in hindsight, i probably should have let the updates finish, but I'm not a very patient person. hahaha

---

### Post by sudodus on 2015-09-14
I think you are right about the interrupted updates, it can damage an operating system.

A persistent live system cannot update/upgrade the kernel. It is locked to the kernel that comes with the iso file. But other program packages can be updated/upgraded, and tweaks can survive, however, with a lot of updates/upgrades the system will start very slowly, and it will be sensitive (and might get broken).

So if you want to keep a system completely up to date, it is better to have an installed system. If you get a [fast USB 3 pendrive](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites) and install Lubuntu or Xubuntu or Ubuntu MATE, it will be reasonably fast (even in a USB 2 port of the computer).

---

### Post by eric89 on 2015-09-14
I think I'm just going to purchase an SSD sooner or later. Until then, all is well here. Thanks :) Solved.

---

### Post by sudodus on 2015-09-14
I'm glad that you feel that your problem is solved :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help other users find your solution.

---

