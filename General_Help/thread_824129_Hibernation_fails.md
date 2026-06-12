---
title: "Hibernation fails"
date: 2008-06-09
forum: General Help
---

### Post by AVH on 2008-06-09
When I try to hibernate my machine the screen goes blank and then comes right back again with the message "Hibernation Failed" (after I have to enter my password again).

here are my Message log and Syslog from when I selected 'hibernate' from the shut down menu:

Message log:

> Jun  9 19:48:36 alan-u-livingroom dhcdbd: Unrequested down ?:3
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.417253] sis900.c: v1.08.10 Apr. 2 2006
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.420913] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.431983] 0000:00:04.0: Using transceiver found at address 1 as default
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.473137] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 20, 00:17:31:7a:09:1b.
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.540609] input: Power Button (FF) as /class/input/input8
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.556079] ACPI: Power Button (FF) [PWRF]
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.596307] input: Power Button (CM) as /class/input/input9
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.611686] ACPI: Power Button (CM) [PWRB]
Jun  9 19:48:40 alan-u-livingroom kernel: [  655.486489] eth0: Media Link On 100mbps full-duplex 
Jun  9 19:48:40 alan-u-livingroom kernel: [  655.976431] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun  9 19:48:40 alan-u-livingroom kernel: [  655.976725] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun  9 19:48:41 alan-u-livingroom dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  9 19:48:41 alan-u-livingroom dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  9 19:48:51 alan-u-livingroom gnome-power-manager: (alan) Resuming computer
Jun  9 19:48:51 alan-u-livingroom gnome-power-manager: (alan) hibernate failed

Syslog:

