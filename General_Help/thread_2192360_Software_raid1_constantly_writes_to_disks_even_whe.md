---
title: "Software raid1 constantly writes to disks even when idle"
date: 2013-12-07
forum: General Help
---

### Post by hier on 2013-12-07
I am running a software raid1 with two disks in a small home server. Since I want to save power, I would like it to spin down its disks as much as possible. Therefore I have added a SSD cache with bcache and configured it to delay writes for a long time. As a result, the system barely reads and writes from/to /dev/md0 (the backing device of the bcache set). Before upgrading to Ubuntu 13.10, this also resulted in rare reads/writes from/to /dev/sdb and /dev/sdc (which hold the partitions the raid is built on), so the disks could shut down for almost the entire day. After I upgraded, this changed. bcache still catches most reads and writes, so /dev/md0 is idle most of the time. Nevertheless the system writes twice per minute (most of the time exactly) to /dev/sdb1 and /dev/sdb2, so the disks cannot spin down any more.

I might have accidentally overwritten a few too many config files with the package defaults while upgrading and I recall having this problem already a very long time ago. Unfortunately I do not remember how I solved it (or even if I solved it, since I used btrfs for mirroring until I started using bcache a while ago). I already tried disabling the mdadm demon to exclude its monitoring doesn't create this problem.

I am running a x86_64 Ubuntu on an Intel Atom 330 CPU, in case this matters. I am monitoring disk reads and writes via /sys/block/.../stat with a small php script once per minute (I use this script also to shut down the idle hard drives, since I want more control).

Thank you very much in advance for any help!
Martin

---

### Post by SaturnusDJ on 2013-12-07
Maybe start with posting a list of running processes etc.

---

### Post by hier on 2013-12-08
Here is the list of processes:

