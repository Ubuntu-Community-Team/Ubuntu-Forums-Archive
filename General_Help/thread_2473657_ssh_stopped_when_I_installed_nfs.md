---
title: "ssh stopped when I installed nfs"
date: 2022-04-09
forum: General Help
---

### Post by Old Jimma on 2022-04-09
Hello Focal Fosiles:


ssh quit! Here is the situation:

[LIST]
[*]I have a server S that backs up client C using rsync over ssh
[*]computer C serves as an NFS server to computer A that grabs music files from C and plays them in my man cave.
[*]
[/LIST]

Every time I install NFS on C, ssh  to backup files to S from C **STOPS WORKING**.

**GRRR!!**

Why? And how do I fix this?

Very grumpy,
Old Jimma

---

### Post by &amp;KyT$0P# on 2022-04-09
Anything related in syslog or the systemd journal when ssh stops?

> **Old Jimma said:**
> computer C serves as an NFS server to computer A that grabs music files from C and plays them 

Is there a specific reason you need NFS?  If you already have ssh set up, why not use sshfs for this?

---

### Post by TheFu on 2022-04-09
Well, NFS is much faster than sshfs (perhaps 2x) and doesn't have the same limitation as sshfs for certain file system modes. Also, sshfs is single user, whereas NFS is system-wide with all users on the client having the expected access to files on the server based on owner, group, permissions, etc.

Lots of reasons to have both ssh and NFS on the same system.

But without facts - relevant logs, there isn't much we can do. Are any systems wifi connected to the LAN? Is the networking stable?

**rsync** isn't really a backup tool. It is a copy tool.  If you want backups, use a real backup tool that handles versioning.

---

### Post by ActionParsnip on 2022-04-09
> **TheFu said:**
> Well, NFS is much faster than sshfs (perhaps 2x) and doesn't have the same limitation as sshfs for certain file system modes. Also, sshfs is single user, whereas NFS is system-wide with all users on the client having the expected access to files on the server based on owner, group, permissions, etc.

Lots of reasons to have both ssh and NFS on the same system.

But without facts - relevant logs, there isn't much we can do. Are any systems wifi connected to the LAN? Is the networking stable?

**rsync** isn't really a backup tool. It is a copy tool.  If you want backups, use a real backup tool that handles versioning.

What do you mean by "single user" for sshfs? I have multiple systems mounting a cheap USB stick in a file server for temp files. No problem... Can you expand please?

---

### Post by TheFu on 2022-04-09
> **ActionParsnip said:**
> What do you mean by "single user" for sshfs? I have multiple systems mounting a cheap USB stick in a file server for temp files. No problem... Can you expand please?

Can the mount happen before a user is logged in and be available to any user/daemon account in the expected way?

For example, both sides of the storage is ext4. Over an sshfs mount:
```
$ sudo chown rthefu x2h265.sh
chown: cannot access 'x2h265.sh': Permission denied

$ ll x2h265.sh
-rwxrwxr-x 1 thefu thefu 299 Feb 27  2017 x2h265.sh*

```

sshfs isn't the same as NFS on a few levels.

It is a great tool for some specific needs. No doubt.  For example, when I want to access data on a different system over the internet to run programs setup to be run only on my current box.  But it is painfully slow.  Still, that is about the only useful reason to use sshfs when sftp or NFS are both available too.

NFS feels nearly as fast as local HDD storage when used on the same LAN. In some situations, if it even faster.  OTOH, I wouldn't use NFS over the internet ... well ... I have, but only from gatekeeper.dec.com in the early 1990s over a read-only NFS mount.  I needed to setup a complete GNU development environment on a new platform (64-bit CPU architecture) that didn't come with a compiler and had to manually resolve all the dependencies for all the programs and libraries required, including all the normal dev tools that end users know nothing about like ar, nm, bison, flex, .... perhaps 30 others.  Lots of chicken-egg issues.

IMHO.

---

### Post by ActionParsnip on 2022-04-09
> **TheFu said:**
> Can the mount happen before a user is logged in and be available to any user/daemon account in the expected way?

For example, both sides of the storage is ext4. Over an sshfs mount:
```
$ sudo chown rthefu x2h265.sh
chown: cannot access 'x2h265.sh': Permission denied

$ ll x2h265.sh
-rwxrwxr-x 1 thefu thefu 299 Feb 27  2017 x2h265.sh*

```

sshfs isn't the same as NFS on a few levels.

