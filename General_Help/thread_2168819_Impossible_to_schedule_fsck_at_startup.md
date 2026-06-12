---
title: "Impossible to schedule fsck at startup"
date: 2013-08-19
forum: General Help
---

### Post by miousername on 2013-08-19
Hi at all,

I'm running ubuntu oneiric on embedded ARM system and I'm trying to schedule fsck at startup.
I tried without success:
        ```
 - touch /forcefsck
         - vim /etc/default/rcS
            ....
            FSCKFIX=yes
            ....
         - add the following bootargs option: fsck.mode=force
```
But still I have the following warning:
        ```
warning: maximal mount count reached, running e2fsck is recom
mended
```

Nobody know a way to check the root filesystem for errors without attach another root filesystem??

Thanks,
Any help it will be really appreciated

---

### Post by ian-weisser on 2013-08-19
Lot of good information in [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)
Including how to change the fsck frequency, discover the current fsck frequency, enable/disable fsck in /etc/fstab, etc.

Check /etc/fstab.
Is fsck enabled (1) in column 6 for the root partition? 
Is it properly disabled (0) for the swap partition?

Check grub.
Is grub using the "fastboot" option? That will prevent fsck.

---

### Post by miousername on 2013-08-21
Hi,

I have already tested the information in:

 [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

without succes. I can't find a Solution.

Other ideas?

---

