---
title: "Ubuntu 12.04 Unable to boot after unexpected shut down"
date: 2015-02-24
forum: General Help
---

### Post by kuanjian on 2015-02-24
After an unexpected power cutoff on my pc, I am not able to boot my Ubuntu 12.04 which is running in Virtualbox. I have recorded the boot-up screen which can be found at [http://tinypic.com/r/2l9jssh/8](http://tinypic.com/r/2l9jssh/8)

There are important content and MySQL database that I need to retrieve. It will be great if anyone can help me resolve my issue.

---

### Post by Ruben_van_Smirren on 2015-02-24
Try to run the installation media again and see if you can repair the OS that way.

---

### Post by kuanjian on 2015-02-25
> **Ruben_van_Smirren said:**
> Try to run the installation media again and see if you can repair the OS that way.

I followed the instructions at [http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/) 

I managed to enter the command line rescue mode using the media. But I have no idea on what to do next.

How do I repair the grub boot?

---

### Post by Bashing-om on 2015-02-25
kuanjian; Hello;

A loss of power - even though 'buntu is a journal-ed file system - can leave the file system in an inconsistent state.
I do suggest that a file system check/repair be run. And then if the boot problem persists then grub be (RE-)installed.

Boot the liveDVD(USB) of the same same release ( this is important that it be same same ) .. boot to "try ubuntu" to terminal and run terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
to identify the hard drive and partition that we are working with:

Try and fix the file system:
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
where 'sda1' is the 1st hard drive and '/' is that 1st partition ( the partition that ubuntu is installed onto).

If errors are reported, next:
```

sudo e2fsck -f -y -v /dev/sda1

```

Maybe this resolves the issue, maybe not. If the issue continues next we resort to (RE-)installing grub. We leave that for the next lesson.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by kuanjian on 2015-02-27
I tried the steps above and ran ```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` but there is no luck. I'm still not able to boot into Ubuntu.
[ATTACH=CONFIG]260306[/ATTACH]

Any other method that I can try?

---

### Post by Bashing-om on 2015-02-27
kuanjian; Yeaya; There are always options:


The file system check looks good.
I suggest at this time we (RE-)install the bootloader.
This will require the liveDVD(USB) as the same same release as that installed to the hard drive.
Post back the results of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
so that we know what the installed partitions are and where they are located. Once known we can then direct where to RE-install grub.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by kuanjian on 2015-02-27
Hi Bashing-om, thank you for your support.

Talking about the same same release. Actually, the system I'm not able to boot into is "Ubuntu 12.04.4 Server" but I'm using "Ubuntu 12.04.4 Desktop" LiveDVD to run the commands. Is this consider as same same release?

From Ubuntu Desktop - LiveDVD Terminal
[ATTACH=CONFIG]260320[/ATTACH]

From Ubuntu Server - Rescue Mode Terminal
[ATTACH=CONFIG]260321[/ATTACH]http://s12.postimg.org/cxr3zqy5p/server_rescue_mode_result.gif

---

### Post by Bashing-om on 2015-02-28
kuanjian; Hummm ...

Looks like you have chosen 'encryption' -> LVM is a factor and I have no experience with encryption.
Can not enlarge the .gif images to make out anything.
We do prefer text output copied/pasted between code tags. Much much easier to work with from a troubleshooting perspective.

Wont hurt things any further to 'try' and re-install grub:
from the liveDVD:
```

sudo mount /dev/sda1 /mnt/boot

```

With that small /boot partition there is the concern that there exist space constraints, - no space left on device !
what returns:
```

ls -al /mnt/boot/
df -h
df -i

```

If it appears there is space available then install grub:
```

sudo grub-install --boot-directory=/mnt/boot /dev/sda
sudo umount /mnt/boot

```

Reboot into the install ..  and let's see. If you boot into the system:
```

sudo update-grub

```

[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

