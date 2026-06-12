---
title: "Booting Problem after the Mother replacement"
date: 2013-01-25
forum: General Help
---

### Post by 1991sudarshan on 2013-01-25
I have a dual boot : Kubuntu 10.04 and Windows Xp. Some days my ASUS P5KPL-AM/PS failed and a got a new mother board ASROCK G41M-VS3 and Transcend DDR3 2GB ram previously I had transcend DDR2 2GB ram.

The problem is, Kubuntu is not booting where as the windows xp is working fine. I got these messages during many restarts. The Data are fine in the Hard Disk. I have no clue how to deal with this issue.  

These are the messages I got while booting Kubuntu 10.04

EDIT

memory test error 

```

**error: too small lower memory (0x99100 > 0x97800)**

**press any key to continue**..


```

---

### Post by Calinou on 2013-01-25
Try updating your BIOS from Windows XP maybe?

ASROCK motherboards... :-D

---

### Post by Starfleet on 2013-01-25
Not completely sure but I suspect you may have a driver issue associated with the new motherboard. Are you using onboard grahics? Or have you a dedicated grahics card? If so, which card do you have and is it Radeon or Nvidea? Grahics drivers are quite well known to cause boot problems with an array of messages often coming up. Windows will normally sort itself out a new driver ok but Kubuntu will need help to install the new driver.

---

### Post by 1991sudarshan on 2013-01-25
> **Calinou said:**
> Try updating your BIOS from Windows XP maybe?

ASROCK motherboards... :-D

I will try that. I forgot to mention the error that I got during the memtest 

memory test error 
```

**error: too small lower memory (0x99100 > 0x97800)**

**press any key to continue**..


```

---

### Post by 1991sudarshan on 2013-01-25
DDR#> **Starfleet said:**
> Not completely sure but I suspect you may have a driver issue associated with the new motherboard. Are you using onboard grahics? Or have you a dedicated grahics card? If so, which card do you have and is it Radeon or Nvidea? Grahics drivers are quite well known to cause boot problems with an array of messages often coming up. Windows will normally sort itself out a new driver ok but Kubuntu will need help to install the new driver.

No onboard graphics. Along with the ASROCK board i have got a new 2G DDR3 Transcend  ram. At times kubuntu goes to boot screen and gets struck there  loading continuously.

---

### Post by Mark Phelps on 2013-01-25
Wish folks would stop telling others to update their BIOS for routine problems.  If you make a mistake updating the BIOS, you wne up with an "electric brick!

It's likely a video driver problem -- which, since you do NOT have onboard graphics, BIOS updating is unlikely to fix.

You didn't tell us the make and model video card.  That would be helpful for us to know.

---

### Post by 1991sudarshan on 2013-01-25
> **Mark Phelps said:**
> 

You didn't tell us the make and model video card.  That would be helpful for us to know.

This is the Graphic Specification given in the manual book and online  
```

Intel® Graphics Media Accelerator X4500,
 Pixel Shader 4.0, DirectX 10,
 Max. shared memory 1759MB 
supports D-sub with max, resolution upto 2048x1536 @ 75 Hz

```

The boot screen of Kubuntu appeared in a large resolution. You can see in the third pic in the opening post

---

### Post by windscape on 2013-01-25
Hi,

It might be that the integrated video controller is stealing too much memory from the BIOS for some reason. Try going into the BIOS settings and changing the amount of video memory assigned to the video controller. For details on doing that, consult the motherboard manual.

---

### Post by 1991sudarshan on 2013-01-26
> **windscape said:**
> Hi,

It might be that the integrated video controller is stealing too much memory from the BIOS for some reason. Try going into the BIOS settings and changing the amount of video memory assigned to the video controller. For details on doing that, consult the motherboard manual.

Thanks, the boot problem is solved for now, The memory was in AUTO option in the bios and I changed it to 64 MB and the booting and login are fine.  But now the ethernet port is now getting detected.

---

### Post by orb9220 on 2013-01-26
> "But now the ethernet port is now getting detected."