It is a great tool for some specific needs. No doubt.  For example, when I want to access data on a different system over the internet to run programs setup to be run only on my current box.  But it is painfully slow.  Still, that is about the only useful reason to use sshfs when sftp or NFS are both available too.

NFS feels nearly as fast as local HDD storage when used on the same LAN. In some situations, if it even faster.  OTOH, I wouldn't use NFS over the internet ... well ... I have, but only from gatekeeper.dec.com in the early 1990s over a read-only NFS mount.  I needed to setup a complete GNU development environment on a new platform (64-bit CPU architecture) that didn't come with a compiler and had to manually resolve all the dependencies for all the programs and libraries required, including all the normal dev tools that end users know nothing about like ar, nm, bison, flex, .... perhaps 30 others.  Lots of chicken-egg issues.

IMHO.

Yes. I have a script that mounts it using SSH keys. It runs later (using rc.local with a large pause so the network can come up) and it mounts....I'll have a play but I'm still not getting the single user bit.

The speed I don't care about. It is temp text files and gubbins so doesn't need any kind of real speed at any time.

---

### Post by TheFu on 2022-04-09
NFS mounts are system-to-system. For all users, but setup by the admins on both sides.

CIFS and SSHFS mounts are single user-to-system.

How do you unlock the ssh key without logging in?  I'm confused.

---

### Post by ActionParsnip on 2022-04-09
> **TheFu said:**
> NFS mounts are system-to-system. For all users, but setup by the admins on both sides.

CIFS and SSHFS mounts are single user-to-system.

How do you unlock the ssh key without logging in?  I'm confused.

I'll have a play and get back to you. I'll have a look at what is going on

---

### Post by kevdog on 2022-04-10
@TheFu

As you probably know, rsync can keep versioned backups although they are rudimentary. There are probably better tools for the job.

---

### Post by The Cog on 2022-04-10
sshfs as root shoudl be able to backup most of the target machine, if not all of it. The speed may be slower than nfs, I don't know.

I do local backups to a usb btrfs drive occasionally. The top level of the drive contains subvolumes /laptop1, /laptop2, /desktop, /pi. I do an rsync to the appropriate folder, and then make a snapshot. I know that TheFu recommends a "pull" backup rather than giving the target machines the ability to write (and maybe corrupt) the backup media themselves, and that could be done with rsync (as root) from a backup server, but I haven't bothered with that part at home.

---

### Post by Old Jimma on 2022-04-10
Hello Focal Fosiles!

Thank you for your many replies. Applogies for a slow reply: spring here with fluctuating temperatures. I had to cover up my gardens so tonight's frost wouldn't kill them.

Here are some replies and questions:

**QUESTIONS:**

I've been asked for logs. How do I get these logs?


**Why am I using both NFS and ssh?**

I use NFS to share music files from a computer in my man cave to the computer in the kitchen. Listening to music while she prepares dinner makes her happy. And by the way, in /etc/fstab I can specify that the music files are READ ONLY.

I use ssh as a secure way of using rsync to back up files.

**QUERY FROM AFAR**

What do you want me to do next? How do I get those logs for you?

Thanks,
Old

---

### Post by &amp;KyT$0P# on 2022-04-10
> **Old Jimma said:**
> I've been asked for logs. How do I get these logs?

syslog is just the file [FONT=Courier New]/var/log/syslog[/FONT].  systemd journal for the current boot can be viewed with
```
journalctl -b
```

On the machine where the problem occurs, please reproduce the problem then check both of the above for related lines.

---

### Post by Old Jimma on 2022-04-10
Thank you for your reply, Halogen2:

Assuming the raspberry pi is the server (where the problem occurs because it cannot ssh to the laptop that has NFS installed), I issued a command and got the resulting reply:

> 
pi@raspberrypi:~ $  rsync --delete -az -e ssh camillesmith@192.168.1.180:/home/camillesmith/ /mnt/3TB_2 # man cave wired location

ssh: connect to host 192.168.1.180 port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(235) [Receiver=3.1.3]



Then, as per your suggestion, on the raspberry pi you asked me to issue the journalctl -b command. The file is so big that ubuntu will not let me list it on the forums.

Here re the first few lines:

