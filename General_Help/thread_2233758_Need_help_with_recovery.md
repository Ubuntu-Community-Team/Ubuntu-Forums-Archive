---
title: "Need help with recovery"
date: 2014-07-10
forum: General Help
---

### Post by David_Knox on 2014-07-10
I received a warning message that stated my boot folder was nearly filled. I deleted the image files and now Ubuntu won't start. I saved the files I deleted. How can I restore my system?

---

### Post by Bashing-om on 2014-07-10
David_Knox; Hi ! Welcome to the forum.

How did you remove the files ? With a "apt-get remove" or 'dpkg' , such that the package manager is aware of your actions ? Let's look and see what we have left to work with and get a better idea of what the situation is:
Boot up the liveDVD and post back to us -between code tags, please - the hard disk partitioning so we know how to mount the root partition, and have a looksee.
```

sudo fdisk -lu
sudo parted -l 

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]we will get this booting situation fingered out -> one step at a time
[/INDENT][/INDENT]

---

### Post by Impavidus on 2014-07-10
You mean you deleted all the /boot/initrd.img-<version> files because they were the largest? They contain the kernel image, the operating system itself, which is rather vital for booting.

You have to boot from a live disk. Putting those files back in /boot of the installed system and pretending nothing ever happened might work – it's worth a try. Else you have to chroot into your system and reinstall the linux-image-<some version> packages (at least the most recent of them) through the package manager.

The proper way to clean /boot is by using the package manager (software centre, synaptic, apt-get, ..., whichever front-end you prefer) to uninstall old versions of linux-image-<version>.

---

