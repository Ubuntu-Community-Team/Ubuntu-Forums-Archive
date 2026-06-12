---
title: "Question(s) About Boot Time"
date: 2013-08-17
forum: General Help
---

### Post by echotech2 on 2013-08-17
Ubuntu 13.04, all updates,
Quad-core CPU @ 3.0 Mhz,
4 Mb RAM @1066 Mhz,
SATA 7200 RPM hard disk.

 According to DMESG my boot time is 47.432786 seconds. Reasonable?

1) I also have a question about zram.  Portion of DMESG:

[   44.077322] r8169 0000:04:00.0 eth0: link down
[   44.077368] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.181586] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   44.181841] zram: **Creating 4 devices** ...
[   44.194345] Adding 506008k swap on /dev/zram0.  Priority:5 extents:1 across:506008k SS
[   44.197773] Adding 506008k swap on /dev/zram1.  Priority:5 extents:1 across:506008k SS
[   44.201611] Adding 506008k swap on /dev/zram2.  Priority:5 extents:1 across:506008k SS
[   44.205853] Adding 506008k swap on /dev/zram3.  Priority:5 extents:1 across:506008k SS
[   44.271476] init: gdm main process (1377) killed by TERM signal
[   45.916324] r8169 0000:04:00.0 eth0: link up

  Do I have (or need) four RAM Disks?

2) Is it taking 24 seconds to do whatever it is doing to the swap partition?  From DMESG:

[   11.422640] EXT4-fs (sda1): mounted filesystem with writeback data mode. Opts: (null)
[   35.325992] Adding 10024556k swap on /dev/sda2.  Priority:-1 extents:1 across:10024556k 
[   36.400078] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

  Don't go away, there maybe more questions to come, lol.

  TIA --Dave

---

### Post by gordintoronto on 2013-08-17
Reasonable. See [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by echotech2 on 2013-08-19
OK thanks gordintoronto.  I am still wondering about zram 1) above and the apparent 24 seconds in 2). After the caffeine kicked in I realized that [EXT4-fs (sda1): mounted filesystem with writeback data mode. Opts: (null)] is (maybe?) what is taking 24 seconds.

PS: I had to visit Toronto on Saturday and get to Yonge/St. Claire area.  Bad move!!  Is there ever NOT traffic jams in Toronto?

  --Dave

---

### Post by gordintoronto on 2013-08-19
Sorry, I have no ideas about zram. 47 seconds is pretty good if you don't have an SSD.

---

### Post by VMC on 2013-08-19
Regarding zram [read this article]("http://gionn.net/2012/03/11/zram-on-debian-ubuntu-for-memory-overcommitment/")

---

### Post by echotech2 on 2013-08-20
Thanks VMC, that link explains ZRAM.  There is one instance of ZRAM for each CPU core, if I understand it correctly.  I have a quad-core CPU therefore voila!  

  An SSD is sitting on my desk, however summertime is not the time for mechanical mods,  too much to do outside.

  --Dave

---

### Post by echotech2 on 2013-08-20
OK, next question.  I get this several times...
 
89.271462] systemd-hostnamed[4400]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

  I read the documentation but it is all Greek (Ubuntu-ese?)to me.  So Should I just install nss-myhostname?

  --Dave

---

### Post by VMC on 2013-08-20
Here's a discussion on [nss-myhostname]("https://bbs.archlinux.org/viewtopic.php?id=156214"). Also what's inside hosts and hostname.

---

### Post by echotech2 on 2013-08-21
hosts contents:

127.0.0.1    scamper    localhost.localdomain    localhost
::1    scamper    localhost6.localdomain6    localhost6
127.0.1.1    scamper

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

hostname contents:

scamper

  I'm just wondering about this more out of curiosity.  Everything seems to be working OK.  

  PS: I'm retired now and decided to keep my brain (somewhat) active by digging into the inner workings of Ubuntu. I might as well start with "boot"

---

### Post by oldfred on 2013-08-21
On my working install with an SSD, it mounts in about a third of a second. But I have never known if timestamp is start or end of process, so is it really swap or mounting of partition? And my SSD has no journal so that might change mount time a lot?

[    5.773475] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    6.077696] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across:3076412k 

But on my test install of Raring on my hard drive (not same sdd in drive order):
[   11.643571] EXT4-fs (sdd13): mounted filesystem with ordered data mode. Opts: (null)
[   21.165832] Adding 3068408k swap on /dev/sdc3.  Priority:-1 extents:1 across:3068408k

---

### Post by echotech2 on 2013-08-22
I was wondering the same thing about DMESG timestamps being start or end of a process.  I looked around and came across the DMESG option which really isn't TOO clear (to me).:

&#8722;d, &#8722;&#8722;show&#8722;delta
             Display the timestamp and time delta spent between             messages.

Using "DMESG -d" :


[   11.878114 <    0.000002>] EXT4-fs (sda1): recovery complete
[   11.944375 <    0.066261>] EXT4-fs (sda1): mounted filesystem with writeback data mode. Opts: (null)
[   34.396351 <   22.451976>] Adding 10024556k swap on /dev/sda2.  Priority:-1 extents:1 across:10024556k 
[   35.594036 <    1.197685>] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

  So I guess it's either taking 23.xx seconds to mount sda1 (boot partition, home is a separate partition) or add sda2 (swap).

  BTW, here is mount for my home partition:
[   36.803199 <    0.000603>] EXT4-fs (sdc1): mounted filesystem with writeback data mode. Opts: (null)
[   36.900973 <    0.097774>] EXT4-fs (sda3): mounted filesystem with writeback data mode. Opts: (null)
[   37.643650 <    0.742677>] parport_pc 00:07: reported by Plug and Play ACPI.

  Thanks everyone for your replies.

  --Dave

---