> 
-- Logs begin at Thu 2019-02-14 05:11:59 EST, end at Sun 2022-04-10 13:08:14 EDT. --
Feb 14 05:11:59 raspberrypi kernel: Booting Linux on physical CPU 0x0
Feb 14 05:11:59 raspberrypi kernel: Linux version 5.10.103-v7l+ (dom@buildbot) (arm-linux-gnueabihf-gcc-8 (Ubuntu/Linaro 8.4.0-3ubuntu1) 8.4.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #1529 SMP Tue Mar 8 12:24:00 GMT 2022
Feb 14 05:11:59 raspberrypi kernel: CPU: ARMv7 Processor [410fd083] revision 3 (ARMv7), cr=30c5383d
Feb 14 05:11:59 raspberrypi kernel: CPU: div instructions available: patching division code
Feb 14 05:11:59 raspberrypi kernel: CPU: PIPT / VIPT nonaliasing data cache, PIPT instruction cache
Feb 14 05:11:59 raspberrypi kernel: OF: fdt: Machine model: Raspberry Pi 4 Model B Rev 1.4
Feb 14 05:11:59 raspberrypi kernel: random: fast init done
Feb 14 05:11:59 raspberrypi kernel: Memory policy: Data cache writealloc
Feb 14 05:11:59 raspberrypi kernel: Reserved memory: created CMA memory pool at 0x000000001ac00000, size 320 MiB
Feb 14 05:11:59 raspberrypi kernel: OF: reserved mem: initialized node linux,cma, compatible id shared-dma-pool
Feb 14 05:11:59 raspberrypi kernel: Zone ranges:
Feb 14 05:11:59 raspberrypi kernel:   DMA      [mem 0x0000000000000000-0x000000002fffffff]
Feb 14 05:11:59 raspberrypi kernel:   Normal   empty
Feb 14 05:11:59 raspberrypi kernel:   HighMem  [mem 0x0000000030000000-0x00000001ffffffff]
Feb 14 05:11:59 raspberrypi kernel: Movable zone start for each node
Feb 14 05:11:59 raspberrypi kernel: Early memory node ranges
Feb 14 05:11:59 raspberrypi kernel:   node   0: [mem 0x0000000000000000-0x000000003b3fffff]
Feb 14 05:11:59 raspberrypi kernel:   node   0: [mem 0x0000000040000000-0x00000000fbffffff]
Feb 14 05:11:59 raspberrypi kernel:   node   0: [mem 0x0000000100000000-0x00000001ffffffff]
Feb 14 05:11:59 raspberrypi kernel: Initmem setup node 0 [mem 0x0000000000000000-0x00000001ffffffff]
Feb 14 05:11:59 raspberrypi kernel: On node 0 totalpages: 2061312
Feb 14 05:11:59 raspberrypi kernel:   DMA zone: 1728 pages used for memmap
Feb 14 05:11:59 raspberrypi kernel:   DMA zone: 0 pages reserved
Feb 14 05:11:59 raspberrypi kernel:   DMA zone: 196608 pages, LIFO batch:63
Feb 14 05:11:59 raspberrypi kernel:   HighMem zone: 1864704 pages, LIFO batch:63
Feb 14 05:11:59 raspberrypi kernel: percpu: Embedded 20 pages/cpu s50828 r8192 d22900 u81920
Feb 14 05:11:59 raspberrypi kernel: pcpu-alloc: s50828 r8192 d22900 u81920 alloc=20*4096
Feb 14 05:11:59 raspberrypi kernel: pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
Feb 14 05:11:59 raspberrypi kernel: Built 1 zonelists, mobility grouping on.  Total pages: 2059584
Feb 14 05:11:59 raspberrypi kernel: Kernel command line: coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 video=HDMI-A-1:1920x1080M@60,margin_left=48,margin_right=48,margin_top=48,margin_bottom=48 smsc95xx.macaddr=E4:5F:01:3C:0C:E4 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  console=ttyS0,115200 console=tty1 root=PARTUUID=b457b5fa-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles
Feb 14 05:11:59 raspberrypi kernel: Kernel parameter elevator= does not have any effect anymore.
                                    Please use sysfs to set IO scheduler for individual devices.
Feb 14 05:11:59 raspberrypi kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes, linear)


and the last few lines:

