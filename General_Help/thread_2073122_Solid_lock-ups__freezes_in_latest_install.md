---
title: "Solid lock-ups / freezes in latest install"
date: 2012-10-19
forum: General Help
---

### Post by mdifabio on 2012-10-19
I am stuck.  PLEASE HELP!

I thought that I had hardware problems on my backend server on 11.10 when it kept freezing up after long reliable use (old hardware).  So I upgraded mobo to GA-970A-DS3 w/ triple core AMD processor.

After such a major change, I figured that I might as well install 12.04 since I was virtually starting over anyway.  After many installs, I just can't get the backend working again.  It continues to randomly freeze up.  I am talking the kind of freezes that allow no mouse movement and no ssh 'ing, requiring a complete hard reset (by hitting the reset button on the case).

I have a suspision that the lock ups are coming due to something related to networking, but I can't be sure.  I can install Mythbuntu as a backend, and I can install a frontend, but I can't make a successful connection.  The frontend does not lock up or freeze, but the backend does.  I even tried a networking card as opposed to the onboard lan, but no better.

Following are some logs that I hope can help you help me.  Did I mention that I am not an expert...

These two were from the backend prior to a freeze:

difabio@Backend:~$ sudo tail -f /var/log/syslog
[sudo] password for difabio:
Oct 17 19:56:08 Backend NetworkManager[1053]: <info> (eth0): DHCPv4 state change                                                      d bound -> renew
Oct 17 19:56:08 Backend NetworkManager[1053]: <info>   address 192.168.15.32
Oct 17 19:56:08 Backend NetworkManager[1053]: <info>   prefix 24 (255.255.255.0)
Oct 17 19:56:08 Backend NetworkManager[1053]: <info>   gateway 192.168.15.1
Oct 17 19:56:08 Backend NetworkManager[1053]: <info>   hostname 'Backend'
Oct 17 19:56:08 Backend NetworkManager[1053]: <info>   nameserver '192.168.15.1'
Oct 17 19:56:08 Backend NetworkManager[1053]: <info>   domain name 'local.tld'
Oct 17 19:56:08 Backend dbus[1016]: [system] Activating service name='org.freede                                                      sktop.nm_dispatcher' (using servicehelper)
Oct 17 19:56:08 Backend dbus[1016]: [system] Successfully activated service 'org                                                      .freedesktop.nm_dispatcher'
Oct 17 20:01:03 Backend kernel: [ 1841.971207] tda9887 1-0043: i2c i/o error: rc                                                       == -6 (should be 4)
Oct 17 20:05:22 Backend anacron[1139]: Job `cron.daily' terminated (mailing output)
Oct 17 20:05:22 Backend anacron[1139]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Oct 17 20:05:22 Backend anacron[1139]: Job `cron.weekly' started
Oct 17 20:05:22 Backend anacron[4953]: Updated timestamp for job `cron.weekly' to 2012-10-17
Oct 17 20:05:26 Backend mythtv-database[4976]: mythconverg checked and backedup.
Oct 17 20:05:26 Backend anacron[1139]: Job `cron.weekly' terminated
Oct 17 20:05:26 Backend anacron[1139]: Job `cron.monthly' started
Oct 17 20:05:26 Backend anacron[1139]: Job `cron.monthly' terminated
Oct 17 20:05:26 Backend anacron[1139]: Normal exit (3 jobs run)
Oct 17 20:05:26 Backend anacron[4981]: Updated timestamp for job `cron.monthly' to 2012-10-17


and:

difabio@Backend:~$ sudo tail -f /var/log/dmesg
[sudo] password for difabio:
[   15.432788] type=1400 audit(1350527436.641:11): apparmor="STATUS" operation="                                                      profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1083 c                                                      omm="apparmor_parser"
[   15.432996] type=1400 audit(1350527436.641:12): apparmor="STATUS" operation="                                                      profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1083 comm="                                                      apparmor_parser"
[   15.434918] type=1400 audit(1350527436.641:13): apparmor="STATUS" operation="                                                      profile_replace" name="/usr/sbin/ntpd" pid=1085 comm="apparmor_parser"
[   15.475108] type=1400 audit(1350527436.681:14): apparmor="STATUS" operation="                                                      profile_load" name="/usr/sbin/mysqld" pid=1084 comm="apparmor_parser"
[   15.483499] type=1400 audit(1350527436.689:15): apparmor="STATUS" operation="                                                      profile_load" name="/usr/sbin/tcpdump" pid=1087 comm="apparmor_parser"
[   15.513637] type=1400 audit(1350527436.721:16): apparmor="STATUS" operation="                                                      profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=                                                      1082 comm="apparmor_parser"
[   15.890098] init: alsa-restore main process (1124) terminated with status 99
[   15.902195] type=1400 audit(1350527437.109:17): apparmor="STATUS" operation="                                                      profile_replace" name="/usr/sbin/mysqld" pid=1146 comm="apparmor_parser"
[   16.123608] r8169 0000:03:00.0: eth0: link up
[   16.123920] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


Here are two more:

difabio@Backend:~$ sudo tail -f /var/log/dmesg
[sudo] password for difabio:
[   11.586029] cx88[1]/2: found at 0000:04:07.2, rev: 5, irq: 21, latency: 32, m                                                      mio: 0xf6000000
[   11.589847] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   11.589850] cx88/2: registering cx8802 driver, type: dvb access: shared
[   11.589853] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=                                                      47]
[   11.589855] cx88[0]/2: cx2388x based DVB/ATSC card
[   11.589860] cx8802_alloc_frontends() allocating 1 frontend(s)
[   11.713411] r8169 0000:03:00.0: eth0: link down
[   11.713416] r8169 0000:03:00.0: eth0: link down
[   11.713787] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.714042] ADDRCONF(NETDEV_UP): eth0: link is not ready

and:

difabio@Backend:~$ sudo tail -f /var/log/syslog
[sudo] password for difabio:
Sorry, try again.
[sudo] password for difabio:
Oct 18 21:40:39 Backend ntpd[2105]: Listen normally on 3 eth0 192.168.15.32 UDP                                                       123
Oct 18 21:40:39 Backend ntpd[2105]: Listen normally on 4 eth0 fe80::6670:2ff:fe0                                                      4:e1bc UDP 123
Oct 18 21:40:39 Backend ntpd[2105]: Listen normally on 5 lo ::1 UDP 123
Oct 18 21:40:39 Backend ntpd[2105]: peers refreshed
Oct 18 21:40:39 Backend ntpd[2105]: Listening on routing socket on fd #22 for in                                                      terface updates
Oct 18 21:40:43 Backend NetworkManager[1027]: <info> (eth0): IP6 addrconf timed                                                       out or failed.
Oct 18 21:40:43 Backend NetworkManager[1027]: <info> Activation (eth0) Stage 4 o                                                      f 5 (IPv6 Configure Timeout) scheduled...
Oct 18 21:40:43 Backend NetworkManager[1027]: <info> Activation (eth0) Stage 4 o                                                      f 5 (IPv6 Configure Timeout) started...
Oct 18 21:40:43 Backend NetworkManager[1027]: <info> Activation (eth0) Stage 4 o                                                      f 5 (IPv6 Configure Timeout) complete.
Oct 18 21:40:51 Backend ntpd_intres[1058]: parent died before we finished, exiti                                                      ng
Oct 18 21:44:45 Backend dbus[965]: [system] Activating service name='com.mythbuntu.ControlCentre' (using servicehelper)
Oct 18 21:44:45 Backend dbus[965]: [system] Successfully activated service 'com.mythbuntu.ControlCentre'
Oct 18 21:46:15 Backend kernel: [  367.353776] init: mythtv-backend main process (2039) killed by TERM signal
Oct 18 21:46:47 Backend kernel: [  398.766967] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
Oct 18 21:50:19 Backend anacron[979]: Job `cron.weekly' started
Oct 18 21:50:19 Backend anacron[2823]: Updated timestamp for job `cron.weekly' to 2012-10-18


The backend logs did not give me a whole lot so I tried to see what the frontend said at the point that the backend crashed.  Here is that:

difabio@Frontend-2:~$ sudo tail -n 100 /var/log/dmesg
[sudo] password for difabio:
[   42.313756] NV_TCO: Watchdog reboot not detected.
[   42.313852] NV_TCO: initialized (0x4440). heartbeat=30 sec (nowayout=0)
[   42.316067] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   42.319187] EDAC amd64: DRAM ECC disabled.
[   42.319197] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   42.319198]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   42.319199]  (Note that use of the override may cause unknown side effects.)
[   42.319419] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 18
[   42.319441] nvidia 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 18 (level, low) -> IRQ 18
[   42.319451] nvidia 0000:03:00.0: setting latency timer to 64
[   42.319457] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   42.320894] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.48  Sun Sep  9 20:22:27 PDT 2012
[   42.370802] cfg80211: Calling CRDA to update world regulatory domain
[   42.380607] IR NEC protocol handler initialized
[   42.396054] IR RC5(x) protocol handler initialized
[   42.405532] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   42.405540] snd_hda_intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   42.405543] hda_intel: Disabling MSI
[   42.405574] snd_hda_intel 0000:00:10.1: setting latency timer to 64
[   42.407588] IR RC6 protocol handler initialized
[   42.417404] IR JVC protocol handler initialized
[   42.420134] Registered IR keymap rc-rc6-mce
[   42.420244] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/rc/rc0/input3
[   42.420311] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/rc/rc0
[   42.428617] IR Sony protocol handler initialized
[   42.437829] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input4
[   42.437950] IR MCE Keyboard/mouse protocol handler initialized
[   42.445102] lirc_dev: IR Remote Control driver registered, major 249
[   42.445451] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   42.445453] IR LIRC bridge handler initialized
[   42.461000] usb 1-5.1: reset high-speed USB device number 4 using ehci_hcd
[   42.509352] cfg80211: World regulatory domain updated:
[   42.509355] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.509358] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.509360] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.509362] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.509364] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.509366] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.648034] mceusb 2-6:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[   42.648039] mceusb 2-6:1.0: 2 tx ports (0x1 cabled) and 2 rx sensors (0x1 active)
[   42.648078] usbcore: registered new interface driver mceusb
[   42.888029] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   42.888034] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888036] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   42.888038] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888040] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   42.888043] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888044] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   42.888047] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888048] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   42.888051] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888053] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   42.888055] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888057] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   42.888059] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888061] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   42.888063] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888065] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   42.888067] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888069] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   42.888071] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888073] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   42.888076] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.888077] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   42.888080] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.888082] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   42.888084] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.888086] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   42.888088] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.891152] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   42.891660] Registered led device: rt73usb-phy0::radio
[   42.891679] Registered led device: rt73usb-phy0::assoc
[   42.891698] Registered led device: rt73usb-phy0::quality
[   42.892364] usbcore: registered new interface driver rt73usb
[   43.016026] hda_codec: ALC883: BIOS auto-probing.
[   43.016031] hda_codec: ALC883: SKU not ready 0x411111f0
[   43.372044] type=1400 audit(1350622196.884:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=677 comm="apparmor_parser"
[   43.372466] type=1400 audit(1350622196.884:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=677 comm="apparmor_parser"
[   43.372707] type=1400 audit(1350622196.884:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=677 comm="apparmor_parser"
[   43.374181] type=1400 audit(1350622196.884:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=730 comm="apparmor_parser"
[   43.374615] type=1400 audit(1350622196.884:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=730 comm="apparmor_parser"
[   43.374861] type=1400 audit(1350622196.884:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=730 comm="apparmor_parser"
[   43.428251] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   43.428254] Bluetooth: BNEP filters: protocol multicast
[   43.433382] Bluetooth: RFCOMM TTY layer initialized
[   43.433390] Bluetooth: RFCOMM socket layer initialized
[   43.433391] Bluetooth: RFCOMM ver 1.11
[   43.520295] init: failsafe main process (919) killed by TERM signal
[   43.770627] type=1400 audit(1350622197.280:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1024 comm="apparmor_parser"
[   43.778095] type=1400 audit(1350622197.288:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1027 comm="apparmor_parser"
[   43.778199] type=1400 audit(1350622197.288:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1025 comm="apparmor_parser"
[   43.785901] type=1400 audit(1350622197.296:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1025 comm="apparmor_parser"
[   43.868181] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:10.1/sound/card0/input5
[   43.873543] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 17
[   43.873565] snd_hda_intel 0000:03:00.1: PCI INT B -> Link[LNEB] -> GSI 17 (level, low) -> IRQ 17
[   43.873567] hda_intel: Disabling MSI
[   43.873621] snd_hda_intel 0000:03:00.1: setting latency timer to 64
[   43.899212] init: alsa-restore main process (1070) terminated with status 19
[   43.904932] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.905262] ADDRCONF(NETDEV_UP): wlan0: link is not ready

and:

difabio@Frontend-2:~$ sudo tail -n /var/log/syslog
[sudo] password for difabio:
tail: /var/log/syslog: invalid number of lines
difabio@Frontend-2:~$ sudo tail -n /var/log/dmesg
tail: /var/log/dmesg: invalid number of lines
difabio@Frontend-2:~$ sudo tail -n 100 /var/log/syslog
Oct 18 21:50:00 Frontend-2 NetworkManager[975]: <info>   hostname 'Frontend-2'
Oct 18 21:50:00 Frontend-2 NetworkManager[975]: <info>   nameserver '192.168.15.1'
Oct 18 21:50:00 Frontend-2 NetworkManager[975]: <info>   domain name 'local.tld'
Oct 18 21:50:00 Frontend-2 NetworkManager[975]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct 18 21:50:00 Frontend-2 NetworkManager[975]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Oct 18 21:50:00 Frontend-2 avahi-daemon[946]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.226.
Oct 18 21:50:00 Frontend-2 avahi-daemon[946]: New relevant interface eth0.IPv4 for mDNS.
Oct 18 21:50:00 Frontend-2 avahi-daemon[946]: Registering new address record for 192.168.15.226 on eth0.IPv4.
Oct 18 21:50:01 Frontend-2 NetworkManager[975]: <info> DNS: starting dnsmasq...
Oct 18 21:50:01 Frontend-2 NetworkManager[975]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Oct 18 21:50:01 Frontend-2 dhclient: bound to 192.168.15.226 -- renewal in 1469 seconds.
Oct 18 21:50:01 Frontend-2 dnsmasq[1338]: started, version 2.59 cache disabled
Oct 18 21:50:01 Frontend-2 dnsmasq[1338]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Oct 18 21:50:01 Frontend-2 dnsmasq[1338]: using nameserver 192.168.15.1#53
Oct 18 21:50:01 Frontend-2 NetworkManager[975]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 18 21:50:03 Frontend-2 NetworkManager[975]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Oct 18 21:50:03 Frontend-2 NetworkManager[975]: <info> Activation (eth0) successful, device activated.
Oct 18 21:50:03 Frontend-2 NetworkManager[975]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Oct 18 21:50:03 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 18 21:50:03 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 18 21:50:03 Frontend-2 acpid: client connected from 1412[0:0]
Oct 18 21:50:03 Frontend-2 acpid: 1 client rule loaded
Oct 18 21:50:05 Frontend-2 kernel: [   51.496620] NVRM: GPU at 0000:03:00: GPU-479c8a84-6c49-0004-a100-6caa5526e0bd
Oct 18 21:50:05 Frontend-2 kernel: [   51.496628] NVRM: Your system is not currently configured to drive a VGA console
Oct 18 21:50:05 Frontend-2 kernel: [   51.496631] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Oct 18 21:50:05 Frontend-2 kernel: [   51.496633] NVRM: requires the use of a text-mode VGA console. Use of other console
Oct 18 21:50:05 Frontend-2 kernel: [   51.496636] NVRM: drivers including, but not limited to, vesafb, may result in
Oct 18 21:50:05 Frontend-2 kernel: [   51.496638] NVRM: corruption and stability problems, and is not supported.
Oct 18 21:50:05 Frontend-2 acpid: client connected from 1412[0:0]
Oct 18 21:50:05 Frontend-2 acpid: 1 client rule loaded
Oct 18 21:50:05 Frontend-2 kernel: [   51.603852] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
Oct 18 21:50:05 Frontend-2 kernel: [   51.608020] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
Oct 18 21:50:05 Frontend-2 kernel: [   51.622922] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
Oct 18 21:50:05 Frontend-2 kernel: [   51.628017] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
Oct 18 21:50:05 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Oct 18 21:50:05 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.Accounts'
Oct 18 21:50:05 Frontend-2 accounts-daemon[1442]: started daemon version 0.6.15
Oct 18 21:50:05 Frontend-2 kernel: [   52.400020] HDMI: detected monitor TX-SR705
Oct 18 21:50:05 Frontend-2 kernel: [   52.400022]      at connection type HDMI
Oct 18 21:50:05 Frontend-2 kernel: [   52.400026] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
Oct 18 21:50:05 Frontend-2 kernel: [   52.400030] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
Oct 18 21:50:05 Frontend-2 kernel: [   52.400034] HDMI: supports coding type LPCM: channels = 8, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
Oct 18 21:50:05 Frontend-2 kernel: [   52.400037] HDMI: supports coding type AC-3: channels = 8, rates = 32000 44100 48000, max bitrate = 640000
Oct 18 21:50:05 Frontend-2 kernel: [   52.400040] HDMI: supports coding type DTS: channels = 8, rates = 44100 48000, max bitrate = 1536000
Oct 18 21:50:05 Frontend-2 kernel: [   52.400043] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 44100 48000
Oct 18 21:50:05 Frontend-2 kernel: [   52.400046] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 96000 176400 192000
Oct 18 21:50:05 Frontend-2 kernel: [   52.400049] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 96000 192000
Oct 18 21:50:05 Frontend-2 kernel: [   52.400051] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 44100
Oct 18 21:50:06 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Oct 18 21:50:06 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Oct 18 21:50:08 Frontend-2 kernel: [   54.672012] eth0: no IPv6 routers present
Oct 18 21:50:12 Frontend-2 ntpdate[1423]: no server suitable for synchronization found
Oct 18 21:50:17 Frontend-2 kernel: [   63.600846] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Oct 18 21:50:17 Frontend-2 kernel: [   63.602655] input: Logitech Cordless MediaBoard Pro(TM) as /devices/pci0000:00/0000:00:0b.1/usb1/1-5/1-5.3/1-5.3:1.0/bluetooth/hci0/hci0:46/input10
Oct 18 21:50:17 Frontend-2 kernel: [   63.603387] generic-bluetooth 0005:046D:B30A.0003: input,hidraw2: BLUETOOTH HID v1.1b Mouse [Logitech Cordless MediaBoard Pro(TM)] on 00:19:DB:03:8E:58
Oct 18 21:50:17 Frontend-2 NetworkManager[975]: <info> (eth0): IP6 addrconf timed out or failed.
Oct 18 21:50:17 Frontend-2 NetworkManager[975]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct 18 21:50:17 Frontend-2 NetworkManager[975]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct 18 21:50:17 Frontend-2 NetworkManager[975]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.UDisks'
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.UPower'
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Successfully called chroot.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Successfully dropped privileges.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Successfully limited resources.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Running.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1771 of process 1771 (n/a) owned by '1000' high priority at nice level -11.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Supervising 1 threads of 1 processes of 1 users.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Watchdog thread running.
Oct 18 21:50:18 Frontend-2 rtkit-daemon[1775]: Canary thread running.
Oct 18 21:50:18 Frontend-2 dbus[865]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Oct 18 21:50:19 Frontend-2 dbus[865]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Oct 18 21:50:20 Frontend-2 dbus[865]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Oct 18 21:50:20 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1893 of process 1771 (n/a) owned by '1000' RT at priority 5.
Oct 18 21:50:20 Frontend-2 rtkit-daemon[1775]: Supervising 2 threads of 1 processes of 1 users.
Oct 18 21:50:20 Frontend-2 blueman-mechanism: Starting blueman-mechanism
Oct 18 21:50:20 Frontend-2 dbus[865]: [system] Successfully activated service 'org.blueman.Mechanism'
Oct 18 21:50:20 Frontend-2 blueman-mechanism: loading Ppp
Oct 18 21:50:20 Frontend-2 blueman-mechanism: loading Config
Oct 18 21:50:20 Frontend-2 blueman-mechanism: loading Network
Oct 18 21:50:20 Frontend-2 blueman-mechanism: loading RfKill
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1896 of process 1771 (n/a) owned by '1000' RT at priority 5.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Supervising 3 threads of 1 processes of 1 users.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1897 of process 1771 (n/a) owned by '1000' RT at priority 5.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Supervising 4 threads of 1 processes of 1 users.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1899 of process 1899 (n/a) owned by '1000' high priority at nice level -11.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Supervising 5 threads of 2 processes of 1 users.
Oct 18 21:50:21 Frontend-2 pulseaudio[1899]: [pulseaudio] pid.c: Daemon already running.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1903 of process 1903 (n/a) owned by '1000' high priority at nice level -11.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Supervising 5 threads of 2 processes of 1 users.
Oct 18 21:50:21 Frontend-2 pulseaudio[1903]: [pulseaudio] pid.c: Daemon already running.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Successfully made thread 1916 of process 1916 (n/a) owned by '1000' high priority at nice level -11.
Oct 18 21:50:21 Frontend-2 rtkit-daemon[1775]: Supervising 5 threads of 2 processes of 1 users.
Oct 18 21:50:21 Frontend-2 pulseaudio[1916]: [pulseaudio] pid.c: Daemon already running.
Oct 18 21:50:50 Frontend-2 blueman-mechanism: Exiting
Oct 18 21:54:57 Frontend-2 anacron[1094]: Job `cron.daily' started
Oct 18 21:54:57 Frontend-2 anacron[2153]: Updated timestamp for job `cron.daily' to 2012-10-18



Please help me figure out how to bring back my working backend.

Thanks in advance!
Mike D

---

### Post by mdifabio on 2012-10-20
Still working on it.  I am stumped and pretty sure it is not a hardware problem.  Replaced mobo, cpu, memory, hdd, gpu, network card...

Tried upgrading Linux kernel 3.4.  Didn't help.

Since this backend is freezing up bad, I don't know which/when are the best logs to check/report?

Help

---

### Post by mdifabio on 2012-10-20
New info:  In the many re-installs of Mythbuntu I have tried on this backend, most seem to have initially frozen when running mythfilldatabase.  This requires a hard reset (reset button on case) and thereafter the freeze ups are frequent at random moments.

What logs and from what time are best to show you to help me?

Thanks in advance.

Mike

---

