---
title: "Dual boot: &quot;Superblock last write time is in the future&quot; and cannot log in"
date: 2015-06-20
forum: General Help
---

### Post by randy17 on 2015-06-20
I dual boot Ubuntu 14.04 and Windows 8.1. I was having trouble with Windows sometimes showing the wrong time, so I tried a solution ([http://lifehacker.com/5742148/fix-windows-clock-issues-when-dual-booting-with-os-x](http://lifehacker.com/5742148/fix-windows-clock-issues-when-dual-booting-with-os-x)) that involves adding a registry key RealTimeIsUniversal with a value of 1. After doing so, I went to boot into Ubuntu, and I could not get past the login screen. My home directory is owned by the correct user, and I tried 

              ```
sudo chmod -R ug+rwx /home/[username]
```

as suggested here: [http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade](http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade). 

I tried running fsck and got messages saying "Superblock last mount time is in the future. (by less than a day, probably due to the hardware clock being incorrectly set). FIXED". It is nice that it says "fixed", but this actually does not fix the problem, and running fsck again returns the same result. However, I do not know if fsck actually applies some sort of permanent fix or if such a fix is only applied when the program finishes running. Like others ([https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1061239/](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1061239/)), I find that fsck stalls when I run it from recovery. Thus I am not sure if any fix actually stuck (not that I know anything about how fsck works)

I tried deleting that key from the Windows registry, but this changed nothing. It has also been more than a week since the computer was turned on, so I guess I cannot just wait a day to trick the computer into thinking the mount time is in the past.

There is some error or warning message when the splash screen appears, but it shows up too briefly for me to read it, and I do not know where it would show up in any log file.

Advice is appreciated. I want to avoid a clean install if possible, as it would require downloading half a terabyte of Dropbox files plus lots of applications, making my ISP mad and halting my work for a day.

---

### Post by dino99 on 2015-06-20
i've kicked windows since 2005, so i cant tell much about it nowadays. That said, i suppose ubuntu being a real install (not a wubi one, which is deprecated since a while). The clock 'in the future' error should not matter anyway, as ubuntu by default is syncing with ntpdate, and the boot process does not care and is not aware of such 'cosmetic' problem.
so better to glance at the bios settings (maybe reset it, aka remove its battery for a while) or with uefi, both installations need to be set the same way (see oldfred's threads/posts about explanations)

---

### Post by randy17 on 2015-06-20
I did not change anything in the BIOS between observing the correct behavior and the incorrect behavior. Oldfred has many thousands of posts; do you have any more specific directions about which of them to see?

---

### Post by randy17 on 2015-06-28
I could really use some help with this. I am thinking of just abandoning Ubuntu.

---