```
mhier@tartaros:~$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:07 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [ksoftirqd/0]
    5 ?        S<     0:00 [kworker/0:0H]
    7 ?        S      0:00 [migration/0]
    8 ?        S      0:00 [rcu_bh]
    9 ?        S      0:00 [rcuob/0]
   10 ?        S      0:00 [rcuob/1]
   11 ?        S      0:00 [rcuob/2]
   12 ?        S      0:00 [rcuob/3]
   13 ?        S      0:14 [rcu_sched]
   14 ?        S      0:03 [rcuos/0]
   15 ?        S      0:03 [rcuos/1]
   16 ?        S      0:03 [rcuos/2]
   17 ?        S      0:03 [rcuos/3]
   18 ?        S      0:00 [watchdog/0]
   19 ?        S      0:00 [watchdog/1]
   20 ?        S      0:00 [migration/1]
   21 ?        S      0:00 [ksoftirqd/1]
   23 ?        S<     0:00 [kworker/1:0H]
   24 ?        S      0:00 [watchdog/2]
   25 ?        S      0:00 [migration/2]
   26 ?        S      0:00 [ksoftirqd/2]
   27 ?        S      0:00 [kworker/2:0]
   28 ?        S<     0:00 [kworker/2:0H]
   29 ?        S      0:00 [watchdog/3]
   30 ?        S      0:00 [migration/3]
   31 ?        S      0:00 [ksoftirqd/3]
   33 ?        S<     0:00 [kworker/3:0H]
   34 ?        S<     0:00 [khelper]
   35 ?        S      0:00 [kdevtmpfs]
   36 ?        S<     0:00 [netns]
   37 ?        S<     0:00 [writeback]
   38 ?        S<     0:00 [kintegrityd]
   39 ?        S<     0:00 [bioset]
   41 ?        S<     0:00 [kblockd]
   42 ?        S<     0:00 [ata_sff]
   43 ?        S      0:00 [khubd]
   44 ?        S<     0:00 [md]
   45 ?        S<     0:00 [devfreq_wq]
   48 ?        S      0:01 [kworker/2:1]
   49 ?        S      0:01 [kworker/3:1]
   50 ?        S      0:00 [khungtaskd]
   51 ?        S      0:03 [kswapd0]
   52 ?        SN     0:00 [ksmd]
   53 ?        S      0:00 [fsnotify_mark]
   54 ?        S      0:00 [ecryptfs-kthrea]
   55 ?        S<     0:00 [crypto]
   67 ?        S<     0:00 [kthrotld]
   69 ?        S      0:00 [scsi_eh_0]
   70 ?        S      0:00 [scsi_eh_1]
   72 ?        S      0:00 [scsi_eh_2]
   73 ?        S      0:00 [scsi_eh_3]
   95 ?        S<     0:00 [deferwq]
   96 ?        S<     0:00 [charger_manager]
  153 ?        S      0:00 [scsi_eh_4]
  155 ?        S      0:00 [scsi_eh_5]
  156 ?        S      0:00 [scsi_eh_6]
  213 ?        S<     0:00 [bcache]
  214 ?        S<     0:00 [bch_btree_gc]
  215 ?        S<     0:00 [bch_btree_io]
  216 ?        S<     0:00 [bcache_writebac]
  217 ?        S<     0:00 [bioset]
  218 ?        S<     0:00 [bioset]
  243 ?        S<     0:00 [bioset]
  245 ?        S      0:00 [bcache_allocato]
  266 ?        S<     0:00 [bioset]
  267 ?        S      0:00 [md0_raid1]
  273 ?        S<     0:00 [bioset]
  274 ?        S<     0:00 [bioset]
  287 ?        S      0:02 [jbd2/sda1-8]
  288 ?        S<     0:00 [ext4-rsv-conver]
  289 ?        S<     0:00 [ext4-unrsv-conv]
  322 ?        S      0:05 @sbin/plymouthd --mode=boot --attach-to-session
  332 ?        S      0:00 [kworker/u8:1]
  488 ?        S      0:01 upstart-udev-bridge --daemon
  497 ?        Ss     0:00 /lib/systemd/systemd-udevd --daemon
  504 ?        S      0:00 [jbd2/bcache0-8]
  507 ?        S<     0:00 [ext4-rsv-conver]
  508 ?        S<     0:00 [ext4-unrsv-conv]
  557 ?        S<     0:00 [rpciod]
  560 ?        S<     0:00 [nfsiod]
  623 ?        S<     0:00 [kpsmoused]
  632 ?        Ss     0:00 rpc.idmapd
  641 ?        Ss     0:08 dbus-daemon --system --fork
  666 ?        Ss     0:08 plymouth-upstart-bridge
  746 ?        Ss     0:02 /lib/systemd/systemd-logind
  756 ?        Ss     0:00 /usr/sbin/bluetoothd
  800 ?        Sl     0:05 rsyslogd -c5
  808 ?        S<     0:00 [krfcommd]
  861 ?        S      0:01 avahi-daemon: running [tartaros.local]
  870 ?        S      0:00 avahi-daemon: chroot helper
 1106 ?        Ss     0:00 /usr/sbin/cups-browsed
 1147 ?        S<     0:00 [hd-audio0]
 1383 ?        Ss     0:00 /usr/sbin/winbindd -F
 1388 ?        Ss     0:00 smbd -F
 1401 ?        Ss     0:01 nmbd -D
 1402 ?        S      0:00 smbd -F
 1416 ?        S      0:00 /usr/sbin/winbindd -F
 1450 ?        Ss     0:00 rpcbind
 1486 ?        Ss     0:00 rpc.statd -L
 1504 ?        Ss     0:06 /usr/bin/perl -wT /usr/sbin/munin-node
 1590 ?        S      0:00 upstart-socket-bridge --daemon
 1614 ?        S      0:00 upstart-file-bridge --daemon
 1657 ?        Ss     0:01 dhclient -1 -v -pf /run/dhclient.eth0.222.pid -lf /var/lib/dhcp/dhclient.eth0.222.leases eth0.222
 1782 ?        Ss     0:01 /usr/sbin/modem-manager
 1831 ?        Ssl    0:04 NetworkManager
 1847 ?        Sl     0:02 /usr/lib/policykit-1/polkitd --no-debug
 1949 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
 1960 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
 1979 ?        Ssl    0:05 /usr/sbin/named -u bind
 1989 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
 1990 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
 1996 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
 2071 ?        Ss     0:00 /usr/sbin/sshd -D
 2083 ?        Ss     0:00 dhcpd -user dhcpd -group dhcpd -f -q -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf eth0
 2106 ?        Ss     0:00 /usr/sbin/dovecot -F -c /etc/dovecot/dovecot.conf
 2137 ?        Ss     0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
 2138 ?        Ss     0:00 atd
 2140 ?        Ss     0:01 cron
 2147 ?        Ssl    0:08 whoopsie
 2205 ?        Ss     0:42 /usr/sbin/irqbalance
 2213 ?        Sl     0:01 /usr/sbin/libvirtd -d
 2267 ?        Ssl    4:13 /usr/sbin/mysqld
 2390 ?        Ss     0:00 /usr/sbin/openvpn --writepid /var/run/openvpn.server.pid --daemon ovpn-server --cd /etc/openvpn --config /etc/openvpn/server.conf --script-security 2
 2713 ?        Ss     3:21 /usr/bin/freshclam -d --quiet
 2736 ?        Rsl  183:35 /usr/bin/minidlna -f /etc/minidlna.conf -P /run/minidlna/minidlna.pid
 2818 ?        S<     0:00 [nfsd4]
 2824 ?        S<     0:00 [nfsd4_callbacks]
 2825 ?        S      0:00 [lockd]
 2836 ?        S      0:00 [nfsd]
 2837 ?        S      0:00 [nfsd]
 2840 ?        S      0:00 [nfsd]
 2842 ?        S      0:00 [nfsd]
 2843 ?        S      0:00 [nfsd]
 2844 ?        S      0:00 [nfsd]
 2845 ?        S      0:00 [nfsd]
 2846 ?        S      0:00 [nfsd]
 2895 ?        Ss     0:00 /usr/sbin/rpc.mountd --manage-gids
 2916 ?        S      0:00 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf
 2929 ?        Sl     0:00 /usr/sbin/osspd -f -f
 3087 ?        Ss     0:00 /usr/lib/postfix/master
 3093 ?        S      0:00 qmgr -l -t fifo -u
 3118 ?        Ss     0:00 /usr/bin/rootd
 3149 ?        S      0:00 /usr/sbin/xrdp
 3151 ?        S      0:00 /usr/sbin/xrdp-sesman
 3341 ?        Ss     0:04 /usr/sbin/apache2 -k start
 3606 ?        S      0:00 dovecot/anvil
 3607 ?        S      0:00 dovecot/log
 3610 ?        S      0:00 dovecot/config
 3851 ?        Sl     0:15 /usr/bin/python /data/system/usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock -p /var/run/fail2ban/fail2ban.pid
 4070 ?        Ss     0:15 /usr/bin/fetchmail -f /etc/fetchmailrc --pidfile /var/run/fetchmail/fetchmail.pid --syslog
 4281 ?        S      0:00 [kworker/3:2]
 4284 ?        Ss     0:00 SCREEN -mdS asterisk /usr/local/sbin/start-asterisk.sh
 4286 pts/1    Ss+    0:00 /bin/sh /usr/local/sbin/start-asterisk.sh
 4406 ?        Ss     0:00 SCREEN -mdS sleepdisks /usr/local/sbin/sleep-disks.php
 4408 pts/4    Ss+    0:09 /usr/bin/php /usr/local/sbin/sleep-disks.php
 4421 ?        Ss     0:00 /usr/bin/xdm
 4426 tty7     Ssl+   0:04 /usr/bin/X :0 vt7 -nolisten tcp -auth /var/lib/xdm/authdir/authfiles/A:0-mpJlI2
 4436 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
 4437 ttyS0    Ss+    0:00 /sbin/getty -L 9600 ttyS0 vt102
 4462 ?        Ss     0:00 -:0         
 4496 ?        Ss     0:07 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 124:136
 4514 ?        S      0:00 [kauditd]
 4535 ?        Ss     0:00 SCREEN -mdS x11vnc x11vnc -display :0 -auth guess -rfbauth /root/.vnc/passwd -ncache_cr -ncache 10 -loop
 4536 pts/5    Ss+    0:00 x11vnc -display :0 -auth guess -rfbauth /root/.vnc/passwd -ncache_cr -ncache 10 -loop
 4544 pts/5    S+     0:49 x11vnc -display :0 -auth guess -rfbauth /root/.vnc/passwd -ncache_cr -ncache 10 -loop
 4557 ?        Sl     0:09 /usr/sbin/console-kit-daemon --no-daemon
 5367 ?        S      0:00 /usr/sbin/winbindd -F
 5965 pts/1    Sl+    0:15 asterisk -f
 6054 ?        S      0:01 /usr/sbin/apache2 -k start
 6060 ?        S      0:02 /usr/sbin/apache2 -k start
 6061 ?        S      0:02 /usr/sbin/apache2 -k start
 6062 ?        S      0:04 /usr/sbin/apache2 -k start
 6066 ?        S      0:01 /usr/sbin/apache2 -k start
 6149 ?        Ss     0:00 /usr/sbin/cupsd -F
 6190 ?        S      0:04 /usr/sbin/apache2 -k start
 6686 ?        S      0:02 [kworker/0:44]
 8396 ?        S      0:00 [kworker/u8:2]
 8707 ?        S      0:01 /usr/sbin/apache2 -k start
 9321 ?        S      0:00 pickup -l -t fifo -u -c
 9935 ?        Ss     0:00 SCREEN
 9936 pts/9    Ss+    0:00 /bin/bash
 9959 ?        S      0:03 [kworker/1:0]
10424 ?        S<     0:00 [kworker/u9:0]
10437 ?        S      0:00 /usr/sbin/apache2 -k start
10438 ?        S      0:00 /usr/sbin/apache2 -k start
10448 ?        S      0:00 /usr/sbin/apache2 -k start
11356 ?        S<     0:00 [kworker/u9:2]
11383 ?        S      0:00 [kworker/1:1]
11667 ?        S<     0:00 [kworker/u9:1]
11691 ?        S      0:00 [kworker/1:2]
11848 ?        Ss     0:00 sshd: mhier [priv]  
11933 ?        S      0:00 sshd: mhier@pts/6   
11948 pts/6    Ss     0:00 -bash
12066 ?        Ss     0:00 sshd: mhier [priv]  
12070 ?        S      0:00 sh -c /usr/bin/env -i PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin run-parts --lsbsysinit /etc/update-motd.d > /run/motd.dynamic.ne
12071 ?        S      0:00 run-parts --lsbsysinit /etc/update-motd.d
12079 ?        S      0:00 /bin/sh /etc/update-motd.d/50-landscape-sysinfo
12086 ?        R      0:00 /usr/bin/python /usr/bin/landscape-sysinfo
12087 pts/6    R+     0:00 ps ax
17540 ?        S      0:00 [kworker/0:0]
24502 ?        S      0:00 tlsmgr -l -t unix -u -c
mhier@tartaros:~$ 
```

