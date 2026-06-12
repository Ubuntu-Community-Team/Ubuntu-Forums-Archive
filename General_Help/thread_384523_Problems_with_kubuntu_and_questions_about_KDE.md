---
title: "Problems with kubuntu and questions about KDE"
date: 2007-03-14
forum: General Help
---

### Post by Homayoon on 2007-03-14
I'm trying to give KDE a try. Having a 10GB (still) unused partition, I decided to install Kubuntu Edgy on it. But when I choose the option during installation to edit the partition table manually I see an error message that says QTParted has crashed (I don't actually need to edit the partition table, but it seems to be the only option that lets me choose where to install Kubuntu). I retried from a command line to see if there are any error messages. I saw it says that qtparted does not support NTFS partitions:

```
No Implementation: Support for opening ntfs file systems is not implemented yet.
```

 (I do have those NTFS partitions, the Windows legacy, because I do not have enough free space to convert all to ext3)

Searching through the forums I only found [this thread]("http://ubuntuforums.org/showthread.php?t=334267") which concludes one should use the alternate install CD to solve the problem. My internet connection is not very fast (128Kbps) so I prefer not to wait a whole 24 hours downloading! Is there a way to use the live CD to install?


Meanwhile, I installed kdebase package on my Ubuntu Dapper installation. I have a few questions about using KDE:

- Firefox does not look good in KDE. Is there a way to have it have the same appearance as the whole system?

- I was surprised that I could not find any option to change display resolution. The only thing I finally managed to do was to remove any reference to 1280x960 resolution in /etc/X11/xorg.conf in order to have the system use the 1024x768 resolution. Isn't there a better solution?

I appreciate any help.

---

