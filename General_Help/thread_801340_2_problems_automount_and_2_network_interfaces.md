---
title: "2 problems: automount and 2 network interfaces"
date: 2008-05-20
forum: General Help
---

### Post by rede82 on 2008-05-20
First of all I've been searching solutions for these two problems quite some time now over these forums and google and found a lot of similar situations and some attempts to fix them, but none have actually worked. So going straight to the point.

1. Installed Ubuntu 8.04 from scratch to my old ubuntu box after formatting all old data from every drive. Basicly i have three different hard drives one main drive 200gigs that currently holds installed ubuntu 8.04 and runs fine, then i have to other drives that i wish to use to extend my hard drive space with, one 80gig and one 120gig. i managed to mount these two drives manually from terminal and now trying to figure out a way to mount them automatically on boot and finally i intent to use them as network drives for my windows machine with read/write access.

**sudo fdisk -l looks like this:**

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc77fc77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x383c0bff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    5  Extended
/dev/sdb5               1        9729    78148129+  83  Linux

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x235960e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14596   117242338+   5  Extended
/dev/sdc5               1       14596   117242307   83  Linux



**And /etc/fstab at the moment look like this:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e70cf615-98f9-4f6e-9f9a-a73b55151c7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8dbbdc7e-84c6-436f-a289-5ad74120ef49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdb5	/home/user/80g	ext3 rw,nodev,auto,utf8,umask=077	0	1
/dev/sdc5	/home/user/120g	ext3 rw,nodev,auto,etf8,umask=077	0	1


Now when i boot the last two drives aren't mounted to the directories i pointed them to mount and when i mount them manually they ain't even read/write accessible to myself when logged in ubuntu, not to even speak when used as shared network drives. So someone who knows better what might be the problem?




2. Same ubuntu machine also has two network cards in it.
First one is on eth0 interface and second eth1 interface.

Eth0 interface is used to access my own lan and adsl gateway to internet and eth1 interface is used by my friend to connect to my ubuntu server trhough his own wlan.

Problem is that these networks ain't working properly at the same time. eth0 gets its ip from dhcp provided by my adsl router and eth1 has static ip configured and uses wlan router as a gateway to connect to my friends wlan.

**ifconfig looks like this:**

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fec0::8:250:8dff:fef5:d07e/64 Scope:Site
          inet6 addr: 2002:c394:49b7:8:250:8dff:fef5:d07e/64 Scope:Global
          inet6 addr: fe80::250:8dff:fef5:d07e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6118128 (5.8 MB)  TX bytes:63701002 (60.7 MB)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a7ff:fe08:eb07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2382 (2.3 KB)  TX bytes:528 (528.0 B)
          Interrupt:19 Base address:0x9400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67379769 (64.2 MB)  TX bytes:67379769 (64.2 MB)



**/etc/network/interfaces looks like this:**

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0
network 10.0.0.0
gateway 10.0.0.254
up route add -net 10.0.0.0/24 gw 10.0.0.254 dev eth1
up route del default gw 10.0.0.254

auto eth1


where 10.0.0.254 is the wlan gateway router
**And finally route -n provides:**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        10.0.0.254      255.255.255.0   UG    0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

problem is that eth0 interface works like a charm most of the time, but eth1 interface only answers to ping 10.0.0.1 which is localhost at that interface, when trying to ping the 10.0.0.254 which is the wlan gateway router to my friend all i get is:  ping: sendmsg: Operation not permitted.
My friend has access to the wlan gateway from his end no problem, so atm the problem is between eth1 and wlan gateway. Although when making the wlan gateway work as dhcp server and 
making eth1 too use dhcp to acquire address then both eth0 and eth1 stop working. I've managed to narrow the problem propably to the routing table but not sure what to do with it. And using sudo to prevent ping: sendmsg: Operation not permitted  is not helping. And to clarify eth1 and wlan router are wire connected not wifi and wlan router confs are working right. Wlan router doesn't have firewall on, but ubuntu has iptables.

---

### Post by ibuclaw on 2008-05-20
[QUOTE=rede82]
And /etc/fstab at the moment look like this:

/dev/sdb5 /home/user/80g ext3 rw,nodev,auto,utf8,umask=077 0 1
/dev/sdc5 /home/user/120g ext3 rw,nodev,auto,etf8,umask=077 0 1
[/QUOTE]

Change it to:
```

/dev/sdb5 /home/user/80g ext3 defaults,users,exec 0 1
/dev/sdc5 /home/user/120g ext3 defaults,users,exec 0 1

```
Then when it mounts, type in:
```

sudo chown yourname:yourname /home/user/80g -R
sudo chown yourname:yourname /home/user/120g -R

```
And that should solve your HardDrive problem.

Regards
Iain

---

### Post by rede82 on 2008-05-20
Thanks for sharing that knowledge, now it works like it was intended.

---

### Post by ibuclaw on 2008-05-20
> **rede82 said:**
> Thanks for sharing that knowledge, now it works like it was intended.

Your welcome.

A hint for the future though.

[LIST]
[*]utf8
[*]umask=000
[*]gid=00
[/LIST]
Are all DOS, FAT and NTFS specific FSTAB arguments and should never be used for Linux and other Unix types of filesystem.

For more info, open up a terminal and type in:
```
man mount
```
It makes a very good midnight read. :D

Regards
Iain

---

### Post by ibuclaw on 2008-05-20
As for problem Number Two, I'm not the best person to talk about Networks, but have a search through ubuntugeek.com, as there is plenty of help there.

[Here is the page on network configuring.]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html")

Regards
Iain

---

