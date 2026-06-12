---
title: "Big boot time"
date: 2016-08-07
forum: General Help
---

### Post by claracc on 2016-08-07
Hello, one week ago, I upgraded my hp compaq 6720s laptop (3 GB RAM) from 14.04 to 16.04.01 ubuntu gnome. Bellow, there are my system specs:

```
clara@clara1:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

The upgrade was smooth and in general I am much more happy with new ubuntu release than with 14.04 (It is quick and responsive and it works out of the box), but today my system has taken more than three minutes to boot. I have run in a xterm the comand:

```
dmesg | less
```

and I have noted two big delays (first one much bigger than second one) which I write bellow:

```

[    5.516639] random: nonblocking pool is initialized
[  159.317213] EXT4-fs (sda5): mounting ext3 file system using the ext4 subsystem
[  159.338034] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[  161.258604] systemd[1]: RTC configured in localtime, applying delta of 120 minutes to system time.
[  161.949506] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
.
.
.
.
.
189.455329] audit: type=1400 audit(1470550297.525:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=2343 comm="apparmor_parser"
[  199.027187] cgroup: new mount options do not match the existing superblock, w
ill be ignored
[  199.943157] apm: BIOS not found.
[  208.795680] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  208.996277] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  209.062981] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  210.428829] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: R
x/Tx
[  210.428838] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[  210.428877] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  215.871090] NET: Registered protocol family 4
[  216.055431] NET: Registered protocol family 5
[  216.862179] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[  216.934041] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  220.056220] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  225.357214] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:2c:b0:5d:79:e5:a3:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2

```

How  could I reduce the boot time?, ¿Is there anything misconfigured?. My sda drive (where ubuntu is installed) is and ext 3 one, is this the problem?.

Thanks in advance.

---

### Post by claracc on 2016-08-09
Bump

Is there any software tool or procedure to apply in order to know why there is an almost two minutes boot time?

Any idea?

Thanks

---

### Post by westie457 on 2016-08-10
> [    5.516639] random: nonblocking pool is initialized
[  159.317213] EXT4-fs (sda5): mounting ext3 file system using the ext4 subsystem
[  159.338034] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[  161.258604] systemd[1]: RTC configured in localtime, applying delta of 120 minutes to system time.
[  161.949506] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
.
.
.
.
.
189.455329] audit: type=1400 audit(1470550297.525:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=2343 comm="apparmor_parser"
[  199.027187] cgroup: new mount options do not match the existing superblock, w
ill be ignored
Looking at the output it might be that a FSCK in recovery mode is needed.

---

