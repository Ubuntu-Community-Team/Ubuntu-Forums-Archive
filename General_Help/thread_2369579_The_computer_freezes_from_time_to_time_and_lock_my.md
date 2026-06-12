---
title: "The computer freezes from time to time and lock my local network"
date: 2017-08-24
forum: General Help
---

### Post by itaroiu on 2017-08-24
Hi,

I have the following problem on my desktop running Lubuntu 17 which is connected to my local network:

The problem is that from unknown reasons my desktop stop responding randomly, at no specific time, and also it locks my router and the entire local network. No router client can't access internet at this stage. The network comes back to normal only if I take out the network cable from desktop LAN card, but the computer is still freeze. I've noticed that orange led from LAN card blinks constantly at constant frequency and the green one is constantly lightning.

The only thing I can do is to switch of the computer by force from the main switch or to reset the computer from the reset button. After reboot everything works fine for awhile.

Does anyone have any idea what is happening and what can I do to solve this issue?

Thanks!

---

### Post by Bashing-om on 2017-08-24
itaroiu' Hello;

I too suffered a similar condition. In MY case installing a proprietary graphic's driver resolved the issue.

What is your graphic's set?
Post back - between code tags - the out put of terminal command:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]maybe same ?
[/INDENT][/INDENT]

---

### Post by itaroiu on 2017-08-24
Hi,
Please find bellow the command output.

```

itaroiu@ThinkCentre-M91p:~$ sudo lshw -C display
[sudo] password for itaroiu: 
  *-display                 
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
itaroiu@ThinkCentre-M91p:~$ 


```

Thanks!

---

### Post by Bashing-om on 2017-08-24
itaroiu; Nope. sorry;

Not related to the issue I faced . Intel graphics and the driver is loaded .
A Random freeze issue is tough to deal with . Particularly so as logging is also halted in most cases.
But, maybe one can get an indication :
open a new terminal and follow the logging, see if you can see an anomaly.
thus:
```

journalctl -f

```
key combo ctl+c to "quit" .

Not likely but watch the memory usage
```

free -m
top

```

Just not an easy
[INDENT][INDENT]straight-forward answer
[/INDENT][/INDENT]

---

### Post by BenginM on 2017-08-24
Hiya itaroiu , Bashing-om ..

which LAN card is it , sudo apt install inxi , then run inxi -Nn ..
 And which kernel is in use ..
Does the system freeze while connected with the wireless card ?

there several reasons for the system to freeze /hang/lockup .. for instance #See:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

