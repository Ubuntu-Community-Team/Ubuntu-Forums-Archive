---
title: "Unable to boot: Kernel Panic"
date: 2008-02-11
forum: General Help
---

### Post by Musicalmidget on 2008-02-11
Hi.

Yesterday I setup Ubuntu 7.10 on my laptop.  It was working fine, although it took a very long time to boot.  I would see the GRUB screen, then nothing for roughly 3-5 minutes until the GNOME login screen appeared.  The Ubuntu splash screen was not shown at all.  I searched around the forum and found a thread for a similar problem, in which the user was advised to check the resolution in a particular file which was related to the boot splash screen, I think.  Unfortunately, I can't find the thread again to post here.  I checked the resolution, changed it from 1280x1024 to 1280x800 for my laptop, and then executed the terminal command in the thread, which was to do with updating the splash settings I think.

Basically, since then I've been unable to boot up Ubuntu.  I recieve the following errors.

```
Starting up...
[  13.186806] RAMDISK: ran out of compressed data
[  13.186910] invalid compressed format (err=1)
[  13.187869] Kernel panic - not syncing: VPS: Unable to mount root fs on unknown-block(0,0)
```

I've attempted to re-load grub through the Ubuntu live CD according to the instructions in [this](http://ubuntuforums.org/showthread.php?t=692066) thread, but it doesn't seem to make any difference.

I'm really hoping there's a fix to this that wont entail another evening spent setting up the system, so any advice would be very much appreciated.

Thanks.

---

### Post by pointone on 2008-02-11
Try regenerating the initrd:

```
sudo update-initramfs
```

---

### Post by Musicalmidget on 2008-02-11
I've just booted into the live CD and given that a try.  Unfortunately however, it doesn't seem to have made a difference.

---

### Post by MighMoS on 2008-02-11
I'm not sure why that would happen (seems rather odd), and pointone seems to be on the right track, but if you just boot off of the CD and run update-initramfs it'll update it for the live session, then you reboot and its gone. Try this from a livecd:
```
sudo mount /dev/XdY /mnt
sudo chroot /mnt /bin/sh
sudo update-initramfs
```

Note that X and Y will be your hard drive and partition that you've installed Ubuntu on. Usually this is A and 1, respectively.

---

### Post by Musicalmidget on 2008-02-12
Great!  That seems to have fixed it.

Thanks for the help.

---

