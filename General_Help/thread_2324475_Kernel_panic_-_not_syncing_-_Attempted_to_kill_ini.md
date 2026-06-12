---
title: "Kernel panic - not syncing - Attempted to kill init"
date: 2016-05-14
forum: General Help
---

### Post by darekch on 2016-05-14
Suddenly  I can't boot as I receive 'kernel panic - not syncing - Attempted to  kill init'. I tried to use previous kernel, then reinstall kernels but  all that didn't help me. I have luks encrypted partition which contains  multiple lvm with ext4 volumes. This was working since 14.04 was  released so this not standard configuration should not cause this issue.
I am able to run live cd, then decrypt luks partition and mount volumes  and chroot. All seems to be ok. I fsck lvm and all is ok.
I found similar issue [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1273261](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1273261)  which suggest to try udev_settle. This didn't helped. I even entered  sleep 5 (thus "sleeping for 5 secs" message on the stacktrace in the  middle) but this didn't solve the issue. Maybe I enter this hack too  early in the script?
 No more idea... so mayday, mayday...
I attached photo of the stacktrace and report of 'apport-cli linux-generic'.

I created bug issue but maybe someone here will help me first? Lack of computer is a big problem :(
[https://bugs.launchpad.net/ubuntu/+bug/1581761](https://bugs.launchpad.net/ubuntu/+bug/1581761)

---

### Post by poltiser2 on 2016-05-14
I noticed the same problem on any kernel 4.5... during switching off only. Hard switch does the trick and I can reboot and use computer normally... 
Any remedy?

Xubuntu 16.04 AMD64 kernel 4.5.3

---

### Post by darekch on 2016-05-14
No. The only change is that instead of message 'fstype not found' I have message 'can't open /dev/mapper/ubuntu-root no such file'.

---

### Post by darekch on 2016-05-18
Anyone... I really tried multiple of options. I installed multiple kernels, even the newest ones, I did autoclean, memtest I even enabled only single core just to be sure it's not some way of concurrency issue.

---

### Post by darekch on 2016-06-10
After 2 weeks of fight I had to backup data and reinstall to 16.04. Well, newly installed OS is always fresh and spicy but it's sad I could not fix the real problem.

---

