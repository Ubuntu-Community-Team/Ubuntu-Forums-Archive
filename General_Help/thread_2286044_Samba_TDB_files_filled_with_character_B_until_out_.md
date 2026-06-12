---
title: "Samba TDB files filled with character B until out of space"
date: 2015-07-09
forum: General Help
---

### Post by ssexton on 2015-07-09
The following four files are being filled with "B"s until the /run/lock partition is full.  This is causing users to lose connection to the Samba shares.
  connections.tdb
  sessionid.tdb
  locking.tdb
  messages.tdb
What can be causing this, a virus?
How can I tell what process is causing this?
Here is a little df and file info:

[SIZE=1][FONT=courier new]root@mpcnet:/run/lock/samba# df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/umpnet-root  813G   69G  704G   9% /
udev                     6.0G  4.0K  6.0G   1% /dev
tmpfs                    2.4G  360K  2.4G   1% /run
none                     5.0M  5.0M     0 100% /run/lock
none                     6.0G     0  6.0G   0% /run/shm
/dev/sda1                228M   26M  191M  12% /boot
root@mpcnet:/run/lock/samba# service smbd stop
smbd stop/waiting
root@mpcnet:/run/lock/samba# rm connections.tdb
root@mpcnet:/run/lock/samba# rm locking.tdb
root@mpcnet:/run/lock/samba# rm messages.tdb
root@mpcnet:/run/lock/samba# rm sessionid.tdb
root@mpcnet:/run/lock/samba# df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/umpnet-root  813G   69G  704G   9% /
udev                     6.0G  4.0K  6.0G   1% /dev
tmpfs                    2.4G  356K  2.4G   1% /run
none                     5.0M  4.7M  380K  93% /run/lock
none                     6.0G     0  6.0G   0% /run/shm
/dev/sda1                228M   26M  191M  12% /boot
root@mpcnet:/run/lock/samba# date
Thu Jul  9 10:33:30 CDT 2015
root@mpcnet:/run/lock/samba# service smbd start
smbd start/running, process 20057
root@mpcnet:/run/lock/samba# df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/umpnet-root  813G   69G  704G   9% /
udev                     6.0G  4.0K  6.0G   1% /dev
tmpfs                    2.4G  360K  2.4G   1% /run
none                     5.0M  5.0M     0 100% /run/lock
none                     6.0G     0  6.0G   0% /run/shm
/dev/sda1                228M   26M  191M  12% /boot
root@mpcnet:/run/lock/samba# date
Thu Jul  9 10:34:20 CDT 2015
root@mpcnet:/run/lock/samba# tail connections.tdb
TDB file
m&âQ¡
     sö¦+D¦v+pºFÇXxÇkaP+oPÆá|+½+ìtxë(ú0à¦hfµ¦+BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB

[/FONT][/SIZE]

---

### Post by ssexton on 2015-07-09
Here is a condensed list of processes running.  Known users processes removed and duplicate CMD removed.

[SIZE=1][FONT=courier new]UID        PID  PPID  C STIME TTY          TIME CMD
root      1808     1  0 Jul08 tty1     00:00:00 /bin/login --
root      1375     1  0 Jul08 tty5     00:00:00 /sbin/getty -8 38400 tty5
root        45     2  0 Jul08 ?        00:00:00 [ata_sff]
root        42     2  0 Jul08 ?        00:00:00 [bdi-default]
root        71     2  0 Jul08 ?        00:00:00 [binder]
root        92     2  0 Jul08 ?        00:00:00 [charger_manager]
root        36     2  0 Jul08 ?        00:00:00 [cpuset]
root        56     2  0 Jul08 ?        00:00:00 [crypto]
root        91     2  0 Jul08 ?        00:00:00 [deferwq]
root        93     2  0 Jul08 ?        00:00:00 [devfreq_wq]
root        55     2  0 Jul08 ?        00:00:00 [ecryptfs-kthrea]
root       710     2  0 Jul08 ?        00:00:00 [edac-poller]
root       326     2  0 Jul08 ?        00:00:00 [ext4-dio-unwrit]
root      1099     2  0 Jul08 ?        00:00:02 [flush-252:0]
root        54     2  0 Jul08 ?        00:00:00 [fsnotify_mark]
root       291     2  0 Jul08 ?        00:00:00 [hpsa]
root       325     2  0 Jul08 ?        00:00:05 [jbd2/dm-0-8]
root        44     2  0 Jul08 ?        00:00:00 [kblockd]
root        38     2  0 Jul08 ?        00:00:00 [kdevtmpfs]
root       305     2  0 Jul08 ?        00:00:00 [kdmflush]
root        37     2  0 Jul08 ?        00:00:00 [khelper]
root        46     2  0 Jul08 ?        00:00:00 [khubd]
root        53     2  0 Jul08 ?        00:00:00 [khugepaged]
root        50     2  0 Jul08 ?        00:00:00 [khungtaskd]
root        43     2  0 Jul08 ?        00:00:00 [kintegrityd]
root       692     2  0 Jul08 ?        00:00:00 [kpsmoused]
root        52     2  0 Jul08 ?        00:00:00 [ksmd]
root        30     2  0 Jul08 ?        00:00:01 [ksoftirqd/6]
root        51     2  0 Jul08 ?        00:00:04 [kswapd0]
root         2     0  0 Jul08 ?        00:00:00 [kthreadd]
root       733     2  0 Jul08 ?        00:00:00 [kvm-irqfd-clean]
root      6252     2  0 07:57 ?        00:00:02 [kworker/u:2]
root        47     2  0 Jul08 ?        00:00:00 [md]
root        12     2  0 Jul08 ?        00:00:00 [migration/2]
root        39     2  0 Jul08 ?        00:00:00 [netns]
root        67     2  0 Jul08 ?        00:00:00 [scsi_eh_0]
root        41     2  0 Jul08 ?        00:00:00 [sync_supers]
root       741     2  0 Jul08 ?        00:00:00 [ttm_swap]
root       100     2  0 Jul08 ?        00:00:00 [usb-storage]
root        15     2  0 Jul08 ?        00:00:00 [watchdog/2]
root      1394     1  0 Jul08 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1404     1  0 Jul08 ?        00:00:00 atd
root      1405     1  0 Jul08 ?        00:00:00 cron
root      1348     1  0 Jul08 ?        00:00:08 nmbd -D
syslog    1310     1  0 Jul08 ?        00:00:06 rsyslogd -c5
root     22590     1  0 11:05 ?        00:00:00 sendmail: MTA: accepting connections
root     21531 20057  0 10:48 ?        00:00:00 smbd -F
lp       17690 17687  0 10:00 ?        00:00:00 socket://192.168.1.89:9100 31734 mmp3 (stdin) 1 finishings=3 number-up=1 job-uuid=urn:uuid:09378196-98c8-33c5-445f-2521ac6e3f81 job-originating-host-name=localhost time-at-creation=1389633752 time-at-proce
root      9028  2275  0 08:19 pts/2    00:00:00 top
root       447     1  0 Jul08 ?        00:00:01 upstart-udev-bridge --daemon[/FONT][/SIZE]

---

### Post by bab1 on 2015-07-09
> **ssexton said:**
> The following four files are being filled with "B"s until the /run/lock partition is full.  This is causing users to lose connection to the Samba shares.
  connections.tdb
  sessionid.tdb
  locking.tdb
  messages.tdb
What can be causing this, a virus?
How can I tell what process is causing this?


I don't think this is a virus.  

I'm running both Ubuntu 12.04 and 14.04 Samba servers.  Neither store the tdb's you listed at the location you show.  What distro and version of Linux are you using?  How did you install Samba?  What is the Samba server being used as (AD-DC or standalone file server)?

---

### Post by ssexton on 2015-07-09
Ubuntu 12.04.  Standalone server.  Server was setup years ago, so do not remember.
Where are the TDB files normally?

---

### Post by ssexton on 2015-07-09
We made a copy of the TDB files in this directory and tried the following:

Stopped smbd removed the large TDB files
Started smbd
The files would just get large again.

Stopped smbd removed all TDB file but printer_list.tdb
Rebooted server
So far (30min) we are OK, knocking on anything around me.

I would like to increase the size of /run/lock from 5M to 50M.  Can you guide me to the correct file?

---

### Post by bab1 on 2015-07-09
> **ssexton said:**
> Ubuntu 12.04.  Standalone server.  Server was setup years ago, so do not remember.
Where are the TDB files normally?
They are at /run/samba

```
ls -l /run/samba
total 484
-rw-r--r-- 1 root root  40200 Jul  9 10:23 brlock.tdb
-rw-r--r-- 1 root root 114688 Jul  9 10:30 connections.tdb
-rw-r--r-- 1 root root    696 Jul  9 10:23 gencache_notrans.tdb
-rw-r--r-- 1 root root    696 Jul  9 10:23 gencache.tdb
-rw-r--r-- 1 root root  77824 Jul  9 10:30 locking.tdb
-rw------- 1 root root  12288 Jul  9 10:28 messages.tdb
-rw-r--r-- 1 root root      5 Jul  9 10:23 nmbd.pid
-rw-r--r-- 1 root root    696 Jul  9 10:23 notify_onelevel.tdb
-rw-r--r-- 1 root root    696 Jul  9 10:23 notify.tdb
-rw-r--r-- 1 root root  12288 Jul  9 10:23 printer_list.tdb
-rw-r--r-- 1 root root   8192 Jul  9 10:30 serverid.tdb
-rw-r--r-- 1 root root 204800 Jul  9 10:30 sessionid.tdb
-rw-r--r-- 1 root root      5 Jul  9 10:23 smbd.pid
srwxrwxrwx 1 root root      0 Jul  9 10:23 unexpected

```

Maybe this will help: [https://lists.samba.org/archive/samba/2013-August/175075.html]("https://lists.samba.org/archive/samba/2013-August/175075.html")

---

