---
title: "How do I format a USB pendrive"
date: 2007-02-25
forum: General Help
---

### Post by jonnymccullagh on 2007-02-25
I just bought a 4gb pen drive used it a few times to transfer files between my Ubuntu and my firends Ubuntu - now I have a few problems. I have a lot of big files appearing with gobbledegook ( ½&#8359;fÿ.&#8730;&#9500;&#9580;) names on the drive. I cannot seem to delete these as Ubuntu is reporting it as a read-only device.
So I thought I would try to reformat it again (FAT). I cannot find a way to do that? I tried Gparted but even it is giving me errors and warnings.
Is there an easy way to reformat or to remove these odd files?

---

### Post by xfile087 on 2007-02-25
Just a thought - did you unmount the drive first before trying to format?

If so and GParted still isn't working you could always try cfdisk from the terminal?

---

### Post by jonnymccullagh on 2007-02-25
thanks but I "ejected" the pendrive and ran gparted and the does not even show up now (previously showed up as sde).
How do I use cfdisk and what does it do?
thanks,
jonny

---

### Post by dcstar on 2007-02-25
> **jonnymccullagh said:**
> thanks but I "ejected" the pendrive and ran gparted and the does not even show up now (previously showed up as sde).
How do I use cfdisk and what does it do?
thanks,
jonny

System-Preferences-Removable Drives & Media, untick the first two auto-mount options.

Now insert the USB drive and you will be able to use Gparted to format it etc.

With those first two things ticked, the partitions mount in the middle of Gparted operations and actually prevent the whole process from completing!

You can re-tick them once you have finished with the process.

---

### Post by chilli on 2007-09-30
> **jonnymccullagh said:**
> I just bought a 4gb pen drive used it a few times to transfer files between my Ubuntu and my firends Ubuntu - now I have a few problems. I have a lot of big files appearing with gobbledegook ( ½&#8359;fÿ.&#8730;&#9500;&#9580;) names on the drive. I cannot seem to delete these as Ubuntu is reporting it as a read-only device.
So I thought I would try to reformat it again (FAT). I cannot find a way to do that? I tried Gparted but even it is giving me errors and warnings.
Is there an easy way to reformat or to remove these odd files?
I know this thread is old, but for the ones that have the same problem:

I also bought two 1GB pendrives some time ago that had the same problems. Those wacky ( ½&#8359;fÿ.&#8730;&#9500;&#9580;) characters seem to appear from nowhere. I realized that it only happened when I had more than 600 MB of data in the drive. It was a hardware problem. Same behaviour several times both in linux and windows.

---

### Post by indian_gamer2003 on 2007-11-15
Thank you for the help, you just saved a linux noob from trouble.

---

### Post by saverjack on 2008-06-15
i'm having a problem with my pen drive it shows all the content to be read only i'm unable to format it i exactly dunno  about its label sda1 0r sda2...
help me Thanks

---

