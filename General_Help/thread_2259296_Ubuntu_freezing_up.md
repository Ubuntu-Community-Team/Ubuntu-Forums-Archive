---
title: "Ubuntu freezing up"
date: 2015-01-03
forum: General Help
---

### Post by dorlow on 2015-01-03
Hi,

I'm having trouble with my Ubuntu installation freezing up frequently.  I'm running it on a laptop.  I run a virtualbox install of Windows 7 constantly when Ubuntu is running.  (I have some apps and services that run significantly better on Ubuntu, but a few things that I need Windows to service them.)  I have an Intel i7 processor and I already ran the fix to allow my processor to use pstate to keep the processor cooler.  But I still think my laptop is significantly hotter than running Windows.

But I know the proper way to fix a PC is not to ask what's wrong, but to ask what is the correct way to diagnose the reason why it's freezing up.  Does anyone have any good logs to look for what the last thing the PC was thinking before it froze up?  

Sometimes after it freezes up, I can do a Ctrl + Alt + an F key to get to a terminal and attempt to kill my x-windows session.  But most of the time, it's so frozen up, it won't respond to that and I have to hard reset my laptop.

---

### Post by Bucky Ball on 2015-01-03
If you can get to the cli with ctl+alt+f1, then login and type in 'dmesg'. See what it says at the bottom of that output. Might give some clues. :-k

Also,

```
sudo reboot -h now
```

... will reboot your machine from the CLI, avoiding the need to hard shutdown, if it will respond to anything, that is. :)

---

### Post by Mohammad_Eid on 2015-01-09
I face the same issue, I tried the command "dmesg" and get the following :


