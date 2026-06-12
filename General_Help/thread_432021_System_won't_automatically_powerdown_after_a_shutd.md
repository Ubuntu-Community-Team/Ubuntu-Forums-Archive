---
title: "System won't automatically powerdown after a shutdown"
date: 2007-05-03
forum: General Help
---

### Post by LucienJ on 2007-05-03
Hi folks,

I'm quite new to Ubuntu and face the following challenge:

After 'pressing' the shutdown button on the desktop Ubuntu stops nicely, yet the computer doesn't power off automatically. I have to press the physical power off button for a few seconds to get it done. Although when booting in rescue mode, and shutting down with 'shutdown -h now' it does so!
I've already played with the /boot/grub/menu.lst and found out that as soon as I specify the 'single' argument to the kernel entry it did do a power off automatically. But hey, then I don't have the graphical shell... Sigh.
I've tried all kinds of options in the /boot/grub/menu.lst, such as "acpi=force" and "lapic", but they don't give the desired effect.

Logging into the console with CTRL+ALT+F1, stopping the gdm with 'sudo /etc/init.d/gdm stop' and then issuing a 'shutdown -h now' also doesn't do the job.

I tried inspecting and comparing the syslog when booting normally and in rescue mode but found out that in rescue mode nothing seems to be logged.

In case it might help, my /boot/grub/menu.lst looks as follows:

---8<-----cut here -------------------
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,7)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,7)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/sda6 ro single
initrd          /initrd.img-2.6.17-11-generic
boot
---8<-----cut here -------------------

Does anybody know if there is a specific option that I need to have, or does anybody know why nothing is logged to my syslog when booting in rescue mode?

Any help is appreciated.

Lucien J.

---

### Post by vav on 2007-05-03
Try 
```

shutdown -P now

```
-h leaves some option open about whether the poweroff happens. I dont know how the system  selects which option (poweroff or not)

---

### Post by LucienJ on 2007-05-04
Thanx for the tip Vav. While browsing I saw the same advice 'shutdown -hP now', but then added in /etc/acpi/powerbtn.sh (see [http://ubuntuforums.org/showthread.php?t=428363](http://ubuntuforums.org/showthread.php?t=428363)) and this solved the problem.

---