Good thing? Bad Thing? Be more specific with your problems.

You mean hangs at booting? errrors?

Need ethernet for your internet? If not also may be able to disable ethernet in the bios. 
But most need ethernet for their home networks or connecting to their router for internet.
.

---

### Post by 1991sudarshan on 2013-01-26
> **orb9220 said:**
> Good thing? Bad Thing? Be more specific with your problems.

You mean hangs at booting? errrors?

Need ethernet for your internet? If not also may be able to disable ethernet in the bios. 
But most need ethernet for their home networks or connecting to their router for internet.
.

I am posting this and the previous thread from my netbook . I went through some thread about the ethernet issues after the mother board replacement.  I tried some commands and I am posting the terminal output here 

```
kevin@kevin-desktop:~$ ifconfig eth0
eth0: error fetching interface information: Device not found
kevin@kevin-desktop:~$ 
```
```
kevin@kevin-desktop:~$ less /var/log/syslog | grep eth0
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 12:49:12 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan 19 12:49:12 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 12:49:12 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 12:49:12 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 19 12:49:15 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 12:49:15 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 19 12:49:15 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 12:49:15 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 12:49:15 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 12:49:15 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 12:49:15 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 12:49:15 kevin-desktop avahi-daemon[876]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 12:49:15 kevin-desktop avahi-daemon[876]: New relevant interface eth0.IPv4 for mDNS.
Jan 19 12:49:15 kevin-desktop avahi-daemon[876]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan 19 12:49:16 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 19 12:49:16 kevin-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 19 12:49:16 kevin-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 19 12:49:16 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 12:53:52 kevin-desktop kernel: [  907.878172] r8169: eth0: link down
Jan 19 12:53:52 kevin-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 19 12:53:53 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Jan 19 12:53:53 kevin-desktop kernel: [  909.815978] r8169: eth0: link up
Jan 19 19:04:48 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 19 19:04:48 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 19 19:04:48 kevin-desktop kernel: [    0.799578] eth0: RTL8168c/8111c at 0xf8044000, 00:24:8c:e5:a1:ac, XID 1c4000c0 IRQ 26
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): now managed
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): preparing device.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 19:04:48 kevin-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 19 19:04:48 kevin-desktop kernel: [   16.834518] r8169: eth0: link up
Jan 19 19:04:48 kevin-desktop kernel: [   16.834523] r8169: eth0: link up
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 19:04:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 19:04:49 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 19 19:04:49 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 19:04:49 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 19:04:50 kevin-desktop avahi-daemon[881]: Registering new address record for fe80::224:8cff:fee5:a1ac on eth0.*.
Jan 19 19:04:52 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan 19 19:04:54 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 19:04:54 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 19 19:04:54 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 19:04:54 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 19:04:54 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 19:04:54 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 19:04:54 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 19:04:54 kevin-desktop avahi-daemon[881]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 19:04:54 kevin-desktop avahi-daemon[881]: New relevant interface eth0.IPv4 for mDNS.
Jan 19 19:04:54 kevin-desktop avahi-daemon[881]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan 19 19:04:55 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 19 19:04:55 kevin-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 19 19:04:55 kevin-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 19 19:04:55 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 19:04:59 kevin-desktop kernel: [   27.032511] eth0: no IPv6 routers present
Jan 19 21:31:13 kevin-desktop kernel: [    0.804216] eth0: RTL8168c/8111c at 0xf8044000, 00:24:8c:e5:a1:ac, XID 1c4000c0 IRQ 26
Jan 19 21:31:13 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 19 21:31:13 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): now managed
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): preparing device.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 21:31:13 kevin-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 19 21:31:13 kevin-desktop kernel: [   17.273999] r8169: eth0: link up
Jan 19 21:31:13 kevin-desktop kernel: [   17.274003] r8169: eth0: link up
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:31:13 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 19 21:31:13 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:31:13 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:31:15 kevin-desktop avahi-daemon[866]: Registering new address record for fe80::224:8cff:fee5:a1ac on eth0.*.
Jan 19 21:31:17 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 19 21:33:00 kevin-desktop kernel: [    0.787254] eth0: RTL8168c/8111c at 0xf8044000, 00:24:8c:e5:a1:ac, XID 1c4000c0 IRQ 26
Jan 19 21:33:00 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 19 21:33:00 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 19 21:33:00 kevin-desktop kernel: [   17.284185] r8169: eth0: link up
Jan 19 21:33:00 kevin-desktop kernel: [   17.284191] r8169: eth0: link up
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): now managed
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): preparing device.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 21:33:00 kevin-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:33:00 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 19 21:33:00 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:33:00 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:33:01 kevin-desktop avahi-daemon[831]: Registering new address record for fe80::224:8cff:fee5:a1ac on eth0.*.
Jan 19 21:33:03 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 19 21:33:10 kevin-desktop kernel: [   27.428019] eth0: no IPv6 routers present
Jan 19 21:33:11 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan 19 21:33:23 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 19 21:33:30 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 19 21:33:44 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Jan 19 21:33:45 kevin-desktop kernel: [   61.952352] r8169: eth0: link down
Jan 19 21:33:45 kevin-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 890
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  Activation (eth0) failed.
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Jan 19 21:33:46 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jan 19 21:33:47 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 3)
Jan 19 21:33:47 kevin-desktop kernel: [   63.910790] r8169: eth0: link up
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:35:03 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan 19 21:35:03 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:35:03 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:35:06 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 19 21:35:08 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:35:08 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 19 21:35:08 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 21:35:08 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 21:35:08 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 21:35:08 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 21:35:08 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 21:35:08 kevin-desktop avahi-daemon[831]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 21:35:08 kevin-desktop avahi-daemon[831]: New relevant interface eth0.IPv4 for mDNS.
Jan 19 21:35:08 kevin-desktop avahi-daemon[831]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan 19 21:35:09 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 19 21:35:09 kevin-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 19 21:35:09 kevin-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 19 21:35:09 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 21:54:09 kevin-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 3 (reason 0)
Jan 19 21:54:09 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1775
Jan 19 21:54:10 kevin-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 19 21:54:10 kevin-desktop avahi-daemon[831]: Withdrawing address record for 192.168.1.2 on eth0.
Jan 19 21:54:10 kevin-desktop avahi-daemon[831]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 21:54:10 kevin-desktop avahi-daemon[831]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:54:10 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan 19 21:54:10 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:54:10 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:54:13 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:54:20 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:54:34 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 19 21:54:38 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 19 21:54:38 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 3 (reason 0)
Jan 19 21:54:38 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2096
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:54:39 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan 19 21:54:39 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:54:39 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:54:39 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:54:44 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:54:55 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 19 21:55:03 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 3 (reason 0)
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2118
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:55:05 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan 19 21:55:05 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:55:05 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:55:07 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:55:14 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:55:28 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 19 21:57:13 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 19 21:57:13 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 19 21:57:13 kevin-desktop kernel: [    0.789212] eth0: RTL8168c/8111c at 0xf8044000, 00:24:8c:e5:a1:ac, XID 1c4000c0 IRQ 26
Jan 19 21:57:13 kevin-desktop kernel: [   18.703916] r8169: eth0: link up
Jan 19 21:57:13 kevin-desktop kernel: [   18.703920] r8169: eth0: link up
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): now managed
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): preparing device.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 21:57:13 kevin-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 21:57:13 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 19 21:57:13 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:57:13 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 21:57:15 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 19 21:57:15 kevin-desktop avahi-daemon[886]: Registering new address record for fe80::224:8cff:fee5:a1ac on eth0.*.
Jan 19 21:57:17 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 21:57:17 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 19 21:57:17 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 21:57:17 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 21:57:17 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 21:57:17 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 21:57:17 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 21:57:17 kevin-desktop avahi-daemon[886]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 21:57:17 kevin-desktop avahi-daemon[886]: New relevant interface eth0.IPv4 for mDNS.
Jan 19 21:57:17 kevin-desktop avahi-daemon[886]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan 19 21:57:18 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 19 21:57:18 kevin-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 19 21:57:18 kevin-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 19 21:57:18 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 22:00:26 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 19 22:00:26 kevin-desktop kernel: [    0.785472] eth0: RTL8168c/8111c at 0xf8044000, 00:24:8c:e5:a1:ac, XID 1c4000c0 IRQ 26
Jan 19 22:00:26 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): now managed
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): preparing device.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 22:00:26 kevin-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 19 22:00:26 kevin-desktop kernel: [   17.260913] r8169: eth0: link up
Jan 19 22:00:26 kevin-desktop kernel: [   17.260917] r8169: eth0: link up
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 22:00:26 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 19 22:00:26 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 22:00:26 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 22:00:26 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 19 22:00:26 kevin-desktop avahi-daemon[859]: Registering new address record for fe80::224:8cff:fee5:a1ac on eth0.*.
Jan 19 22:00:28 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 22:00:28 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 19 22:00:28 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 22:00:28 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 22:00:28 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 22:00:28 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 22:00:28 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 22:00:28 kevin-desktop avahi-daemon[859]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 22:00:28 kevin-desktop avahi-daemon[859]: New relevant interface eth0.IPv4 for mDNS.
Jan 19 22:00:28 kevin-desktop avahi-daemon[859]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan 19 22:00:29 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 19 22:00:29 kevin-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 19 22:00:29 kevin-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 19 22:00:29 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 22:00:38 kevin-desktop kernel: [   27.832013] eth0: no IPv6 routers present
Jan 19 22:49:45 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 19 22:49:45 kevin-desktop kernel: [    0.800424] eth0: RTL8168c/8111c at 0xf8044000, 00:24:8c:e5:a1:ac, XID 1c4000c0 IRQ 26
Jan 19 22:49:45 kevin-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): now managed
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): preparing device.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 22:49:45 kevin-desktop kernel: [   17.104128] r8169: eth0: link up
Jan 19 22:49:45 kevin-desktop kernel: [   17.104132] r8169: eth0: link up
Jan 19 22:49:45 kevin-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 22:49:45 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 19 22:49:45 kevin-desktop dhclient: Listening on LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 22:49:45 kevin-desktop dhclient: Sending on   LPF/eth0/00:24:8c:e5:a1:ac
Jan 19 22:49:46 kevin-desktop avahi-daemon[849]: Registering new address record for fe80::224:8cff:fee5:a1ac on eth0.*.
Jan 19 22:49:48 kevin-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 19 22:49:48 kevin-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan 19 22:49:48 kevin-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 19 22:49:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 22:49:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 22:49:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 22:49:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 22:49:48 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 22:49:48 kevin-desktop avahi-daemon[849]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan 19 22:49:48 kevin-desktop avahi-daemon[849]: New relevant interface eth0.IPv4 for mDNS.
Jan 19 22:49:48 kevin-desktop avahi-daemon[849]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan 19 22:49:49 kevin-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 19 22:49:49 kevin-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 19 22:49:49 kevin-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 19 22:49:49 kevin-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 22:49:55 kevin-desktop kernel: [   27.484015] eth0: no IPv6 routers present
Jan 19 22:51:12 kevin-desktop kernel: [  104.197689] r8169: eth0: link down
Jan 19 22:51:12 kevin-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 19 22:51:14 kevin-desktop kernel: [  105.996413] r8169: eth0: link up
Jan 19 22:51:14 kevin-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 8)
kevin@kevin-desktop:~$ 
```
```
kevin@kevin-desktop:~$ ifconfig -a 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:170226 (170.2 KB)  TX bytes:170226 (170.2 KB)

kevin@kevin-desktop:~$ 

```
```
kevin@kevin-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
kevin@kevin-desktop:~$ 
``````
kevin@kevin-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)
kevin@kevin-desktop:~$ 


```

