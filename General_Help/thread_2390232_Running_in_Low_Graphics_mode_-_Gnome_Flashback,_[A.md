---
title: "Running in Low Graphics mode - Gnome Flashback, [AMD/ATI] Cape Verde PRO [Radeon HD 7"
date: 2018-04-26
forum: General Help
---

### Post by RogerDavis on 2018-04-26
After a recent update (kernel?), I have begun to occasionally receive the message "Running in Low Graphics Mode" at boot (maybe half the time).  I can tell it to use Default setting from the options it offers, and get by it, after which things look and work normally, even after some reboots.

I also usually get "System error detected, Report? at the same time, so I agree to report it.

Please note that I'm using 16.04 (fully updated),  Gnome Flashback Metacity, with [AMD/ATI] Cape Verde PRO [Radeon HD 7750/8740 / R7 250E] .

This problem shows up no matter which of the above I'm using, or Unity...

roger@roger-desktop:~$ uname -a
Linux roger-desktop 4.4.0-124-generic #148-Ubuntu SMP Wed May 2 13:00:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

I've seen some suggestion like :
# sudo apt-get update
# sudo apt-get remove ubuntu-desktop
# sudo apt-get install ubuntu-desktop
# sudo shutdown -r now
But these are all quite old, at least 3 years, up to 6 or more years, and some of the simple items in some of these (boot while holding (shift), ... just don't work, so I'm afraid of them.

I's unclear to me if this would wipe out my Gnome and Cinnamon, etc. installations, or if that is separate and safe.  Please advise...

There appears to be plenty of memory and storage available.

roger@roger-desktop:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:          16013        3880       10410         363        1722       11443
Swap:         16348           0       16348

roger@roger-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sda1       902G   77G  779G   9% /
tmpfs           7.9G  127M  7.7G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G   52K  1.6G   1% /run/user/1000


Also, if I simply go to 18.04 ( don't really want to just yet ) will it likely fix this in the process, or might this block or damage the upgrade ?

---

### Post by Claus7 on 2018-05-03
Hello,

I used 16.04 for a short amount of time and I did not face such an issue (similar graphics card). Yet, have you tried to re-install the drivers? Usually in a kernel update things might get messed up.

I have not faced such an issue even when upgraded to 18.04.

Regards!

---

