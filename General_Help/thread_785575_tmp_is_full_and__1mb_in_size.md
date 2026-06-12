---
title: "/tmp is full and  1mb in size"
date: 2008-05-07
forum: General Help
---

### Post by Nelson-Ray on 2008-05-07
This is weird. I installed ubuntu on a single 15 gb partition. Sometimes when I try to download files through firefox into my download directory that has sufficient free space, I get an error message saying /tmp is full please make space or use another directory. My actual / directory has 3GB of free space. I typed in df in the terminal and it shows :

/dev/hda5             17299004  12961780   3458472  79% /
varrun                 1037304       112   1037192   1% /var/run
varlock                1037304         0   1037304   0% /var/lock
udev                   1037304        76   1037228   1% /dev
devshm                 1037304      1484   1035820   1% /dev/shm
lrm                    1037304     38176    999128   4% /lib/modules/2.6.24-12-generic/volatile
overflow                  1024      1012        12  99% /tmp

it looks like the /tmp directroy somehow has its own 1mb partition causing all this problem. It should be in the root directory where there is still free space. I never made this /tmp directory on its own partition nor is there any reference to it in fstab. How can I solve this? thanks...

---

### Post by timcredible on 2008-05-07
/tmp is not in the root directory, it's the swap partition, and it should be at least 512MB.  you need to run gparted to re-do your partitions.

---

### Post by Nelson-Ray on 2008-05-07
aha thanks. I didn't realize /tmp is the swap folder. I checked back in /etc/fstab and mistakenly commented out that partition. Thanks problem now resolved.

---

### Post by alphakamp on 2008-09-10
I have this same problem, and I can not download anything from firefox because of it.  I check my partitions, I have a 3gb swap partition.

What is going on?

---

### Post by prosario_2000 on 2008-10-31
I have the same problem here.

---

### Post by Jonne on 2008-11-02
I have the same thing, and I'm sure the overflow thing has something to do with it. My partition that tmp was on became full, and kicked in the overflow thing, but it seems like it doesn't go to the previous state after a reboot, as it's supposed to do. The biggest issue with this is that flash video's won't play in FF (they'll load a couple of seconds, then fail).

I had the same thing in Hardy once, and just making room on the partition that contained /tmp and rebooting was enough to fix this issue. in Intrepid this doesn't work any more.

---

### Post by Genixoid on 2008-11-06
I have the same trouble and here is a solution:

* create /etc/default/mountoverflowtmp
* put MINTMPKB=8388608 there (this step increase /tmp space up to 8 Mb)
* apply this patch:
```
--- /etc/init.d/mountoverflowtmp.orig   2008-11-06 14:12:38.000000000 +0300
+++ /etc/init.d/mountoverflowtmp        2008-11-06 14:14:30.000000000 +0300
@@ -30,7 +30,7 @@
        [ "$VERBOSE" != no ] && log_action_end_msg 0
        if test $avail -lt "$MINTMPKB"; then
                log_action_begin_msg "Mounting emergency tmpfs on /tmp"
-               mount -t tmpfs -o size=1048576,mode=1777 overflow /tmp
+               mount -t tmpfs -o size=$MINTMPKB,mode=1777 overflow /tmp
                log_action_end_msg 0
        fi
        ;;
```
or
change /etc/init.d/mountoverflowtmp section start (replace mount option size=1048576 with size=$MINTMPKB).

Developers hard coded size of /tmp partition and this patch allow you to manage it by changing /etc/default/mountoverflowtmp parameters.

---