> Jun  9 19:48:36 alan-u-livingroom dhcdbd: Unrequested down ?:3
Jun  9 19:48:36 alan-u-livingroom NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Jun  9 19:48:36 alan-u-livingroom avahi-daemon[5571]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  9 19:48:36 alan-u-livingroom avahi-daemon[5571]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Jun  9 19:48:36 alan-u-livingroom avahi-daemon[5571]: Withdrawing address record for fe80::217:31ff:fe7a:91b on eth0.
Jun  9 19:48:36 alan-u-livingroom avahi-daemon[5571]: Withdrawing address record for 192.168.1.101 on eth0.
Jun  9 19:48:36 alan-u-livingroom NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jun  9 19:48:36 alan-u-livingroom NetworkManager: <info>  Deactivating device eth0. 
Jun  9 19:48:36 alan-u-livingroom NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jun  9 19:48:36 alan-u-livingroom NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jun  9 19:48:36 alan-u-livingroom NetworkManager: <debug> [1213055316.616375] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_17_31_7a_09_1b'). 
Jun  9 19:48:36 alan-u-livingroom NetworkManager: <info>  Deactivating device eth0. 
Jun  9 19:48:37 alan-u-livingroom kernel: [  653.131451] PM: suspend-to-disk mode set to 'shutdown'
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.417253] sis900.c: v1.08.10 Apr. 2 2006
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.420913] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.431983] 0000:00:04.0: Using transceiver found at address 1 as default
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <debug> [1213055318.241825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_17_31_7a_09_1b'). 
Jun  9 19:48:38 alan-u-livingroom kernel: [  653.473137] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 20, 00:17:31:7a:09:1b.
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  eth0: Device is fully-supported using driver 'sis900'. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Deactivating device eth0. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Will activate connection 'eth0'. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Device eth0 activation scheduled... 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) started... 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jun  9 19:48:38 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jun  9 19:48:39 alan-u-livingroom NetworkManager: <debug> [1213055319.229117] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Jun  9 19:48:39 alan-u-livingroom NetworkManager: <debug> [1213055319.244540] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.540609] input: Power Button (FF) as /class/input/input8
Jun  9 19:48:39 alan-u-livingroom NetworkManager: <debug> [1213055319.414597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.556079] ACPI: Power Button (FF) [PWRF]
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.596307] input: Power Button (CM) as /class/input/input9
Jun  9 19:48:39 alan-u-livingroom NetworkManager: <debug> [1213055319.470287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Jun  9 19:48:39 alan-u-livingroom kernel: [  654.611686] ACPI: Power Button (CM) [PWRB]
Jun  9 19:48:40 alan-u-livingroom kernel: [  655.486489] eth0: Media Link On 100mbps full-duplex 
Jun  9 19:48:40 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jun  9 19:48:40 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jun  9 19:48:40 alan-u-livingroom NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jun  9 19:48:40 alan-u-livingroom kernel: [  655.976431] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun  9 19:48:40 alan-u-livingroom kernel: [  655.976725] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun  9 19:48:41 alan-u-livingroom anacron[8177]: Anacron 2.3 started on 2008-06-09
Jun  9 19:48:41 alan-u-livingroom anacron[8177]: Normal exit (0 jobs run)
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jun  9 19:48:41 alan-u-livingroom dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun  9 19:48:41 alan-u-livingroom dhclient: DHCPACK from 192.168.1.1
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: New relevant interface eth0.IPv4 for mDNS.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jun  9 19:48:41 alan-u-livingroom dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  9 19:48:41 alan-u-livingroom dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    address 192.168.1.101 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    netmask 255.255.255.0 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    broadcast 192.168.1.255 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    gateway 192.168.1.1 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    nameserver 68.87.77.130 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    nameserver 68.87.72.130 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    hostname 'alan-u-livingroom' 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>    domain name 'hsd1.mi.comcast.net.' 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jun  9 19:48:41 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Withdrawing address record for 192.168.1.101 on eth0.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: New relevant interface eth0.IPv4 for mDNS.
Jun  9 19:48:41 alan-u-livingroom avahi-daemon[5571]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Jun  9 19:48:41 alan-u-livingroom dhclient: bound to 192.168.1.101 -- renewal in 35996 seconds.
Jun  9 19:48:42 alan-u-livingroom NetworkManager: <info>  Clearing nscd hosts cache. 
Jun  9 19:48:42 alan-u-livingroom NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jun  9 19:48:42 alan-u-livingroom NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jun  9 19:48:42 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jun  9 19:48:42 alan-u-livingroom NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  9 19:48:43 alan-u-livingroom ntpdate[8246]: adjust time server 91.189.94.4 offset -0.042304 sec
Jun  9 19:48:44 alan-u-livingroom avahi-daemon[5571]: Registering new address record for fe80::217:31ff:fe7a:91b on eth0.*.
Jun  9 19:48:51 alan-u-livingroom gnome-power-manager: (alan) Resuming computer
Jun  9 19:48:51 alan-u-livingroom gnome-power-manager: (alan) hibernate failed
Jun  9 19:48:53 alan-u-livingroom kernel: [  668.321143] eth0: no IPv6 routers present

---

### Post by AVH on 2008-06-09
Sorry about the way the previous post reads. I tried to put the logs into quote boxes, but apparently I don't know how.

---

### Post by iaculallad on 2008-06-09
Did you create a SWAP partition in you're Ubuntu installation?

---

### Post by AVH on 2008-06-09
yes. Here is the output of fdisl -l

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14692   118013458+   7  HPFS/NTFS
/dev/sda2           14694       15216     4200997+  82  Linux swap / Solaris
/dev/sda3           15217       19177    31816732+  83  Linux
alan@alan-u-livingroom:~$ 

```

---

### Post by iaculallad on 2008-06-09
Create a backup of your /etc/acpi/lid.sh file:

```
sudo cp /etc/acpi/lid.sh /etc/acpi/lid.sh.original
```

Open the file for editing:

```
sudo gedit /etc/acpi/lid.sh
```

And select all text within your /lid.sh file and delete it. Replace it with the text below and save.

```
#!/bin/sh
  sudo hibernate

```

---

### Post by AVH on 2008-06-09
Same result.

---