> 
Apr 10 12:57:29 raspberrypi avahi-daemon[467]: Registering new address record for 192.168.1.136 on eth0.IPv4.
Apr 10 12:57:29 raspberrypi dhcpcd[489]: eth0: adding default route via 192.168.1.254
Apr 10 12:57:30 raspberrypi systemd[1]: systemd-rfkill.service: Succeeded.
Apr 10 12:57:31 raspberrypi kernel: v3d fec00000.v3d: MMU error from client L2T (0) at 0x3d21000, pte invalid
Apr 10 12:57:34 raspberrypi ovpn-autostart[551]: TCP/UDP: Preserving recently used remote address: [AF_INET]181.214.227.6:1198
Apr 10 12:57:34 raspberrypi ovpn-autostart[551]: UDP link local: (not bound)
Apr 10 12:57:34 raspberrypi ovpn-autostart[551]: UDP link remote: [AF_INET]181.214.227.6:1198
Apr 10 12:57:34 raspberrypi ovpn-autostart[551]: WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Apr 10 12:57:34 raspberrypi ovpn-autostart[551]: [houston427] Peer Connection Initiated with [AF_INET]181.214.227.6:1198
Apr 10 12:57:35 raspberrypi dhcpcd[489]: eth0: fe80::22f3:75ff:fe40:2720 is reachable again
Apr 10 12:57:35 raspberrypi dhcpcd[489]: eth0: fe80::22f3:75ff:fe40:2720 is reachable again
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: OpenVPN ROUTE6: OpenVPN needs a gateway parameter for a --route-ipv6 option and no default was specified by either --route-ipv6-gateway or --ifconfig-ipv6 options
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: OpenVPN ROUTE: failed to parse/resolve route for host/network: 2000::/3
Apr 10 12:57:35 raspberrypi kernel: tun: Universal TUN/TAP device driver, 1.6
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: TUN/TAP device tun0 opened
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: /sbin/ip link set dev tun0 up mtu 1500
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: /sbin/ip addr add dev tun0 10.5.112.145/24 broadcast 10.5.112.255
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: WARNING: OpenVPN was configured to add an IPv6 route over tun0. However, no IPv6 has been configured for this interface, therefore the route installation may fail or may not work as expected.
Apr 10 12:57:35 raspberrypi ovpn-autostart[551]: Initialization Sequence Completed
Apr 10 12:57:47 raspberrypi systemd[1]: systemd-fsckd.service: Succeeded.
Apr 10 12:58:05 raspberrypi systemd-timesyncd[397]: Synchronized to time server for the first time [2602:fe90:300:1a2::b954:70b5]:123 (2.debian.pool.ntp.org).
Apr 10 12:58:12 raspberrypi systemd[1]: systemd-hostnamed.service: Succeeded.
Apr 10 12:58:20 raspberrypi dhcpcd[489]: eth0: Router Advertisement from fe80::22f3:75ff:fe40:2720
Apr 10 12:58:33 raspberrypi dbus-daemon[460]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.6' (uid=0 pid=438 comm="/usr/sbin/cupsd -l ")
Apr 10 12:58:33 raspberrypi systemd[1]: Starting Manage, Install and Generate Color Profiles...
Apr 10 12:58:33 raspberrypi dbus-daemon[460]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Apr 10 12:58:33 raspberrypi systemd[1]: Started Manage, Install and Generate Color Profiles.
Apr 10 12:58:34 raspberrypi colord[1106]: failed to get session [pid 438]: No data available
Apr 10 12:59:03 raspberrypi sudo[1117]:       pi : TTY=pts/0 ; PWD=/mnt ; USER=root ; COMMAND=/usr/bin/chown -R pi:pi 3TB_2
Apr 10 12:59:03 raspberrypi sudo[1117]: pam_unix(sudo:session): session opened for user root by (uid=0)
Apr 10 12:59:03 raspberrypi sudo[1117]: pam_unix(sudo:session): session closed for user root
Apr 10 13:00:08 raspberrypi dbus-daemon[658]: [session uid=1000 pid=658] Activating service name='ca.desrt.dconf' requested by ':1.22' (uid=1000 pid=1135 comm="gedit file:///home/pi/Documents/2021-03-04-pi-comp")
Apr 10 13:00:08 raspberrypi dbus-daemon[658]: [session uid=1000 pid=658] Successfully activated service 'ca.desrt.dconf'
Apr 10 13:03:28 raspberrypi rtkit-daemon[749]: Supervising 1 threads of 1 processes of 1 users.
Apr 10 13:03:28 raspberrypi rtkit-daemon[749]: Supervising 1 threads of 1 processes of 1 users.
Apr 10 13:03:29 raspberrypi rtkit-daemon[749]: Supervising 1 threads of 1 processes of 1 users.
Apr 10 13:03:29 raspberrypi rtkit-daemon[749]: Supervising 1 threads of 1 processes of 1 users.
Apr 10 13:03:29 raspberrypi rtkit-daemon[749]: Supervising 1 threads of 1 processes of 1 users.
Apr 10 13:03:29 raspberrypi rtkit-daemon[749]: Supervising 1 threads of 1 processes of 1 users.
Apr 10 13:03:29 raspberrypi rtkit-daemon[749]: Successfully made thread 1282 of process 1186 (n/a) owned by '1000' RT at priority 10.
Apr 10 13:03:29 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:31 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:31 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:35 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:35 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:35 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:35 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:47 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:03:47 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:05:07 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:05:07 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:05:37 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:05:37 raspberrypi rtkit-daemon[749]: Supervising 2 threads of 2 processes of 1 users.
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#12 UNKNOWN(0x2003) Result: hostbyte=0x00 driverbyte=0x08 cmd_age=7s
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#12 Sense Key : 0x5 [current] 
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#12 ASC=0x21 ASCQ=0x0 
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#12 CDB: opcode=0x8a 8a 00 00 00 00 00 11 40 09 00 00 00 04 00 00 00
Apr 10 13:08:14 raspberrypi kernel: blk_update_request: critical target error, dev sdc, sector 289409280 op 0x1:(WRITE) flags 0x4000 phys_seg 128 prio class 0
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#13 UNKNOWN(0x2003) Result: hostbyte=0x00 driverbyte=0x08 cmd_age=7s
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#13 Sense Key : 0x5 [current] 
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#13 ASC=0x21 ASCQ=0x0 
Apr 10 13:08:14 raspberrypi kernel: sd 3:0:0:0: [sdc] tag#13 CDB: opcode=0x8a 8a 00 00 00 00 00 11 40 0d 00 00 00 04 00 00 00
Apr 10 13:08:14 raspberrypi kernel: blk_update_request: I/O error, dev sdc, sector 289410304 op 0x1:(WRITE) flags 0x0 phys_seg 128 prio class 0


