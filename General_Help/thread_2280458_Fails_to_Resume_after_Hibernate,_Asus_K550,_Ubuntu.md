---
title: "Fails to Resume after Hibernate, Asus K550, Ubuntu 14 Gnome"
date: 2015-05-30
forum: General Help
---

### Post by webmanoffesto on 2015-05-30
When I did "sudo pm-hibernate" my laptop resumed fine. But after a  close-the-lid-hibernate it does not resume. I get a blank screen. After  doing a hard-reboot (hold down power button) will get it to shut down,  and then start again. Meaning I "lost" the six programs that were  running, and I have to restart them.

When I run 

ls /var/log/

I find
```

[    0.779237] rtc_cmos 00:05: setting system clock to 2015-05-31 11:08:08 UTC (1433070488)
[    0.779891] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.779892] EDD information not available.
**[    0.779959] PM: Hibernation image not present or could not be loaded.**
[    0.780669] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    0.780670] Write protecting the kernel read-only data: 12288k
[    0.782252] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    0.783605] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    0.793312] systemd-udevd[116]: starting version 204


```






Taking a hint from here blog.shadura.me/2015/04/16/power-button-and-logind/
In the file /etc/systemd/logind.conf
I uncommented two lines and now have
```
HandleHibernateKey=suspend
HandleLidSwitch=suspend`

```

I also did:
```
gedit com.ubuntu.enable-hibernate.pkla
[Disable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=no
          
[Disable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=no

```

but that didn't resolve the problem.

I read that a too-small "swap" file can cause problems but
free -m
Seems to say that is not the problem. My Swap is at least as big as my RAM.
```

total       used       free     shared    buffers     cached
Mem:          3839       3588        251         27          6        162
-/+ buffers/cache:       3419        419
Swap:         3909        136       3773

```

I also followed the instructions here
[B]"Dead, blank, or black screen on resume"
[/B][https://wiki.ubuntu.com/DebuggingKernelHibernate](https://wiki.ubuntu.com/DebuggingKernelHibernate)
Add nomodeset to the end, inside the quotes:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

None of this has resolved the "No Resume from Hibernate After Closing Laptop-Lid" problem. How do I resolve this problem?

Asus K55A Laptop
Ubuntu 14.04.2 LTS Gnome

---

