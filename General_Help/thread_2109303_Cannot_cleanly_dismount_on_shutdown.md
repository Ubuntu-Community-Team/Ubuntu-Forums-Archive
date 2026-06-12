---
title: "Cannot cleanly dismount on shutdown"
date: 2013-01-27
forum: General Help
---

### Post by myownrequiem on 2013-01-27
**Edit:** This bug has been reported, and hopefully on the way to being fixed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433?comments=all)

Since about one week ago, Kubuntu (Quantal, x86_64) is failing to cleanly dismount my partition(s) on shutdown.
The messages on shutdown go too quickly to read, but I can make out "umount2", "device or resource busy", and a red "[Fail]".  This happens every time, and on every boot there is a delay while the journal is recovered:

```
Scanning for Btrfs filesystems
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda2: clean, 388855/4833280 files, 3235736/19318162 blocks
/dev/sda3: recovering journal
/dev/sda3: Clearing orphaned inode 105186607 (uid=1000, gid=1000, mode=0100644, size=20)
/dev/sda3: Clearing orphaned inode 105186045 (uid=1000, gid=1000, mode=0100600, size=3449)
/dev/sda3: Clearing orphaned inode 105185554 (uid=1000, gid=1000, mode=0100644, size=20)
/dev/sda3: clean, 556382/163889152 files, 189331898/327752105 blocks
```

sda2 is my root partition and sda3 is /home.  They're formatted with EXT-4 and EXT-3, respectively.

I ran fsck from a live CD, and so far, I've had no actual damage to the filesystem, but this must have the potential to cause it.

My symptoms are similar to this bug: [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639)
I took the advice about adding "lsof > /openfiles.txt" to the top of /etc/init.d/umountroot, and it typically gives me the following:

```
COMMAND     PID   USER   FD      TYPE             DEVICE SIZE/OFF    NODE NAME
init          1   root  cwd       DIR                8,2     4096       2 /
init          1   root  rtd       DIR                8,2     4096       2 /
init          1   root  txt       REG                8,2   163144  393274 /sbin/init
init          1   root  mem       REG                8,2    52152 1838742 /lib/x86_64-linux-gnu/libnss_files-2.15.so
init          1   root  mem       REG                8,2    47712 1838746 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
init          1   root  mem       REG                8,2    97272 1838736 /lib/x86_64-linux-gnu/libnsl-2.15.so
init          1   root  mem       REG                8,2    35712 1838738 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
init          1   root  mem       REG                8,2   135398 1838773 /lib/x86_64-linux-gnu/libpthread-2.15.so
init          1   root  mem       REG                8,2  1811160 1838677 /lib/x86_64-linux-gnu/libc-2.15.so
init          1   root  mem       REG                8,2    31784 1838781 /lib/x86_64-linux-gnu/librt-2.15.so
init          1   root  mem       REG                8,2   277448 1838689 /lib/x86_64-linux-gnu/libdbus-1.so.3.7.2
init          1   root  mem       REG                8,2    38920 1838729 /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
init          1   root  mem       REG                8,2    96280 1838731 /lib/x86_64-linux-gnu/libnih.so.1.0.0
init          1   root  mem       REG                8,2   149312 1838653 /lib/x86_64-linux-gnu/ld-2.15.so
init          1   root    0u      CHR                1,3      0t0    5901 /dev/null
init          1   root    1u      CHR                1,3      0t0    5901 /dev/null
init          1   root    2u      CHR                1,3      0t0    5901 /dev/null
init          1   root    3r     FIFO                0,8      0t0    6624 pipe
init          1   root    4w     FIFO                0,8      0t0    6624 pipe
init          1   root    5r     0000                0,9        0    5876 anon_inode
init          1   root    6r     0000                0,9        0    5876 anon_inode
init          1   root    7u     unix 0xffff8801c1f54000      0t0    6625 @/com/ubuntu/upstart
kthreadd      2   root  cwd       DIR                8,2     4096       2 /
kthreadd      2   root  rtd       DIR                8,2     4096       2 /
kthreadd      2   root  txt   unknown                                     /proc/2/exe
ksoftirqd     3   root  cwd       DIR                8,2     4096       2 /
ksoftirqd     3   root  rtd       DIR                8,2     4096       2 /
ksoftirqd     3   root  txt   unknown                                     /proc/3/exe
migration     6   root  cwd       DIR                8,2     4096       2 /
migration     6   root  rtd       DIR                8,2     4096       2 /
migration     6   root  txt   unknown                                     /proc/6/exe
watchdog/     7   root  cwd       DIR                8,2     4096       2 /
watchdog/     7   root  rtd       DIR                8,2     4096       2 /
watchdog/     7   root  txt   unknown                                     /proc/7/exe
migration     8   root  cwd       DIR                8,2     4096       2 /
migration     8   root  rtd       DIR                8,2     4096       2 /
migration     8   root  txt   unknown                                     /proc/8/exe
ksoftirqd    10   root  cwd       DIR                8,2     4096       2 /
ksoftirqd    10   root  rtd       DIR                8,2     4096       2 /
ksoftirqd    10   root  txt   unknown                                     /proc/10/exe
watchdog/    11   root  cwd       DIR                8,2     4096       2 /
watchdog/    11   root  rtd       DIR                8,2     4096       2 /
watchdog/    11   root  txt   unknown                                     /proc/11/exe
cpuset       12   root  cwd       DIR                8,2     4096       2 /
cpuset       12   root  rtd       DIR                8,2     4096       2 /
cpuset       12   root  txt   unknown                                     /proc/12/exe
khelper      13   root  cwd       DIR                8,2     4096       2 /
khelper      13   root  rtd       DIR                8,2     4096       2 /
khelper      13   root  txt   unknown                                     /proc/13/exe
kdevtmpfs    14   root  cwd       DIR                0,5     4220       3 /
kdevtmpfs    14   root  rtd       DIR                0,5     4220       3 /
kdevtmpfs    14   root  txt   unknown                                     /proc/14/exe
netns        15   root  cwd       DIR                8,2     4096       2 /
netns        15   root  rtd       DIR                8,2     4096       2 /
netns        15   root  txt   unknown                                     /proc/15/exe
sync_supe    17   root  cwd       DIR                8,2     4096       2 /
sync_supe    17   root  rtd       DIR                8,2     4096       2 /
sync_supe    17   root  txt   unknown                                     /proc/17/exe
bdi-defau    18   root  cwd       DIR                8,2     4096       2 /
bdi-defau    18   root  rtd       DIR                8,2     4096       2 /
bdi-defau    18   root  txt   unknown                                     /proc/18/exe
kintegrit    19   root  cwd       DIR                8,2     4096       2 /
kintegrit    19   root  rtd       DIR                8,2     4096       2 /
kintegrit    19   root  txt   unknown                                     /proc/19/exe
kblockd      20   root  cwd       DIR                8,2     4096       2 /
kblockd      20   root  rtd       DIR                8,2     4096       2 /
kblockd      20   root  txt   unknown                                     /proc/20/exe
ata_sff      21   root  cwd       DIR                8,2     4096       2 /
ata_sff      21   root  rtd       DIR                8,2     4096       2 /
ata_sff      21   root  txt   unknown                                     /proc/21/exe
khubd        22   root  cwd       DIR                8,2     4096       2 /
khubd        22   root  rtd       DIR                8,2     4096       2 /
khubd        22   root  txt   unknown                                     /proc/22/exe
md           23   root  cwd       DIR                8,2     4096       2 /
md           23   root  rtd       DIR                8,2     4096       2 /
md           23   root  txt   unknown                                     /proc/23/exe
khungtask    26   root  cwd       DIR                8,2     4096       2 /
khungtask    26   root  rtd       DIR                8,2     4096       2 /
khungtask    26   root  txt   unknown                                     /proc/26/exe
kswapd0      27   root  cwd       DIR                8,2     4096       2 /
kswapd0      27   root  rtd       DIR                8,2     4096       2 /
kswapd0      27   root  txt   unknown                                     /proc/27/exe
ksmd         28   root  cwd       DIR                8,2     4096       2 /
ksmd         28   root  rtd       DIR                8,2     4096       2 /
ksmd         28   root  txt   unknown                                     /proc/28/exe
khugepage    29   root  cwd       DIR                8,2     4096       2 /
khugepage    29   root  rtd       DIR                8,2     4096       2 /
khugepage    29   root  txt   unknown                                     /proc/29/exe
fsnotify_    30   root  cwd       DIR                8,2     4096       2 /
fsnotify_    30   root  rtd       DIR                8,2     4096       2 /
fsnotify_    30   root  txt   unknown                                     /proc/30/exe
ecryptfs-    31   root  cwd       DIR                8,2     4096       2 /
ecryptfs-    31   root  rtd       DIR                8,2     4096       2 /
ecryptfs-    31   root  txt   unknown                                     /proc/31/exe
crypto       32   root  cwd       DIR                8,2     4096       2 /
crypto       32   root  rtd       DIR                8,2     4096       2 /
crypto       32   root  txt   unknown                                     /proc/32/exe
kthrotld     41   root  cwd       DIR                8,2     4096       2 /
kthrotld     41   root  rtd       DIR                8,2     4096       2 /
kthrotld     41   root  txt   unknown                                     /proc/41/exe
binder       42   root  cwd       DIR                8,2     4096       2 /
binder       42   root  rtd       DIR                8,2     4096       2 /
binder       42   root  txt   unknown                                     /proc/42/exe
deferwq      61   root  cwd       DIR                8,2     4096       2 /
deferwq      61   root  rtd       DIR                8,2     4096       2 /
deferwq      61   root  txt   unknown                                     /proc/61/exe
charger_m    62   root  cwd       DIR                8,2     4096       2 /
charger_m    62   root  rtd       DIR                8,2     4096       2 /
charger_m    62   root  txt   unknown                                     /proc/62/exe
devfreq_w    63   root  cwd       DIR                8,2     4096       2 /
devfreq_w    63   root  rtd       DIR                8,2     4096       2 /
devfreq_w    63   root  txt   unknown                                     /proc/63/exe
scsi_eh_0   178   root  cwd       DIR                8,2     4096       2 /
scsi_eh_0   178   root  rtd       DIR                8,2     4096       2 /
scsi_eh_0   178   root  txt   unknown                                     /proc/178/exe
scsi_eh_1   181   root  cwd       DIR                8,2     4096       2 /
scsi_eh_1   181   root  rtd       DIR                8,2     4096       2 /
scsi_eh_1   181   root  txt   unknown                                     /proc/181/exe
scsi_eh_2   183   root  cwd       DIR                8,2     4096       2 /
scsi_eh_2   183   root  rtd       DIR                8,2     4096       2 /
scsi_eh_2   183   root  txt   unknown                                     /proc/183/exe
scsi_eh_3   185   root  cwd       DIR                8,2     4096       2 /
scsi_eh_3   185   root  rtd       DIR                8,2     4096       2 /
scsi_eh_3   185   root  txt   unknown                                     /proc/185/exe
scsi_eh_4   186   root  cwd       DIR                8,2     4096       2 /
scsi_eh_4   186   root  rtd       DIR                8,2     4096       2 /
scsi_eh_4   186   root  txt   unknown                                     /proc/186/exe
scsi_eh_5   189   root  cwd       DIR                8,2     4096       2 /
scsi_eh_5   189   root  rtd       DIR                8,2     4096       2 /
scsi_eh_5   189   root  txt   unknown                                     /proc/189/exe
scsi_eh_6   191   root  cwd       DIR                8,2     4096       2 /
scsi_eh_6   191   root  rtd       DIR                8,2     4096       2 /
scsi_eh_6   191   root  txt   unknown                                     /proc/191/exe
scsi_eh_7   193   root  cwd       DIR                8,2     4096       2 /
scsi_eh_7   193   root  rtd       DIR                8,2     4096       2 /
scsi_eh_7   193   root  txt   unknown                                     /proc/193/exe
kworker/u   194   root  cwd       DIR                8,2     4096       2 /
kworker/u   194   root  rtd       DIR                8,2     4096       2 /
kworker/u   194   root  txt   unknown                                     /proc/194/exe
jbd2/sda2   317   root  cwd       DIR                8,2     4096       2 /
jbd2/sda2   317   root  rtd       DIR                8,2     4096       2 /
jbd2/sda2   317   root  txt   unknown                                     /proc/317/exe
ext4-dio-   318   root  cwd       DIR                8,2     4096       2 /
ext4-dio-   318   root  rtd       DIR                8,2     4096       2 /
ext4-dio-   318   root  txt   unknown                                     /proc/318/exe
hd-audio0   784   root  cwd       DIR                8,2     4096       2 /
hd-audio0   784   root  rtd       DIR                8,2     4096       2 /
hd-audio0   784   root  txt   unknown                                     /proc/784/exe
kvm-irqfd   788   root  cwd       DIR                8,2     4096       2 /
kvm-irqfd   788   root  rtd       DIR                8,2     4096       2 /
kvm-irqfd   788   root  txt   unknown                                     /proc/788/exe
flush-8:0   854   root  cwd       DIR                8,2     4096       2 /
flush-8:0   854   root  rtd       DIR                8,2     4096       2 /
flush-8:0   854   root  txt   unknown                                     /proc/854/exe
kjournald   857   root  cwd       DIR                8,2     4096       2 /
kjournald   857   root  rtd       DIR                8,2     4096       2 /
kjournald   857   root  txt   unknown                                     /proc/857/exe
krfcommd    957   root  cwd       DIR                8,2     4096       2 /
krfcommd    957   root  rtd       DIR                8,2     4096       2 /
krfcommd    957   root  txt   unknown                                     /proc/957/exe
dnsmasq    2651 nobody  cwd       DIR                8,2     4096       2 /
dnsmasq    2651 nobody  rtd       DIR                8,2     4096       2 /
dnsmasq    2651 nobody  txt       REG                8,2   253560 3154435 /usr/sbin/dnsmasq
dnsmasq    2651 nobody  mem       REG                8,2    52152 1838742 /lib/x86_64-linux-gnu/libnss_files-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2    47712 1838746 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2    97272 1838736 /lib/x86_64-linux-gnu/libnsl-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2    35712 1838738 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2  2919792 3152429 /usr/lib/locale/locale-archive
dnsmasq    2651 nobody  mem       REG                8,2    26376 3147947 /usr/lib/libnfnetlink.so.0.2.0
dnsmasq    2651 nobody  mem       REG                8,2    31784 1838781 /lib/x86_64-linux-gnu/librt-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2   135398 1838773 /lib/x86_64-linux-gnu/libpthread-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2  1811160 1838677 /lib/x86_64-linux-gnu/libc-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2   207096 3154095 /usr/lib/x86_64-linux-gnu/libidn.so.11.6.8
dnsmasq    2651 nobody  mem       REG                8,2    92016 3154164 /usr/lib/x86_64-linux-gnu/libnetfilter_conntrack.so.3.3.0
dnsmasq    2651 nobody  mem       REG                8,2   277448 1838689 /lib/x86_64-linux-gnu/libdbus-1.so.3.7.2
dnsmasq    2651 nobody  mem       REG                8,2   149312 1838653 /lib/x86_64-linux-gnu/ld-2.15.so
dnsmasq    2651 nobody  mem       REG                8,2    26258 3280973 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
dnsmasq    2651 nobody  mem       REG                8,2      486 3418563 /usr/share/locale-langpack/en_GB/LC_MESSAGES/dnsmasq.mo
dnsmasq    2651 nobody    0u      CHR                1,3      0t0    5901 /dev/null
dnsmasq    2651 nobody    1u      CHR                1,3      0t0    5901 /dev/null
dnsmasq    2651 nobody    2u      CHR                1,3      0t0    5901 /dev/null
dnsmasq    2651 nobody    3u  netlink                         0t0   14073 ROUTE
dnsmasq    2651 nobody    4u     IPv4              14078      0t0     UDP Jenova:domain 
dnsmasq    2651 nobody    5u     IPv4              14079      0t0     TCP Jenova:domain (LISTEN)
dnsmasq    2651 nobody    7r     FIFO                0,8      0t0   14353 pipe
dnsmasq    2651 nobody    8w     FIFO                0,8      0t0   14353 pipe
dnsmasq    2651 nobody    9u     unix 0xffff8801a4d7b740      0t0   14355 socket
kworker/u  2999   root  cwd       DIR                8,2     4096       2 /
kworker/u  2999   root  rtd       DIR                8,2     4096       2 /
kworker/u  2999   root  txt   unknown                                     /proc/2999/exe
kworker/1 10205   root  cwd       DIR                8,2     4096       2 /
kworker/1 10205   root  rtd       DIR                8,2     4096       2 /
kworker/1 10205   root  txt   unknown                                     /proc/10205/exe
kworker/1 10488   root  cwd       DIR                8,2     4096       2 /
kworker/1 10488   root  rtd       DIR                8,2     4096       2 /
kworker/1 10488   root  txt   unknown                                     /proc/10488/exe
kworker/0 12204   root  cwd       DIR                8,2     4096       2 /
kworker/0 12204   root  rtd       DIR                8,2     4096       2 /
kworker/0 12204   root  txt   unknown                                     /proc/12204/exe
kworker/0 12488   root  cwd       DIR                8,2     4096       2 /
kworker/0 12488   root  rtd       DIR                8,2     4096       2 /
kworker/0 12488   root  txt   unknown                                     /proc/12488/exe
kworker/0 12912   root  cwd       DIR                8,2     4096       2 /
kworker/0 12912   root  rtd       DIR                8,2     4096       2 /
kworker/0 12912   root  txt   unknown                                     /proc/12912/exe
rc        13846   root  cwd       DIR                8,2     4096       2 /
rc        13846   root  rtd       DIR                8,2     4096       2 /
rc        13846   root  txt       REG                8,2   105712  262177 /bin/dash
rc        13846   root  mem       REG                8,2  1811160 1838677 /lib/x86_64-linux-gnu/libc-2.15.so
rc        13846   root  mem       REG                8,2   149312 1838653 /lib/x86_64-linux-gnu/ld-2.15.so
rc        13846   root    0u      CHR                5,1      0t0    5910 /dev/console
rc        13846   root    1u      CHR                5,1      0t0    5910 /dev/console
rc        13846   root    2u      CHR                5,1      0t0    5910 /dev/console
rc        13846   root   10r      REG                8,2     8635  132495 /etc/init.d/rc
S60umount 14016   root  cwd       DIR                8,2     4096       2 /
S60umount 14016   root  rtd       DIR                8,2     4096       2 /
S60umount 14016   root  txt       REG                8,2   105712  262177 /bin/dash
S60umount 14016   root  mem       REG                8,2  1811160 1838677 /lib/x86_64-linux-gnu/libc-2.15.so
S60umount 14016   root  mem       REG                8,2   149312 1838653 /lib/x86_64-linux-gnu/ld-2.15.so
S60umount 14016   root    0u      CHR                5,1      0t0    5910 /dev/console
S60umount 14016   root    1w      REG                8,2        0      13 /openfiles.txt
S60umount 14016   root    2u      CHR                5,1      0t0    5910 /dev/console
S60umount 14016   root   10r      REG                8,2     3047  132521 /etc/init.d/umountroot
S60umount 14016   root   11u      CHR                5,1      0t0    5910 /dev/console
lsof      14019   root  cwd       DIR                8,2     4096       2 /
lsof      14019   root  rtd       DIR                8,2     4096       2 /
lsof      14019   root  txt       REG                8,2   163224 3146446 /usr/bin/lsof
lsof      14019   root  mem       REG                8,2  1811160 1838677 /lib/x86_64-linux-gnu/libc-2.15.so
lsof      14019   root  mem       REG                8,2   149312 1838653 /lib/x86_64-linux-gnu/ld-2.15.so
lsof      14019   root    0u      CHR                5,1      0t0    5910 /dev/console
lsof      14019   root    1w      REG                8,2        0      13 /openfiles.txt
lsof      14019   root    2u      CHR                5,1      0t0    5910 /dev/console
lsof      14019   root    3r      DIR                0,3        0       1 /proc
lsof      14019   root    4r      DIR                0,3        0   72697 /proc/14019/fd
lsof      14019   root    5w     FIFO                0,8      0t0   72702 pipe
lsof      14019   root    6r     FIFO                0,8      0t0   72703 pipe
lsof      14020   root  cwd       DIR                8,2     4096       2 /
lsof      14020   root  rtd       DIR                8,2     4096       2 /
lsof      14020   root  txt       REG                8,2   163224 3146446 /usr/bin/lsof
lsof      14020   root  mem       REG                8,2  1811160 1838677 /lib/x86_64-linux-gnu/libc-2.15.so
lsof      14020   root  mem       REG                8,2   149312 1838653 /lib/x86_64-linux-gnu/ld-2.15.so
lsof      14020   root    4r     FIFO                0,8      0t0   72702 pipe
lsof      14020   root    7w     FIFO                0,8      0t0   72703 pipe
```

"lsof /home" gives no output at all, which seems strange given that it appears not to be dismounting cleanly.

None of the workarounds in that thread work for me.  I tried disabling the network, stopping a bunch of services, logging out, killing Xorg and shutting down from tty1, but I still see "device or resource busy" every time.

It's possible that this problem started with my upgrade to kernel 3.5.0.22.28, but I didn't notice anything wrong until a few days afterwards.

Does anyone have any suggestions?

---