[   11.940377] [drm] Initialized nouveau 1.1.2 20120801 for 0000:01:00.0 on minor 0
[   12.380244] audit: type=1400 audit(1420787855.932:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=460 comm="apparmor_parser"
[   12.380250] audit: type=1400 audit(1420787855.932:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   12.380254] audit: type=1400 audit(1420787855.932:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   12.380262] audit: type=1400 audit(1420787855.932:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=416 comm="apparmor_parser"
[   12.380268] audit: type=1400 audit(1420787855.932:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=416 comm="apparmor_parser"
[   12.380272] audit: type=1400 audit(1420787855.932:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=416 comm="apparmor_parser"
[   12.380280] audit: type=1400 audit(1420787855.932:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
[   12.380286] audit: type=1400 audit(1420787855.932:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=415 comm="apparmor_parser"
[   12.380290] audit: type=1400 audit(1420787855.932:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=415 comm="apparmor_parser"
[   12.579978] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.318855] init: Error while reading from descriptor: Broken pipe
[   13.319941] init: failsafe main process (620) killed by TERM signal
[   13.846496] audit: type=1400 audit(1420787857.400:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=725 comm="apparmor_parser"
[   14.382323] floppy0: no floppy controllers found
[   14.523656] init: cups main process (774) killed by HUP signal
[   14.523665] init: cups main process ended, respawning
[   14.635364] Bluetooth: Core ver 2.19
[   14.635376] NET: Registered protocol family 31
[   14.635377] Bluetooth: HCI device and connection manager initialized
[   14.635383] Bluetooth: HCI socket layer initialized
[   14.635385] Bluetooth: L2CAP socket layer initialized
[   14.635391] Bluetooth: SCO socket layer initialized
[   14.638218] Bluetooth: RFCOMM TTY layer initialized
[   14.638223] Bluetooth: RFCOMM socket layer initialized
[   14.638227] Bluetooth: RFCOMM ver 1.11
[   14.671542] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.671545] Bluetooth: BNEP filters: protocol multicast
[   14.671549] Bluetooth: BNEP socket layer initialized
[   15.654555] systemd-logind[1077]: New seat seat0.
[   15.724124] systemd-logind[1077]: Watching system buttons on /dev/input/event1 (Power Button)
[   15.724171] systemd-logind[1077]: Watching system buttons on /dev/input/event0 (Power Button)
[   16.231288] r8169 0000:04:00.0 eth0: link down
[   16.231314] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.237540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.489119] wlan0: authenticate with dc:02:8e:62:4d:80
[   17.491060] wlan0: send auth to dc:02:8e:62:4d:80 (try 1/3)
[   17.513736] wlan0: authenticated
[   17.516762] wlan0: associate with dc:02:8e:62:4d:80 (try 1/3)
[   17.520009] wlan0: RX AssocResp from dc:02:8e:62:4d:80 (capab=0x411 status=0 aid=1)
[   17.520074] wlan0: associated
[   17.520104] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   17.520165] cfg80211: Calling CRDA for country: JO
[   17.530922] cfg80211: Regulatory domain changed to country: JO
[   17.530924] cfg80211:  DFS Master region: unset
[   17.530925] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   17.530927] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   17.530928] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 1800 mBm), (N/A)
[   18.674815] systemd-logind[1077]: Failed to start unit [EMAIL="user@112.servic"]user@112.servic[/EMAIL]e: Unknown unit: [EMAIL="user@112.servic"]user@112.servic[/EMAIL]e
[   18.674827] systemd-logind[1077]: Failed to start user service: Unknown unit: [EMAIL="user@112.servic"]user@112.servic[/EMAIL]e
[   18.679379] systemd-logind[1077]: New session c1 of user lightdm.
[   18.679409] systemd-logind[1077]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
[   35.483790] systemd-logind[1077]: Failed to start unit [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Unknown unit: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
[   35.483797] systemd-logind[1077]: Failed to start user service: Unknown unit: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
[   35.487651] systemd-logind[1077]: New session c2 of user mohammad.
[   35.487667] systemd-logind[1077]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   44.462216] audit_printk_skb: 72 callbacks suppressed
[   44.462219] audit: type=1400 audit(1420787888.000:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2503 comm="apparmor_parser"
[   44.462225] audit: type=1400 audit(1420787888.000:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2503 comm="apparmor_parser"
[   44.473656] audit: type=1400 audit(1420787888.012:38): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=2503 comm="apparmor_parser"
[  233.599287] udevadm: The scan_unevictable_pages sysctl/node-interface has been disabled for lack of a legitimate use case.  If you have one, please send an email to [EMAIL="linux-mm@kvack.org"]linux-mm@kvack.org[/EMAIL].
[  388.070075] Broke affinity for irq 18
[  388.070093] Broke affinity for irq 41
[  388.071144] kvm: disabling virtualization on CPU1
[  388.173547] smpboot: CPU 1 is now offline
[  388.210019] Broke affinity for irq 19
[  388.210037] Broke affinity for irq 42
[  388.211090] kvm: disabling virtualization on CPU2
[  388.211118] smpboot: CPU 2 is now offline
[  388.237754] Broke affinity for irq 43
[  388.238801] kvm: disabling virtualization on CPU3
[  388.341558] smpboot: CPU 3 is now offline
[  388.356989] x86: Booting SMP configuration:
[  388.356992] smpboot: Booting Node 0 Processor 1 APIC 0x2
[  388.368768] kvm: enabling virtualization on CPU1
[  388.376352] hpet: hpet3 irq 41 for MSI
[  388.378380] smpboot: Booting Node 0 Processor 2 APIC 0x4
[  388.390177] kvm: enabling virtualization on CPU2
[  388.394919] hpet: hpet4 irq 42 for MSI
[  388.397767] smpboot: Booting Node 0 Processor 3 APIC 0x6
[  388.409571] kvm: enabling virtualization on CPU3
[  388.412994] hpet: hpet5 irq 43 for MSI
[  490.216625] usb 5-2: USB disconnect, device number 3
[  500.276003] usb 7-2: new low-speed USB device number 2 using uhci_hcd
[  500.459156] usb 7-2: New USB device found, idVendor=045e, idProduct=0040
[  500.459163] usb 7-2: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[  500.459168] usb 7-2: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[  500.459171] usb 7-2: Manufacturer: Microsoft
[  500.477343] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/0003:045E:0040.0003/input/input12
[  500.477703] hid-generic 0003:045E:0040.0003: input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2/input0
[  788.529659] systemd-hostnamed[5300]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1236.718491] perf interrupt took too long (2507 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

---

### Post by Bucky Ball on 2015-01-09
@Mohammad_Eid: Best to post a new thread, also, please use [code] tags. See the last link in my signature for how. Thanks. ;)

---