---

### Post by 1991sudarshan on 2013-01-26
I run the same commands under lives session Kubuntu 11.10

```
ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:7c:f0:43  
          inet6 addr: fe80::be5f:f4ff:fe7c:f043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11970 (11.9 KB)
          Interrupt:43 

ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ less /var/log/syslog | grep eth0
Jan 26 13:47:30 ubuntu NetworkManager[1824]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Jan 26 13:47:30 ubuntu NetworkManager[1824]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): carrier is OFF
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): new Ethernet device (driver: 'atl1c' ifindex: 2)
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): now managed
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): bringing up device.
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): preparing device.
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): deactivating device (reason: 2).
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Jan 26 13:47:30 ubuntu kernel: [   70.629437] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): carrier now ON (device state 2)
Jan 26 13:47:30 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) starting connection 'Auto eth0'
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 26 13:47:31 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 26 13:47:32 ubuntu avahi-daemon[1650]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::be5f:f4ff:fe7c:f043.
Jan 26 13:47:32 ubuntu avahi-daemon[1650]: New relevant interface eth0.IPv6 for mDNS.
Jan 26 13:47:32 ubuntu avahi-daemon[1650]: Registering new address record for fe80::be5f:f4ff:fe7c:f043 on eth0.*.
Jan 26 13:47:32 ubuntu NetworkManager[1824]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan 26 13:47:32 ubuntu dhclient: Listening on LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:47:32 ubuntu dhclient: Sending on   LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:47:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:47:35 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan 26 13:47:40 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 26 13:47:41 ubuntu kernel: [   81.016007] eth0: no IPv6 routers present
Jan 26 13:47:46 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Jan 26 13:48:03 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan 26 13:48:15 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <warn> (eth0): DHCPv4 request timed out.
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1869
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Marking connection 'Auto eth0' invalid.
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <warn> Activation (eth0) failed.
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jan 26 13:48:17 ubuntu NetworkManager[1824]: <info> (eth0): deactivating device (reason: 0).
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) starting connection 'Auto eth0'
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 26 13:49:57 ubuntu NetworkManager[1824]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan 26 13:49:57 ubuntu dhclient: Listening on LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:49:57 ubuntu dhclient: Sending on   LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:49:57 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:50:00 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 26 13:50:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan 26 13:50:07 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 7 -> 3 (reason 0)
Jan 26 13:50:07 ubuntu NetworkManager[1824]: <info> (eth0): deactivating device (reason: 0).
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4557
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) starting connection 'Auto eth0'
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 26 13:50:08 ubuntu NetworkManager[1824]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan 26 13:50:08 ubuntu dhclient: Listening on LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:50:08 ubuntu dhclient: Sending on   LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:50:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:50:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:50:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 26 13:50:22 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Jan 26 13:50:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan 26 13:50:47 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <warn> (eth0): DHCPv4 request timed out.
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4559
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Marking connection 'Auto eth0' invalid.
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <warn> Activation (eth0) failed.
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jan 26 13:50:53 ubuntu NetworkManager[1824]: <info> (eth0): deactivating device (reason: 0).
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) starting connection 'Auto eth0'
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 26 13:51:04 ubuntu NetworkManager[1824]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan 26 13:51:04 ubuntu dhclient: Listening on LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:51:04 ubuntu dhclient: Sending on   LPF/eth0/bc:5f:f4:7c:f0:43
Jan 26 13:51:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:51:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 26 13:51:13 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 26 13:51:20 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 26 13:51:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 26 13:51:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <warn> (eth0): DHCPv4 request timed out.
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4630
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Marking connection 'Auto eth0' invalid.
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <warn> Activation (eth0) failed.
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jan 26 13:51:50 ubuntu NetworkManager[1824]: <info> (eth0): deactivating device (reason: 0).
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="bc:5f:f4:7c:f0:43", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
ubuntu@ubuntu:~$ 
```


```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: bc:5f:f4:7c:f0:43
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:febc0000-febfffff ioport:ec00(size=128)
ubuntu@ubuntu:~$ 
```

---