---

### Post by TheFu on 2022-04-10
> **kevdog said:**
> @TheFu

As you probably know, rsync can keep versioned backups although they are rudimentary. There are probably better tools for the job.

It can.  But changes in permissions, owner, group, are not versioned with each hardlink copy rsync-backup set. Only the latest metadata is retained.  It isn't an issue .... until it is and you get burned. I happily used rsync + hardlinks (al le rsnapshot, back-in-time, and many others) for about 15 yrs.  Then I was burned and had to restore some programs from 6+ weeks earlier.  In that time, the program team had decided to lock down their security, so the older version wouldn't run.

There's almost always a reason - obvious or subtle - for my suggestions. Often, those suggestions were hard learned due to some failure.

If backing up just a user's HOME, then versioning using rsync+hardlinks (or any similar tool), then it is highly unlikely that the file metadata is too complex.  OTOH, people often make assumptions that backing up a HOME can be expanded to backing up /etc/ and /opt/ and /var/lib/ ... which isn't true.

rsync commands and rdiff-backup commands for simple uses are nearly identical. When I first learned that, I felt dumb for sticking with rsync longer than necessary just because it was comfortable.  rdiff-backup 2.x and later (default in 20.04) fixes the 1 remaining issue that I've experienced with that tool, sparse file support.  It doesn't just provide versioning of data, but of file metadata, including owner, group, ACLs, and xattrs.  Some tools use xattrs as a way to allow tagging of files without touching the files.  I've seen this in some photo and video organization tools, though not widely used, since that *other OS* doesn't use a similar option.

As for sshfs performance ... when dealing with whole files, it seems fine, but when performing random reads and writes of small files, it has performance issues.  I'll have to reconsider my use of sshfs looking at the data in the link below and on my own tests.  I'm just so used to use scp and the default prompt makes using scp 2nd nature for copying a few files.
[https://blog.ja-ke.tech/2019/08/27/nas-performance-sshfs-nfs-smb.html](https://blog.ja-ke.tech/2019/08/27/nas-performance-sshfs-nfs-smb.html)

In my testing, I was able to saturate the GigE LAN between my systems with most of the tools. I tried scp, rsync, sftp, sshfs, and NFSv4. In copying a 700MB file using each of those methods, most reported 108-112MB/sec for all methods.  For me, that makes the choice purely based on convenience alone when dealing with entire files.  sshfs uses FUSE, so it will have higher overhead than NFS. On a modern computer, that probably doesn't matter too much. Running processing using sshfs is most definitely slower than NFS.  I know this from real-world experience with code that does data processing while reading and writing to multiple files.

YMMV.

Having some facts is definitely better than going on 'feelings'.

---

### Post by TheFu on 2022-04-10
> Apr 10 13:08:14 raspberrypi kernel: blk_update_request: I/O error, dev sdc, sector 289410304 op 0x1WRITE) flags 0x0 phys_seg 128 prio class 0 

