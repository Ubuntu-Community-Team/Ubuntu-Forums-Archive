---
title: "[SOLVED] Cannot mount NTFS volume!"
date: 2007-12-07
forum: General Help
---

### Post by demonzrulaz on 2007-12-07
I'm dual-booting Windows XP and Ubuntu 7.10 and it was working fine until I did something to Ubuntu, now it won't mount my XP partition. I tried mounting it and it gave me this error. It also suggested some choices I can take. I tried choice 2 and it works but I have to do it every time I start Ubuntu . I don't know what they mean by it in choice 1 because I only have one hard drive and I can't eject it safely. Can anybody help me?

This is the error details I got:

Cannot mount volume
unable to mount the volume

Details:
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/hda1/': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/hda1 /media/disk -o force  or add the option to the relevant row in the /etc/fstab file:   /dev/hda1 /media/disk ntfs-3g defaults,force 0 0

---

### Post by taurus on 2007-12-07
It means you need to boot into windows and shut it down cleanly.  Try not to use suspend or hibernation to shut down windows.  Try that and see if you can mount it with Ubuntu without any warning or error.

---

### Post by demonzrulaz on 2007-12-09
thanks that helped!

---

### Post by beefsack on 2007-12-10
ah that would be my problem too, reset out of windows because it was annoying me and threw in the ubuntu cd for the first time :o loving it but dont really want to install windows again just to shut it down, any idea as to how to fix it inside linux?

---

### Post by kpkeerthi on 2007-12-10
> **beefsack said:**
> ah that would be my problem too, reset out of windows because it was annoying me and threw in the ubuntu cd for the first time :o loving it but dont really want to install windows again just to shut it down, any idea as to how to fix it inside linux?

[This]("http://ubuntuforums.org/showthread.php?t=636777") might help. Change /dev/sda1 to whatever is appropriate for your system.

Hint: To list your partitions, plug in your external drive and run
```

sudo fdisk -l

```

---

### Post by beefsack on 2007-12-10
thanks a million fixed it no worries :D

---

