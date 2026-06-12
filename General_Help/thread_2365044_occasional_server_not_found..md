---
title: "occasional server not found."
date: 2017-07-01
forum: General Help
---

### Post by Kris_M on 2017-07-01
16.04.2 4.8.0-56.

seem to sometimes lose connection.
yesterday determined that powercycling router fixed it. (I'd been thinking I had a bad router (TPLINK 841) ).
Today determined that System Settings/Network/(wired) OFF, then ON, fixed it. (so much for bad router!) <-- will use this. Easy!

I used to have this problem random times but determined it was my particular onboard Intel NIC (I212-V), so got a separate card (HiRO) and having been using that.

It now seems to be related to playing games (offline - don't use internet - VERY old games, DOSBOX or wine). That is, after playing a game for a while I get server not found on TBird or FF and nothing works.

I did at one point think it was fault of DNS servers and played with that in router, but I think just the act of resetting something fixes it.
RJ11 VDSL2 converter RJ45 to linksys router RJ45 to HiRO NIC. 100Mbs.  I really doubt it has anything to do with IPS (Netblazer - building dish to fiber optic to converter, to RJ11 to me.)

I have started to notice it when I am randomly FF'ing which is what I do most of the time.

---

### Post by Kris_M on 2017-07-05
This has continued to happen.

The nic connected is the realtec one. enp5s0

Don't know if this is related
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1586528](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1586528)


```
                         syslog (more separate below.)
 Jul  5 20:21:20 kris-Z97X-UD3H avahi-daemon[994]: Withdrawing address record for 192.168.0.101 on enp5s0.
 Jul  5 20:21:20 kris-Z97X-UD3H avahi-daemon[994]: Leaving mDNS multicast group on interface enp5s0.IPv4 with address 192.168.0.101.
 Jul  5 20:21:20 kris-Z97X-UD3H avahi-daemon[994]: Interface enp5s0.IPv4 no longer relevant for mDNS.
 Jul  5 20:21:40 kris-Z97X-UD3H whoopsie[908]: [20:21:40] Cannot reach: [https://daisy.ubuntu.com]("https://daisy.ubuntu.com/")
 
 
 
 
 kris@kris-Z97X-UD3H:~$ route
 Kernel IP routing table
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 kris@kris-Z97X-UD3H:~$ 
 
 
 
 
 kris@kris-Z97X-UD3H:~$ sudo lshw -c network
 [sudo] password for kris:  
   *-network                
        description: Ethernet interface
        product: Ethernet Connection I217-V
        vendor: Intel Corporation
        physical id: 19
        bus info: pci@0000:00:19.0
        logical name: eno1
        version: 00
        serial: 40:8d:5c:59:ac:23
        capacity: 1Gbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
        resources: irq:26 memory:f7900000-f791ffff memory:f793c000-f793cfff ioport:f080(size=32)
   *-network
        description: Ethernet interface
        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:05:00.0
        logical name: enp5s0
        version: 07
        serial: 00:e0:4c:12:14:8d
        size: 100Mbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
        resources: irq:27 ioport:d000(size=256) memory:f7800000-f7800fff memory:f2100000-f2103fff
 kris@kris-Z97X-UD3H:~$ 
 
 
 
 
 kris@kris-Z97X-UD3H:~$ ifconfig -a
 eno1      Link encap:Ethernet  HWaddr 40:8d:5c:59:ac:23   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:20 Memory:f7900000-f7920000  
 
 
 enp5s0    Link encap:Ethernet  HWaddr 00:e0:4c:12:14:8d   
           inet6 addr: fe80::1c1f:5500:988d:f8ed/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:41918 errors:0 dropped:0 overruns:0 frame:0
           TX packets:37868 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:36467656 (36.4 MB)  TX bytes:6767711 (6.7 MB)
 
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
           TX packets:2469 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1  
           RX bytes:246237 (246.2 KB)  TX bytes:246237 (246.2 KB)
 
 
 kris@kris-Z97X-UD3H:~$ 
 
 
 
 
 ufw.log
 Jul  5 20:15:42 kris-Z97X-UD3H kernel: [ 6869.154439] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  

 Jul  5 20:17:47 kris-Z97X-UD3H kernel: [ 6994.157462] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  

 Jul  5 20:19:52 kris-Z97X-UD3H kernel: [ 7119.160522] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00


kern.log
Jul  5 21:48:22 kris-Z97X-UD3H kernel: [12429.363160] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:48:22 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305702.7079] dhcp6 (enp5s0): activation: beginning transaction (timeout in 45 seconds)
Jul  5 21:48:22 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305702.7086] dhcp6 (enp5s0): dhclient started with pid 3876
Jul  5 21:48:22 kris-Z97X-UD3H kernel: [12429.940035] audit: type=1400 audit(1499305702.705:50): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=3876 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:48:22 kris-Z97X-UD3H kernel: [12429.941169] audit: type=1400 audit(1499305702.705:51): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=3877 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <warn>  [1499305748.0484] dhcp6 (enp5s0): request timed out
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305748.0484] dhcp6 (enp5s0): state changed unknown -> timeout
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305748.0491] dhcp6 (enp5s0): canceled DHCP transaction, DHCP client pid 3876
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305748.0491] dhcp6 (enp5s0): state changed timeout -> done
Jul  5 21:49:27 kris-Z97X-UD3H kernel: [12494.293103] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:51:32 kris-Z97X-UD3H kernel: [12619.295624] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:53:37 kris-Z97X-UD3H kernel: [12744.298753] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:55:42 kris-Z97X-UD3H kernel: [12869.301854] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:57:47 kris-Z97X-UD3H kernel: [12994.304988] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:59:52 kris-Z97X-UD3H kernel: [13119.308096] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:cd:a8:5e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 


/etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

 
 
  
```


more syslog:
```
Jul  5 18:48:12 kris-Z97X-UD3H kernel: [ 1619.027101] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 18:50:17 kris-Z97X-UD3H kernel: [ 1744.030116] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 18:52:22 kris-Z97X-UD3H kernel: [ 1869.033156] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 18:53:49 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul  5 18:53:49 kris-Z97X-UD3H systemd[1]: Starting Hostname Service...
Jul  5 18:53:49 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  5 18:53:49 kris-Z97X-UD3H systemd[1]: Started Hostname Service.
Jul  5 18:53:52 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (gvfsd:1684): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jul  5 18:53:52 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (process:2560): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jul  5 18:53:55 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (gvfsd:1684): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jul  5 18:53:55 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (process:2548): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jul  5 18:53:58 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (gvfsd:1684): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jul  5 18:53:58 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (process:2550): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jul  5 18:54:01 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (gvfsd:1684): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jul  5 18:54:01 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (process:2555): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jul  5 18:54:04 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (gvfsd:1684): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jul  5 18:54:04 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (process:2567): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jul  5 18:54:07 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (gvfsd:1684): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jul  5 18:54:07 kris-Z97X-UD3H org.gtk.vfs.Daemon[1612]: ** (process:2565): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jul  5 18:54:27 kris-Z97X-UD3H kernel: [ 1994.036244] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 18:55:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499295316.7015] keyfile: update /etc/NetworkManager/system-connections/Wired connection 2 (6efaa0a8-c13c-30b6-b214-3c4769d084c1,"Wired connection 2")
Jul  5 18:55:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499295316.7018] audit: op="connection-update" uuid="6efaa0a8-c13c-30b6-b214-3c4769d084c1" name="Wired connection 2" pid=2531 uid=1000 result="success"
Jul  5 18:56:32 kris-Z97X-UD3H kernel: [ 2119.039256] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 18:58:37 kris-Z97X-UD3H kernel: [ 2244.042257] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:00:42 kris-Z97X-UD3H kernel: [ 2369.045310] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:02:47 kris-Z97X-UD3H kernel: [ 2494.048325] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:04:52 kris-Z97X-UD3H kernel: [ 2619.051437] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:06:57 kris-Z97X-UD3H kernel: [ 2744.054408] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:09:02 kris-Z97X-UD3H kernel: [ 2869.057475] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:11:07 kris-Z97X-UD3H kernel: [ 2994.060510] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:13:12 kris-Z97X-UD3H kernel: [ 3119.063597] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:15:17 kris-Z97X-UD3H kernel: [ 3244.066644] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:17:01 kris-Z97X-UD3H CRON[2738]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 19:17:22 kris-Z97X-UD3H kernel: [ 3369.069698] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:19:27 kris-Z97X-UD3H kernel: [ 3494.072737] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:21:26 kris-Z97X-UD3H org.gnome.evolution.dataserver.Sources5[1612]: ** (evolution-source-registry:1851): WARNING **: secret_service_search_sync: must specify at least one attribute to match
Jul  5 19:21:32 kris-Z97X-UD3H kernel: [ 3619.075743] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:23:37 kris-Z97X-UD3H kernel: [ 3744.078807] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:25:42 kris-Z97X-UD3H kernel: [ 3869.081782] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:27:47 kris-Z97X-UD3H kernel: [ 3994.084917] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:29:52 kris-Z97X-UD3H kernel: [ 4119.087851] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:31:57 kris-Z97X-UD3H kernel: [ 4244.090905] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:34:02 kris-Z97X-UD3H kernel: [ 4369.094000] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:36:07 kris-Z97X-UD3H kernel: [ 4494.097045] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:38:12 kris-Z97X-UD3H kernel: [ 4619.100041] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:40:17 kris-Z97X-UD3H kernel: [ 4744.102990] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:42:22 kris-Z97X-UD3H kernel: [ 4869.106051] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:44:27 kris-Z97X-UD3H kernel: [ 4994.109109] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:46:32 kris-Z97X-UD3H kernel: [ 5119.112061] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:48:37 kris-Z97X-UD3H kernel: [ 5244.115032] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:50:42 kris-Z97X-UD3H kernel: [ 5369.118053] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:52:47 kris-Z97X-UD3H kernel: [ 5494.121020] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:54:52 kris-Z97X-UD3H kernel: [ 5619.124053] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:56:57 kris-Z97X-UD3H kernel: [ 5744.127094] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 19:59:02 kris-Z97X-UD3H kernel: [ 5869.130072] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:01:07 kris-Z97X-UD3H kernel: [ 5994.133127] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:03:12 kris-Z97X-UD3H kernel: [ 6119.136185] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:05:17 kris-Z97X-UD3H kernel: [ 6244.139228] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:07:22 kris-Z97X-UD3H kernel: [ 6369.142253] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:09:27 kris-Z97X-UD3H kernel: [ 6494.145259] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:11:32 kris-Z97X-UD3H kernel: [ 6619.148328] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:13:37 kris-Z97X-UD3H kernel: [ 6744.151402] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:15:42 kris-Z97X-UD3H kernel: [ 6869.154439] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:17:01 kris-Z97X-UD3H CRON[3210]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 20:17:47 kris-Z97X-UD3H kernel: [ 6994.157462] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:19:52 kris-Z97X-UD3H kernel: [ 7119.160522] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 20:21:20 kris-Z97X-UD3H avahi-daemon[994]: Withdrawing address record for 192.168.0.101 on enp5s0.
Jul  5 20:21:20 kris-Z97X-UD3H avahi-daemon[994]: Leaving mDNS multicast group on interface enp5s0.IPv4 with address 192.168.0.101.
Jul  5 20:21:20 kris-Z97X-UD3H avahi-daemon[994]: Interface enp5s0.IPv4 no longer relevant for mDNS.
Jul  5 20:21:40 kris-Z97X-UD3H whoopsie[908]: [20:21:40] Cannot reach: https://daisy.ubuntu.com
Jul  5 20:21:40 kris-Z97X-UD3H whoopsie[908]: [20:21:40] offline

noticed here

Jul  5 21:06:53 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul  5 21:06:53 kris-Z97X-UD3H systemd[1]: Starting Hostname Service...
Jul  5 21:06:53 kris-Z97X-UD3H org.freedesktop.FileManager1[1612]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Jul  5 21:06:53 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  5 21:06:53 kris-Z97X-UD3H systemd[1]: Started Hostname Service.
Jul  5 21:17:01 kris-Z97X-UD3H CRON[3505]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 21:47:06 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul  5 21:47:06 kris-Z97X-UD3H systemd[1]: Starting Hostname Service...
Jul  5 21:47:06 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  5 21:47:06 kris-Z97X-UD3H systemd[1]: Started Hostname Service.
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.0682] device (enp5s0): state change: activated -> deactivating (reason 'user-requested') [100 110 39]
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.0683] manager: NetworkManager state is now DISCONNECTING
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.0734] audit: op="device-disconnect" interface="enp5s0" ifindex=2 pid=3717 uid=1000 result="success"
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.0738] device (enp5s0): state change: deactivating -> disconnected (reason 'user-requested') [110 30 39]
Jul  5 21:48:16 kris-Z97X-UD3H avahi-daemon[994]: Withdrawing address record for fe80::1c1f:5500:988d:f8ed on enp5s0.
Jul  5 21:48:16 kris-Z97X-UD3H avahi-daemon[994]: Leaving mDNS multicast group on interface enp5s0.IPv6 with address fe80::1c1f:5500:988d:f8ed.
Jul  5 21:48:16 kris-Z97X-UD3H avahi-daemon[994]: Interface enp5s0.IPv6 no longer relevant for mDNS.
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.1072] dhcp4 (enp5s0): canceled DHCP transaction, DHCP client pid 1320
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.1072] dhcp4 (enp5s0): state changed bound -> done
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.1075] dns-mgr: Writing DNS information to /sbin/resolvconf
Jul  5 21:48:16 kris-Z97X-UD3H dnsmasq[1331]: setting upstream servers from DBus
Jul  5 21:48:16 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305696.1109] manager: NetworkManager state is now DISCONNECTED
Jul  5 21:48:16 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jul  5 21:48:16 kris-Z97X-UD3H systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul  5 21:48:16 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  5 21:48:16 kris-Z97X-UD3H systemd[1]: Started Network Manager Script Dispatcher Service.
Jul  5 21:48:16 kris-Z97X-UD3H nm-dispatcher: req:1 'down' [enp5s0]: new request (1 scripts)
Jul  5 21:48:16 kris-Z97X-UD3H nm-dispatcher: req:1 'down' [enp5s0]: start running ordered scripts...
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6619] device (enp5s0): Activation: starting connection 'Wired connection 2' (6efaa0a8-c13c-30b6-b214-3c4769d084c1)
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6619] audit: op="connection-activate" uuid="6efaa0a8-c13c-30b6-b214-3c4769d084c1" name="Wired connection 2" pid=3717 uid=1000 result="success"
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6620] device (enp5s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6621] manager: NetworkManager state is now CONNECTING
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6623] device (enp5s0): state change: prepare -> config (reason 'none') [40 50 0]
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6625] device (enp5s0): state change: config -> ip-config (reason 'none') [50 70 0]
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6626] dhcp4 (enp5s0): activation: beginning transaction (timeout in 45 seconds)
Jul  5 21:48:20 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305700.6644] dhcp4 (enp5s0): dhclient started with pid 3751
Jul  5 21:48:20 kris-Z97X-UD3H kernel: [12427.895851] audit_printk_skb: 3 callbacks suppressed
Jul  5 21:48:20 kris-Z97X-UD3H kernel: [12427.895852] audit: type=1400 audit(1499305700.661:47): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=3751 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:48:20 kris-Z97X-UD3H kernel: [12427.897397] audit: type=1400 audit(1499305700.661:48): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=3752 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:48:20 kris-Z97X-UD3H dhclient[3751]: DHCPREQUEST of 192.168.0.101 on enp5s0 to 255.255.255.255 port 67 (xid=0x5042dd19)
Jul  5 21:48:21 kris-Z97X-UD3H dhclient[3751]: DHCPACK of 192.168.0.101 from 192.168.0.1
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019]   address 192.168.0.101
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019]   plen 24 (255.255.255.0)
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019]   gateway 192.168.0.1
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019]   server identifier 192.168.0.1
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019]   lease time 7200
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019]   nameserver '192.168.0.1'
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7019] dhcp4 (enp5s0): state changed unknown -> bound
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7024] device (enp5s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7027] device (enp5s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7028] device (enp5s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7029] manager: NetworkManager state is now CONNECTED_LOCAL
Jul  5 21:48:21 kris-Z97X-UD3H avahi-daemon[994]: Joining mDNS multicast group on interface enp5s0.IPv4 with address 192.168.0.101.
Jul  5 21:48:21 kris-Z97X-UD3H avahi-daemon[994]: New relevant interface enp5s0.IPv4 for mDNS.
Jul  5 21:48:21 kris-Z97X-UD3H avahi-daemon[994]: Registering new address record for 192.168.0.101 on enp5s0.IPv4.
Jul  5 21:48:21 kris-Z97X-UD3H kernel: [12428.931649] audit: type=1400 audit(1499305701.697:49): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=3758 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:48:21 kris-Z97X-UD3H whoopsie[908]: [21:48:21] Cannot reach: https://daisy.ubuntu.com
Jul  5 21:48:21 kris-Z97X-UD3H dhclient[3751]: bound to 192.168.0.101 -- renewal in 3231 seconds.
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7102] manager: NetworkManager state is now CONNECTED_GLOBAL
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7102] policy: set 'Wired connection 2' (enp5s0) as default for IPv4 routing and DNS
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7103] dns-mgr: Writing DNS information to /sbin/resolvconf
Jul  5 21:48:21 kris-Z97X-UD3H dnsmasq[1331]: setting upstream servers from DBus
Jul  5 21:48:21 kris-Z97X-UD3H dnsmasq[1331]: using nameserver 192.168.0.1#53(via enp5s0)
Jul  5 21:48:21 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305701.7132] device (enp5s0): Activation: successful, device activated.
Jul  5 21:48:21 kris-Z97X-UD3H nm-dispatcher: req:2 'up' [enp5s0]: new request (1 scripts)
Jul  5 21:48:21 kris-Z97X-UD3H nm-dispatcher: req:2 'up' [enp5s0]: start running ordered scripts...
Jul  5 21:48:21 kris-Z97X-UD3H kernel: [12428.943237] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:48:21 kris-Z97X-UD3H whoopsie[908]: [21:48:21] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Jul  5 21:48:21 kris-Z97X-UD3H whoopsie[908]: [21:48:21] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Jul  5 21:48:21 kris-Z97X-UD3H whoopsie[908]: [21:48:21] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Jul  5 21:48:21 kris-Z97X-UD3H whoopsie[908]: [21:48:21] online
Jul  5 21:48:22 kris-Z97X-UD3H kernel: [12429.363160] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:48:22 kris-Z97X-UD3H avahi-daemon[994]: Joining mDNS multicast group on interface enp5s0.IPv6 with address fe80::1c1f:5500:988d:f8ed.
Jul  5 21:48:22 kris-Z97X-UD3H avahi-daemon[994]: New relevant interface enp5s0.IPv6 for mDNS.
Jul  5 21:48:22 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305702.7079] dhcp6 (enp5s0): activation: beginning transaction (timeout in 45 seconds)
Jul  5 21:48:22 kris-Z97X-UD3H avahi-daemon[994]: Registering new address record for fe80::1c1f:5500:988d:f8ed on enp5s0.*.
Jul  5 21:48:22 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305702.7086] dhcp6 (enp5s0): dhclient started with pid 3876
Jul  5 21:48:22 kris-Z97X-UD3H kernel: [12429.940035] audit: type=1400 audit(1499305702.705:50): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=3876 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:48:22 kris-Z97X-UD3H kernel: [12429.941169] audit: type=1400 audit(1499305702.705:51): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=3877 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  5 21:48:23 kris-Z97X-UD3H dhclient[3876]: XMT: Solicit on enp5s0, interval 1080ms.
Jul  5 21:48:24 kris-Z97X-UD3H dhclient[3876]: XMT: Solicit on enp5s0, interval 2190ms.
Jul  5 21:48:26 kris-Z97X-UD3H dhclient[3876]: XMT: Solicit on enp5s0, interval 4480ms.
Jul  5 21:48:31 kris-Z97X-UD3H dhclient[3876]: XMT: Solicit on enp5s0, interval 9200ms.
Jul  5 21:48:40 kris-Z97X-UD3H dhclient[3876]: XMT: Solicit on enp5s0, interval 18350ms.
Jul  5 21:48:59 kris-Z97X-UD3H dhclient[3876]: XMT: Solicit on enp5s0, interval 35060ms.
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <warn>  [1499305748.0484] dhcp6 (enp5s0): request timed out
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305748.0484] dhcp6 (enp5s0): state changed unknown -> timeout
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305748.0491] dhcp6 (enp5s0): canceled DHCP transaction, DHCP client pid 3876
Jul  5 21:49:08 kris-Z97X-UD3H NetworkManager[988]: <info>  [1499305748.0491] dhcp6 (enp5s0): state changed timeout -> done
Jul  5 21:49:27 kris-Z97X-UD3H kernel: [12494.293103] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:51:32 kris-Z97X-UD3H kernel: [12619.295624] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:53:37 kris-Z97X-UD3H kernel: [12744.298753] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:55:42 kris-Z97X-UD3H kernel: [12869.301854] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:57:47 kris-Z97X-UD3H kernel: [12994.304988] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 21:59:52 kris-Z97X-UD3H kernel: [13119.308096] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:01:00 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul  5 22:01:00 kris-Z97X-UD3H systemd[1]: Starting Hostname Service...
Jul  5 22:01:00 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  5 22:01:00 kris-Z97X-UD3H systemd[1]: Started Hostname Service.
Jul  5 22:01:01 kris-Z97X-UD3H org.freedesktop.FileManager1[1612]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Jul  5 22:01:57 kris-Z97X-UD3H kernel: [13244.311184] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <info>  [1499306633.5440] NetworkManager (version 1.2.6) is starting...
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <info>  [1499306633.5440] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <info>  [1499306633.5457] manager[0x26421c0]: monitoring kernel firmware directory '/lib/firmware'.
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <info>  [1499306633.5458] monitoring ifupdown state file '/run/network/ifstate'.
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <info>  [1499306633.5465] dns-mgr[0x263d150]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <error> [1499306633.5473] bus-manager: could not acquire the NetworkManager service as it is already taken
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <error> [1499306633.5473] failed to start the dbus service.
Jul  5 22:03:53 kris-Z97X-UD3H NetworkManager[4001]: <info>  [1499306633.5473] exiting (error)
Jul  5 22:04:02 kris-Z97X-UD3H kernel: [13369.314326] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:05:06 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul  5 22:05:06 kris-Z97X-UD3H systemd[1]: Starting Hostname Service...
Jul  5 22:05:06 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  5 22:05:06 kris-Z97X-UD3H systemd[1]: Started Hostname Service.
Jul  5 22:06:07 kris-Z97X-UD3H kernel: [13494.317437] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:07:39 kris-Z97X-UD3H systemd[1]: snapd.refresh.timer: Adding 4h 10min 42.870286s random time.
Jul  5 22:08:12 kris-Z97X-UD3H kernel: [13619.320530] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:10:17 kris-Z97X-UD3H kernel: [13744.323665] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:10:53 kris-Z97X-UD3H dbus[963]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul  5 22:10:53 kris-Z97X-UD3H systemd[1]: Starting Hostname Service...
Jul  5 22:10:53 kris-Z97X-UD3H dbus[963]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  5 22:10:53 kris-Z97X-UD3H systemd[1]: Started Hostname Service.
Jul  5 22:10:53 kris-Z97X-UD3H org.freedesktop.FileManager1[1612]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Jul  5 22:12:22 kris-Z97X-UD3H kernel: [13869.326783] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:14:27 kris-Z97X-UD3H kernel: [13994.329954] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:16:32 kris-Z97X-UD3H kernel: [14119.333018] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:13:37 kris-Z97X-UD3H org.freedesktop.FileManager1[1612]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Jul  5 22:17:01 kris-Z97X-UD3H CRON[4131]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 22:18:37 kris-Z97X-UD3H kernel: [14244.336126] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:20:42 kris-Z97X-UD3H kernel: [14369.339205] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 22:20:54 kris-Z97X-UD3H systemd-timesyncd[812]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Jul  5 22:22:47 kris-Z97X-UD3H kernel: [14494.342375] [UFW BLOCK] IN=enp5s0 OUT= MAC=x SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
```

---

