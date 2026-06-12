---
title: "Dapper freezes"
date: 2008-04-12
forum: General Help
---

### Post by karrank% on 2008-04-12
Dapper (yes, I'm still using it) freezes intermittently, and unpredictably. Perused all the related threads (excellent feature btw) without success. Don't know where to post, this seemed like a good start. Trying to get the family off windows, but won't be able to if this keeps up. Any ideas where to start?

---

### Post by ellgor on 2008-04-12
Hi 

Are you by any chance using Nautilus as a file manager etc., I was using dapper until very recently, and found that when Nautilus crashed the whole system went with it, I changed to KDE (konqueror is a good manager) and what I did find was that if an application crashed it was only that app that crashed and not the whole system, hope this is of help.

Regards, Ellgor.

---

### Post by Crafty Kisses on 2008-04-12
Hey, don't worry about using Dapper man, I do too.:)

Can you post the following output?
```
top
```

---

### Post by Zill on 2008-04-12
Nothing wrong with Dapper - it is a rock solid version that should serve you well until the next LTS version is released - ie. any day now :-)

It may be software configuration problems causing the freezing but it could also be hardware failure.  You may like to run memtest from either the Live CD or the grub menu during boot.  Run this for several hours and it will determine if the RAM is flakey.

---

### Post by karrank% on 2008-04-13
ellgor, thanks, and yes to the nautilus, I believe it arrived with the CD. It seems to "freeze" not so much as "crash" although the two terms describe the same event (?)

codename, I'll post top as soon as I can figure out how. from terminal maybe?

and zill, i'll run memtest tomorrow

Thanks for all the helpful hints

---

### Post by Crafty Kisses on 2008-04-13
Yeah, type it in the Terminal.

---

### Post by Zill on 2008-04-13
karrank% - My apologies if you already know this but here are a couple of pointers that may help :???:

When you want to run a command such as "top" you open a terminal (menu Applications, Accessories, Terminal).  This is similar to the old Windows DOS box, so you simply type the command, or, if long, copy and paste it to prevent errors!  Many commands can be run by the user, but "admin" commands must be prefaced by the command "sudo", which will then ask for your user password as authorisation.

If you want to know more about any command, just type "man" followed by the command, eg "man top", at the terminal prompt.  This will show the appropriate manual page, which can be closed by typing "q", returning you to the prompt.

"top" is a very useful command as it shows which processes are currently running.

If you reboot with the Live CD in the drive, you should see a menu option to run memtest from the CD, rather than Ubuntu.  Alternatively, if Ubuntu is installed on the harddrive then memtest is also installed and can be chosen at bootup.  You should see, briefly, an option while starting boot to press Esc to access the GRUB menu.  If you do this you will see memtest as an option.  Simply select this to test your RAM.

---

### Post by karrank% on 2008-04-13
> **Codename said:**
> Yeah, type it in the Terminal.
Egad! Zombie? I have gmail, have I been screwed?
And I remember how to do memtest, but will have to wait a bit on that.
-Thanks again gents...
errr, ladies, whatever...:D
Tasks:  94 total,   2 running,  91 sleeping,   0 stopped,   1 zombie
Cpu(s):  7.0% us,  1.7% sy,  0.0% ni, 91.0% id,  0.0% wa,  0.0% hi,  0.3% si
Mem:   1555264k total,   525820k used,  1029444k free,    74868k buffers
Swap:   738948k total,        0k used,   738948k free,   222308k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4686 root      16   0 56500  43m 8656 R  7.0  2.9   0:28.72 Xorg
 6265 fordpref  15   0 50640  15m 9.8m S  1.3  1.0   0:02.61 gnome-terminal
 5139 fordpref  15   0 54616 8536 6924 S  0.3  0.5   0:01.62 gnome-cups-icon
    1 root      16   0  1568  528  460 S  0.0  0.0   0:01.06 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.05 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  124 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  125 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  127 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  126 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  714 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1729 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1730 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata_hotplug/0
 1733 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1734 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1840 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1987 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 2215 root      12  -4  2432  920  368 S  0.0  0.1   0:00.24 udevd
 3098 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3131 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
 3132 root      10  -5     0    0    0 S  0.0  0.0   0:00.16 usb-storage
 3250 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3635 dhcp      13  -2  2336  544  236 S  0.0  0.0   0:00.00 dhclient3
 4213 root      16   0  1684  496  412 S  0.0  0.0   0:00.01 dd
 4215 klog      18   0  2428 1356  388 S  0.0  0.1   0:00.04 klogd
 4239 messageb  16   0  2196  872  668 S  0.0  0.1   0:00.02 dbus-daemon

---