I also tried finding out which processes are writing to disk using iotop, but it also shows the writes going to the cache, so it's essentially unusable for this problem. Or is there any way of finding out per-process writes on the device level?

---

### Post by SaturnusDJ on 2013-12-08
Did you apply the dirty writeback centisecs tweak or is data intercepted before this?

---

### Post by hier on 2013-12-08
Well, I have tried enabling the laptop mode, which enables this tweak as well afaik. But this should affect only writing to the file systems, right? In my case, the file system is located on /dev/bcache0. /dev/md0 is the backing device, there no writes are arriving, since they are caught by bcache.

But I have found another hint: I now tried using the old kernel 3.10.2, which I compiled for Ubuntu 13.4 to have bcache support. Running this kernel, I do not have those writes and my hard drives do shut down after the time out. So it must be something inside the kernel, either the configuration or one of the Ubuntu patches (my custom kernel is vanilla).

I have uploaded the diff between the kernel configs here (sorry, for some reason I cannot upload it as an attachment):
[http://pool.beta-centauri.de/get.php?id=84&key=160901ab6c0b73753d757a5fe1e54ef0](http://pool.beta-centauri.de/get.php?id=84&key=160901ab6c0b73753d757a5fe1e54ef0)

Unfortunately there are many differences (my config was based on the original config of Ubuntu 13.4) and I didn't find a direct suspect. I only noticed that the IO scheduler is "deadline" in the Ubuntu 13.10 kernel and (maybe by my choice) CFQ in my kernel. Can this do such a difference? I didn't find any change w.r.t. block devices (like multi device support)...

Thank you very much for your input!

---

### Post by SaturnusDJ on 2013-12-08
Yeah that was what I was thinking...

Good find on the kernel. My knowledge doesn't go there but will browsing the file I saw that the I/O scheduler might be different. I can't help any further if that isn't the fix.

---

### Post by hier on 2013-12-08
I now tried changing the IO scheduler via sys interface on the default Ubuntu 13.10 kernel, this doesn't help (I still have those writes).

---

### Post by hier on 2013-12-09
I performed another test: I downloaded the kernel sources for the current Ubuntu default kernel and compiled it with the same configuration as my older 3.10 kernel where it worked. Even then I get the same frequent writes and the disks are not spinning down. I begin to suspect one of the Ubuntu patches creates this behaviour... I wonder if I shall create a bug report? Or can I do another test first?

---

### Post by trefmanic on 2014-04-28
This thread is relevant: [http://ubuntuforums.org/showthread.php?t=1917200&page=2](http://ubuntuforums.org/showthread.php?t=1917200&page=2)

I'm posting this so others can google it and because the other thread is closed.

Apparently, this is a normal behaviour when using ext4. I have found an answer in the linux-lvm mailing list here : [http://osdir.com/ml/linux-lvm/2013-06/msg00007.html](http://osdir.com/ml/linux-lvm/2013-06/msg00007.html)

Quote:
> The default for ext4 is to do a lazy initialization of the filesystem  and journal when you create it.  Depending on the size of the file  system this can last for some time.  To prevent this use:
mkfs.ext4 -E lazy_itable_init=0,lazy_journal_init=0

-Greg

---

