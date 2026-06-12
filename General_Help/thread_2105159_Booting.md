---
title: "Booting"
date: 2013-01-15
forum: General Help
---

### Post by tad1073 on 2013-01-15
Ubuntu will only boot from recovery mode, when I try to boot normally all I get is the purple background that grub uses.

Nvidia Gforce GTX 550i w/ and w/o nvidia drivers.

---

### Post by dino99 on 2013-01-15
you should remove "quiet splash" from the boot line, to see the verbose mode and the possible warnings/errors

---

### Post by tad1073 on 2013-01-15
> **dino99 said:**
> you should remove "quiet splash" from the boot line, to see the verbose mode and the possible warnings/errors

I've tried that and the same thing happens.

---

### Post by sdowney717 on 2013-01-15
look at the system log in /var/log

It is likely something to do with the video.
'EE' are error code headers 
'WW' are warnings

Xorg.0.log is the file to look into.

---

### Post by tad1073 on 2013-01-15
> **sdowney717 said:**
> look at the system log in /var/log

It is likely something to do with the video.
'EE' are error code headers 
'WW' are warnings

Xorg.0.log is the file to look into.

It didn't generate one for the normal boot only for recovery mode.

---

### Post by oldfred on 2013-01-15
Have you used nomodeset in place of splash quiet?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tad1073 on 2013-01-15
> **oldfred said:**
> Have you used nomodeset in place of splash quiet?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I got it working, thanks. The first link did it.

---