we should probably have a look at some logs , in /var/log  kern.log.1 and syslog.1 , please post them to [https://paste.ubuntu.com/](https://paste.ubuntu.com/) , then paste the links for us here, Thanks.

I hope your system has a previous kernel , if so try bootin' with it and check if this behavior is there too . at some point you will need to try and test a new kernel.

---

### Post by itaroiu on 2017-08-25
Hi,
This is the listing of journalctl -f

```

itaroiu@ThinkCentre-M91p:~$ journalctl -f
-- Logs begin at Thu 2017-08-24 21:02:59 EEST. --
aug 25 09:50:31 ThinkCentre-M91p xrdp-sesman[1003]: (1003)(140271766832512)[INFO ] ++ reconnected session: username itaroiu, display :10.0, session_pid 1850, ip 0.0.0.0:44278 - socket: 12
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[INFO ] xrdp_wm_log_msg: login successful for display 10
aug 25 09:50:31 ThinkCentre-M91p xrdp-sesman[1003]: (1003)(140271766832512)[DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[DEBUG] xrdp_wm_log_msg: started connecting
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[INFO ] lib_mod_log_peer: xrdp_pid=5097 connected to X11rdp_pid=1852 X11rdp_uid=1000 X11rdp_gid=1000 client_ip=::ffff:192.168.5.12 client_port=44278
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[DEBUG] xrdp_wm_log_msg: connected ok
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[DEBUG] xrdp_mm_connect_chansrv: chansrv connect successful
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[DEBUG] Closed socket 16 (AF_INET6 ::1 port 50176)
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[INFO ] The following channel is allowed: cliprdr (0)
aug 25 09:50:31 ThinkCentre-M91p xrdp[5097]: (5097)(140385884384064)[DEBUG] The allow channel list now initialized for this session

```

---

### Post by itaroiu on 2017-08-25
@BenginM
Hi,
You can find bellow the links of logs:
[https://paste.ubuntu.com/25387796/](https://paste.ubuntu.com/25387796/)
[https://paste.ubuntu.com/25387816/](https://paste.ubuntu.com/25387816/)

and the listing of inxi -Nn
```

itaroiu@ThinkCentre-M91p:~$ inxi -Nn
Network:   Card: Intel 82579LM Gigabit Network Connection driver: e1000e
           IF: eno1 state: up speed: 100 Mbps duplex: full
           mac: 44:37:e6:72:64:60
itaroiu@ThinkCentre-M91p:~$ 

```

Thanks a lot!

---

### Post by Bashing-om on 2017-08-25
itaroiu;

@BenginM

Numerous instances of
> 
internal error: unable to execute QEMU command 'query-cpu-definitions':

for various units.

What in the world is going on here ?

Trying to spin up a virtual machine and failing ??

[INDENT][INDENT]I do wonder
[/INDENT][/INDENT]

---

### Post by BenginM on 2017-08-25
Bashing-om , Yes exactly my thoughts , and there are several confusion instance of connections :

```

21:03:03 ThinkCentre-M91p libvirtd[984]: Failed to probe capabilities for /usr/bin/qemu-system-xtensa: internal error: unable to execute QEMU command 'query-cpu-definitions': The command query-cpu-definitions has not been found
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9577] device (eno1): link connected
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9579] device (eno1): state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9586] policy: auto-activating connection 'Wired connection 1'
Aug 24 21:03:03 ThinkCentre-M91p kernel: [   12.788459] e1000e: eno1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Aug 24 21:03:03 ThinkCentre-M91p kernel: [   12.788506] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9599] device (eno1): Activation: starting connection 'Wired connection 1' (02b71661-5632-3f07-ad25-b87d270f5fa3)
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9601] device (eno1): state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9602] manager: NetworkManager state is now CONNECTING
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9606] device (eno1): state change: prepare -> config (reason 'none') [40 50 0]
Aug 24 21:03:03 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597783.9610] device (eno1): state change: config -> ip-config (reason 'none') [50 70 0]
##
21:03:04 ThinkCentre-M91p systemd-udevd[1502]: Could not generate persistent MAC address for virbr0: No such file or directory
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.2622] manager: (virbr0): new Bridge device (/org/freedesktop/NetworkManager/Devices/2)
Aug 24 21:03:04 ThinkCentre-M91p kernel: [   13.092029] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.2639] manager: (virbr0-nic): new Tun device (/org/freedesktop/NetworkManager/Devices/3)
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.2700] devices added (path: /sys/devices/virtual/net/virbr0, iface: virbr0)
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.2701] device added (path: /sys/devices/virtual/net/virbr0, iface: virbr0): no ifupdown configuration found.
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.2715] devices added (path: /sys/devices/virtual/net/virbr0-nic, iface: virbr0-nic)
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.2715] device added (path: /sys/devices/virtual/net/virbr0-nic, iface: virbr0-nic): no ifupdown configuration found.
Aug 24 21:03:04 ThinkCentre-M91p kernel: [   13.174606] virbr0: port 1(virbr0-nic) entered blocking state
Aug 24 21:03:04 ThinkCentre-M91p kernel: [   13.174607] virbr0: port 1(virbr0-nic) entered disabled state
Aug 24 21:03:04 ThinkCentre-M91p kernel: [   13.174679] device virbr0-nic entered promiscuous mode
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.3757] device (virbr0-nic): state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Aug 24 21:03:04 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597784.3763] device (virbr0-nic): state change: unavailable -> disconnected (reason 'none') [20 30 0]
##
21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6307] device (virbr0): state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Aug 24 21:03:05 ThinkCentre-M91p avahi-daemon[879]: Registering new address record for 192.168.122.1 on virbr0.IPv4.
Aug 24 21:03:05 ThinkCentre-M91p kernel: [   14.461921] virbr0: port 1(virbr0-nic) entered blocking state
Aug 24 21:03:05 ThinkCentre-M91p kernel: [   14.461923] virbr0: port 1(virbr0-nic) entered listening state
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6319] keyfile: add connection in-memory (8b9d5da7-9773-4e05-8413-1be61f276482,"virbr0")
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6323] device (virbr0): state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6329] device (virbr0): Activation: starting connection 'virbr0' (8b9d5da7-9773-4e05-8413-1be61f276482)
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6336] device (virbr0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6339] device (virbr0): state change: prepare -> config (reason 'none') [40 50 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6345] keyfile: add connection in-memory (70413b36-0c6a-4638-a554-437ba674b322,"virbr0-nic")
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6354] device (virbr0-nic): Activation: starting connection 'virbr0-nic' (70413b36-0c6a-4638-a554-437ba674b322)
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6354] device (virbr0): state change: config -> ip-config (reason 'none') [50 70 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6362] device (virbr0-nic): state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <warn>  [1503597785.6365] arping[0x5633ab4ab1a0,3]: arping could not be found; no ARPs will be sent
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6365] device (virbr0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6371] device (virbr0-nic): state change: prepare -> config (reason 'none') [40 50 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6374] device (virbr0-nic): state change: config -> ip-config (reason 'none') [50 70 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6375] device (virbr0): bridge port virbr0-nic was attached
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6375] device (virbr0-nic): Activation: connection 'virbr0-nic' enslaved, continuing activation
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6375] device (virbr0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6378] device (virbr0-nic): state change: ip-config -> secondaries (reason 'none') [70 90 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6379] device (virbr0): state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6406] device (virbr0): Activation: successful, device activated.
Aug 24 21:03:05 ThinkCentre-M91p nm-dispatcher: req:4 'up' [virbr0]: new request (1 scripts)
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6434] device (virbr0-nic): state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 24 21:03:05 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597785.6453] device (virbr0-nic): Activation: successful, device activated.
Aug 24 21:03:05 ThinkCentre-M91p nm-dispatcher: req:5 'up' [virbr0-nic]: new request (1 scripts)
Aug 24 21:03:05 ThinkCentre-M91p indicator-appli[1316]: Application already exists, re-requesting properties.
Aug 24 21:03:05 ThinkCentre-M91p indicator-appli[1316]: Application already exists, re-requesting properties.
##
21:03:06 ThinkCentre-M91p kernel: [   14.977856] virbr0: port 1(virbr0-nic) entered disabled state
Aug 24 21:03:06 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597786.1494] device (virbr0-nic): state change: activated -> unmanaged (reason 'connection-assumed') [100 10 41]
Aug 24 21:03:06 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597786.1505] device (virbr0): bridge port virbr0-nic was detached
Aug 24 21:03:06 ThinkCentre-M91p NetworkManager[885]: <info>  [1503597786.1506] device (virbr0-nic): released from master device virbr0
Aug 24 21:03:06 ThinkCentre-M91p nm-dispatcher: req:6 'down' [virbr0-nic]: new request (1 scripts)
##
22:16:00 ThinkCentre-M91p NetworkManager[885]: <info>  [1503602160.0494] manager: (macvtap0): new Macvlan device (/org/freedesktop/NetworkManager/Devices/4)
Aug 24 22:16:00 ThinkCentre-M91p NetworkManager[885]: <info>  [1503602160.0567] devices added (path: /sys/devices/virtual/net/macvtap0, iface: macvtap0)
Aug 24 22:16:00 ThinkCentre-M91p NetworkManager[885]: <info>  [1503602160.0567] device added (path: /sys/devices/virtual/net/macvtap0, iface: macvtap0): no ifupdown configuration found.
Aug 24 22:16:00 ThinkCentre-M91p libvirtd[984]: Domain id=1 name='VM-Development' uuid=813ff31b-460f-442a-8e40-a064eecab5f9 is tainted: high-privileges
22:16:01 ThinkCentre-M91p NetworkManager[885]: <info>  [1503602161.1647] manager: (macvtap1): new Macvlan device (/org/freedesktop/NetworkManager/Devices/5)
Aug 24 22:16:01 ThinkCentre-M91p NetworkManager[885]: <info>  [1503602161.1704] devices added (path: /sys/devices/virtual/net/macvtap1, iface: macvtap1)
Aug 24 22:16:01 ThinkCentre-M91p NetworkManager[885]: <info>  [1503602161.1704] device added (path: /sys/devices/virtual/net/macvtap1, iface: macvtap1): no ifupdown configuration 
 00:16:20 ThinkCentre-M91p NetworkManager[885]: <info>  [1503609380.4050] manager: (macvtap0): new Macvlan device (/org/freedesktop/NetworkManager/Devices/6)
Aug 25 00:16:20 ThinkCentre-M91p NetworkManager[885]: <info>  [1503609380.4138] devices added (path: /sys/devices/virtual/net/macvtap0, iface: macvtap0)
Aug 25 00:16:20 ThinkCentre-M91p NetworkManager[885]: <info>  [1503609380.4139] device added (path: /sys/devices/virtual/net/macvtap0, iface: macvtap0): no ifupdown configuration 
 00:16:22 ThinkCentre-M91p NetworkManager[885]: <info>  [1503609382.6401] manager: (macvtap1): new Macvlan device (/org/freedesktop/NetworkManager/Devices/7)
Aug 25 00:16:22 ThinkCentre-M91p NetworkManager[885]: <info>  [1503609382.6492] devices added (path: /sys/devices/virtual/net/macvtap1, iface: macvtap1)
Aug 25 00:16:22 ThinkCentre-M91p NetworkManager[885]: <info>  [1503609382.6493] device added (path: /sys/devices/virtual/net/macvtap1, iface: macvtap1): no ifupdown configuration 
 01:45:20 ThinkCentre-M91p NetworkManager[885]: <info>  [1503614720.8762] manager: (macvtap2): new Macvlan device (/org/freedesktop/NetworkManager/Devices/8)
Aug 25 01:45:20 ThinkCentre-M91p NetworkManager[885]: <info>  [1503614720.8900] devices added (path: /sys/devices/virtual/net/macvtap2, iface: macvtap2)
Aug 25 01:45:20 ThinkCentre-M91p NetworkManager[885]: <info>  [1503614720.8901] device added (path: /sys/devices/virtual/net/macvtap2, iface: macvtap2): no ifupdown configuration found.
Aug 25 01:45:21 ThinkCentre-M91p kernel: [16953.936858] audit: type=1400 audit(1503614721.325:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-f7e900a9-2540-48ce-9f99-acf17a5fb82e" pid=3622 comm="apparmor_parser"
Aug 25 01:45:21 ThinkCentre-M91p libvirtd[984]: Domain id=5 name='VM-Development_2' uuid=f7e900a9-2540-48ce-9f99-acf17a5fb82e is tainted: high-privileges
Aug 25 01:45:21 ThinkCentre-M91p libvirtd[984]: internal error: unknown CPU feature __kvm_hv_spinlocks
Aug 25 01:45:21 ThinkCentre-M91p NetworkManager[885]: <info>  [1503614721.5393] device (macvtap2): link connected
Aug 25 01:45:21 ThinkCentre-M91p virtlogd[2144]: End of file while reading data: Input/output error
Aug 25 01:45:22 ThinkCentre-M91p avahi-daemon[879]: Joining mDNS multicast group on interface macvtap2.IPv6 with address fe80::5054:ff:fe8a:82df.
Aug 25 01:45:22 ThinkCentre-M91p avahi-daemon[879]: New relevant interface macvtap2.IPv6 for mDNS.
Aug 25 01:45:22 ThinkCentre-M91p avahi-daemon[879]: Registering new address record for fe80::5054:ff:fe8a:82df on macvtap2.*.
Aug 25 01:59:38 ThinkCentre-M91p libvirtd[984]: internal error: End of file from qemu monitor
Aug 25 01:59:38 ThinkCentre-M91p virtlogd[2144]: End of file while reading data: Input/output error
02:05:57 ThinkCentre-M91p NetworkManager[885]: <info>  [1503615957.1813] devices removed (path: /sys/devices/virtual/net/macvtap2, iface: macvtap2)
Aug 25 02:05:57 ThinkCentre-M91p kernel: [18190.599431] audit: type=1400 audit(1503615957.673:41): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-f7e900a9-2540-48ce-9f99-acf17a5fb82e" pid=3769 comm="apparmor_parser"
Aug 25 02:05:57 ThinkCentre-M91p NetworkManager[885]: <info>  [1503615957.7044] manager: (macvtap0): new Macvlan device (/org/freedesktop/NetworkManager/Devices/9)
Aug 25 02:05:57 ThinkCentre-M91p NetworkManager[885]: <info>  [1503615957.7183] devices added (path: /sys/devices/virtual/net/macvtap0, iface: macvtap0)
Aug 25 02:05:57 ThinkCentre-M91p NetworkManager[885]: <info>  [1503615957.7183] device added (path: /sys/devices/virtual/net/macvtap0, iface: macvtap0): no ifupdown configuration found.
Aug 25 02:05:58 ThinkCentre-M91p libvirtd[984]: Domain id=6 name='VM-Development_2' uuid=f7e900a9-2540-48ce-9f99-acf17a5fb82e is tainted: high-privileges

```

##
is this happening while using Virtual machines , or is it on an actual ubuntu installation on the ThinkCenter ..

how you're connection with the wired ethernet cable.. is there a VPN connection, a connection using a bridge!? and since the thinkcenter doen't seem to have a wifi card , why is this happening :
[URL="https://paste.ubuntu.com/25387796/"]https://paste.ubuntu.com/25387796/
[/URL]
you're not using a wifi usb adapter the same time with the wired connection , or are you?! 
At firt i thought it might be the e1000e driver faults , while it could be, but now we seeing other stuff going on.. to troubleshoot this we need a clean slate of the system.
I read system logs quite a lot , but your system logs is rather confusing.. So if you care to explain your system configuration with Network setup, please do. Thanks!

---

### Post by itaroiu on 2017-08-26
Hi!
Thanks for your time...

I'm using this computer mostly for running some virtual machines on it. Indeed there was some problems in spinning up some virtual machines.
I can't tell this is happening on actual Ubuntu installation as I always used this system with Qemu virtualizer installed.
All my virtual machines are connected to my local networks using a bridge connection, to be able to access them through VNC, RDP or xrdp from my local network.

Regarding the wifi usb adapter, indeed I've test one device to see if I still get the system freezing, but no luck. I don't use lan adapter and wifi adapter in the same time. In fact I'm not using anymore the wifi usb adapter. I'm using only LAN adapter and I'm not using a VPN connection.

This is the listing of ifconfig -a, with 3 running virtual machines in bridge connections (macvtap0,macvtap1,macvtap2).
[https://paste.ubuntu.com/25398354/](https://paste.ubuntu.com/25398354/)

Thanks a lot!

---

### Post by Bashing-om on 2017-08-27
itaroiu; Ouch,

I do not know where to start to re-configure the VMs. The logs sure reflect that the system is not happy with the VM(s). Seems reasonable to verify ALL the config files for these VMs .

[INDENT][INDENT]I am not a know-it-all
[/INDENT][/INDENT]

---

### Post by BenginM on 2017-08-27
since when you deployed these virtual machines , and was this issue from the start or did it recently occurred! are you using KVM with QEMU+libvirt ? is secure boot option disabled in the BIOS. 

which version of QEMU and libvirt , and which kernel version currently in use? you mentioned this is in lubuntu 17, is it 17.04 or 10 to be exact!

Yes, we can see in the logs the instance of xrdp .. and we see several failures of libvirt and QEMU

references  :
[https://help.ubuntu.com/community/Installation/QemuEmulator](https://help.ubuntu.com/community/Installation/QemuEmulator)
[https://help.ubuntu.com/lts/serverguide/qemu.html](https://help.ubuntu.com/lts/serverguide/qemu.html)
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

---

### Post by itaroiu on 2017-08-30
Hi BenginM,
Yes I'm using KVM with QEMU+libvirt, and I always used this configuration with the same running virtual machines ad always have had this problem. I'm using also xrdp when need to access the computer remotely.
Now, my luck is that I've hadn't any issue for 3 days, and this is a record ;)

Current configuration:
   QEMU version:
   Libvirt version: 2.5.0
   Lubuntu version: 17.04
   Kernel: Linux 4.10.0-32-generic (x86_64)

This is my complete computer report:
[https://paste.ubuntu.com/25430433/](https://paste.ubuntu.com/25430433/)

In the next days I'll take into consideration a new fresh install of Lubuntu or Ubuntu server and go with another network settings for my virtual machines, because as I understood this problem can be due of virtual interface when connecting through bridge.

Thanks a lot for your time!

---

### Post by BenginM on 2017-09-03
Hiya itaroiu, Yes good idea to start with a clean slate .. check those links above and this one might be of help as well
[https://help.ubuntu.com/lts/serverguide/libvirt.html](https://help.ubuntu.com/lts/serverguide/libvirt.html)

tell us how it goes, hopefully it goes well this time :)

---