Does that timestamp reflect when the issue was happening?  Only logs around the time of the issue are likely to matter.

Looks like a file system or disk issue getting in the way ... or not. Still, it is a problem to be solved.

---

### Post by Old Jimma on 2022-04-11
Thanks for your studied remarks, TheFu. You're reply shows alot of knowledge gained by experience and testing.

Yes, I've fallen into a feathered pillow with rsync. My problems are[LIST]
[*]I use a Raspberry Pi running Raspian (PI OS) that doesn't use the same version of rdiff-backup as Ubuntu 2.04.... and plain old refuses to work because of that, and
[*]after installing NFS on my laptop, the Pi ssh server can no longer connect with my laptop to backup the laptop.
[*]
[/LIST]

The reason why I want NFS to work is because other computers on my network want to use VLC to play flac (music) files that are on the laptop. Who wouldn't go thru alot of grief to listen to John Coltrane?

I'm going to play arround with things to solve one problem at a time.

For example, when I first got my pi and was experimenting with it to backup files on my laptop, I had Ubuntu installed on my pi: rdiff-back up versions between the pi and the laptop differed... but worked. 

I'm going to revisit my decision to use PI OS on my Pi. Perhaps using Ubuntu on the Pi will solve the NFS problem.

I'll report results here.

Old

---

### Post by TheFu on 2022-04-11
I ran into the incompatible **rdiff-backup** versioning with 20.04 and later as well. It really isn't rdiff-backup that is the issue. It was the move from python2 to python3 that is the root cause.  Python3 does data serialization different than python2.  Basically, if we have a pitcher and a catcher ... the pitcher is throwing round balls (python2) and the catcher can only accept cubes (python3), even though both have exactly the same volume of data inside, they don't fit.  In fact, the file format on disk for both versions of rdiff-backup are the same. It is just the network serialization causing issues.

Thankfully, the rdiff-backup guys clearly split v1.x and v2.x between python2 and python3, so it is easy to check **rdiff-backup --version** for cross-version compatibility problems.

I don't have a great answer for most people. 

What I did was to install python2 on my 20.04+ systems, then ported the few dependencies for rdiff-backup v1.x to 20.04+ systems.  I did it this way because I had 1 20.04 system to start and my backup server is still running 18.04 (rdiff-backup v1.x).  As I add more 20.04+ systems, the best answer is becoming less clear.  Right now, I have 2 different backup servers. One with v1.x and the other with v2.x rdiff-backup.  The older system was planned to be retired last fall, but there is some storage on that system (RAID array and 8 HDDs total) that I need to move to another box. Other machines don't have sufficient ports to support it. The drives in it are getting old, so a HDD upgrade project - say 2 8TB HDDs would hold 100% of the data on the  older machine and solve all sorts of problems.  Money is tight and the disks aren't showing any issues in SMART.

I did setup an lxd container with 20.04 just for backups in the physical 18.04 system. Linux Containers for on raspberry Pi hardware just fine.  LXD has a storage access method that allows root to write to local storage, outside the container, so the OS would be fairly small and the same storage already being used for backups can be used.  I think this is the command to make a host directory available inside the LXD container, "NAME". This will be remembered in the profile for that specific container.
```
$ lxc storage create NAME dir source=/some/empty/directory
```

NFS doesn't work easily from any Linux Container in a secure way. This is because NFS is a kernel model and must run as root - real root. Containers don't like to have a real root (uid=0) account inside. This is also called "privileged mode". It is one of the key security DON'Ts for using containers on Linux.  I tested nfs and did get it working, but decided it was a bad idea and that using the lxd local storage method was better.

Anyway, there are a few methods.  Plus, having a backup container, each with a compatible rdiff-backup toolset solves a few other issues that are likely in the future.  Overhead of containers is very small.  Every search everyone in the world does to google's search engine spins up a container, looks for the answers, returns a webpage, and feeds the stolen data back into their nosql DB, before the container instance is spun down.  Google searches seem pretty fast, right?

---

