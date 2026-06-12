---
title: "Ye Olde kernel panic, help would be appreciated as I don't want to wipe this machine"
date: 2015-09-21
forum: General Help
---

### Post by vperaino on 2015-09-21
Not sure what happened. I put the computer into hibernation (probably the first time I've ever done that, incidentally), then I woke it up but decided to restart it because it was acting a little wonky. 

Suddenly, Panic!AtTheBootloader:

[IMG]http://i.imgur.com/GbXb7va.jpg?1[/IMG]

I assume PID 1 means that it's not a hardware issue (unless the HDD got randomly corrupted).

---

### Post by v3.xx on 2015-09-21
PID is something else
[https://en.wikipedia.org/wiki/Process_identifier](https://en.wikipedia.org/wiki/Process_identifier)

Have you tried switching back to previous kernel?
[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

You can also try these commands while in text console:
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get -f install
```

---

### Post by vperaino on 2015-09-21
As it turns out, it may very well be a HDD issue as I'm getting I/O errors when trying to benchmark the disk, and I can't mount the LVM partitions for some reason. Attempting to run a rescue scan with Gparted on another system, we'll see what's what.

---

### Post by tgalati4 on 2015-09-21
Connect your computer with an ethernet cable.  Boot a LiveUSB or DVD.  Install *smartmontools* and examine the SMART status of your disk.

Open a terminal:  

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

PID is process ID #1.  The first process that gets started during boot.  Otherwise known as "init" (initial process) or the "Mother of All Processes".

> tgalati4@Mint17 ~ $ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
**root         1  0.0  0.1  33852  2188 ?        Ss   Sep16   0:05 /sbin/init**
root         2  0.0  0.0      0     0 ?        S    Sep16   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Sep16   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Sep16   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    Sep16   0:27 [rcu_sched]


A bad hard disk can certainly cause a kernel panic.

---

