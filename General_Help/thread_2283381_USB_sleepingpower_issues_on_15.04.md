---
title: "USB sleeping/power issues on 15.04"
date: 2015-06-21
forum: General Help
---

### Post by thomas-morehead131 on 2015-06-21
[COLOR=#111111][FONT=Ubuntu]After my upgrade to 15.04, my USB ports have been acting weird, before i can charge my phone and use a USB mouse without issues but now it acts like Ubuntu will disconnect my USB devices on its own if it feels like it, my USB ports are fine, it's just Ubuntu. I never broke a USB port or worn out the ports at all.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Oddly, it starts if I go to a Youtube video and play one, then all USB devices stop.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Log from /var/log/syslog[/FONT][/COLOR]

```
Jun 21 10:21:18 kyle-HP-Envy-dv6-Notebook-PC rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="352" x-info="http://www.rsyslog.com"] rsyslogd was HUPedJun 21 10:21:22 kyle-HP-Envy-dv6-Notebook-PC anacron[1508]: Job `cron.daily' terminated
Jun 21 10:21:22 kyle-HP-Envy-dv6-Notebook-PC anacron[1508]: Normal exit (1 job run)
Jun 21 10:35:18 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jun 21 10:35:18 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 21 10:39:22 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1408.051492] usb 3-1: USB disconnect, device number 2
Jun 21 10:39:22 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 17
Jun 21 10:39:22 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 18
Jun 21 10:39:22 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:22 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:23 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:23 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:23 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:23 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1410.894576] usb 3-1: new full-speed USB device number 3 using xhci_hcd
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.058762] usb 3-1: New USB device found, idVendor=3938, idProduct=1032
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.058770] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.058774] usb 3-1: Product: 2.4G RF Keyboard & Mouse
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.058777] usb 3-1: Manufacturer: MOSART Semi.
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.059048] usb 3-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.074546] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/0003:3938:1032.0003/input/input20
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.130896] hid-generic 0003:3938:1032.0003: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:10.1-1/input0
Jun 21 10:39:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.161352] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/0003:3938:1032.0004/input/input21
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1411.215888] hid-generic 0003:3938:1032.0004: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:10.1-1/input1
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:10.1/usb3/3-1"
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: bus: 3, device: 3 was not an MTP device
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:26 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1422.224841] usb 3-1: USB disconnect, device number 3
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 17
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 18
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:37 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:38 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.117950] usb 3-1: new full-speed USB device number 4 using xhci_hcd
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.281932] usb 3-1: New USB device found, idVendor=3938, idProduct=1032
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.281938] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.281941] usb 3-1: Product: 2.4G RF Keyboard & Mouse
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.281943] usb 3-1: Manufacturer: MOSART Semi.
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.282158] usb 3-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.297410] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/0003:3938:1032.0005/input/input22
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.350219] hid-generic 0003:3938:1032.0005: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:10.1-1/input0
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.380160] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/0003:3938:1032.0006/input/input23
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 1424.434276] hid-generic 0003:3938:1032.0006: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:10.1-1/input1
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:10.1/usb3/3-1"
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: bus: 3, device: 4 was not an MTP device
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:39:39 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed bound -> renew
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 10:45:07 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1502 seconds.
Jun 21 10:45:59 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:45:59 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active [unchanged]
Jun 21 10:47:43 kyle-HP-Envy-dv6-Notebook-PC signond[17333]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 10:47:43 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jun 21 10:47:43 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 21 10:53:08 kyle-HP-Envy-dv6-Notebook-PC signond[26221]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 10:57:38 kyle-HP-Envy-dv6-Notebook-PC signond[32543]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 10:59:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:59:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active
Jun 21 10:59:07 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jun 21 10:59:07 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jun 21 10:59:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Failed.
Jun 21 10:59:08 kyle-HP-Envy-dv6-Notebook-PC console-kit-daemon[2380]: GLib-CRITICAL: Source ID 14 was not found when attempting to remove it
Jun 21 10:59:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2592.337211] hp_wmi: Unknown event_id - 0 - 0x0
Jun 21 10:59:08 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:59:08 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 10:59:08 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 10:59:08 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 10:59:35 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2619.683853] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 10:59:46 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2630.673860] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:00:26 kyle-HP-Envy-dv6-Notebook-PC signond[5166]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 11:00:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2675.628316] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:01:20 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2724.672307] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:02:13 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2777.050234] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:02:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2795.635952] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:03:00 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2824.446367] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:03:09 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2833.493437] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x60 returns -16
Jun 21 11:03:28 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2852.741795] usb 3-1: USB disconnect, device number 4
Jun 21 11:03:28 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 17
Jun 21 11:03:28 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 18
Jun 21 11:03:29 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 11:03:29 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active
Jun 21 11:03:29 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 11:03:29 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active
Jun 21 11:03:30 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2854.830623] usb 6-1: new full-speed USB device number 3 using ohci-pci
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2854.997514] usb 6-1: New USB device found, idVendor=3938, idProduct=1032
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2854.997520] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2854.997523] usb 6-1: Product: 2.4G RF Keyboard & Mouse
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2854.997525] usb 6-1: Manufacturer: MOSART Semi.
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2855.004038] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.0/0003:3938:1032.0007/input/input24
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2855.058698] hid-generic 0003:3938:1032.0007: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:12.0-1/input0
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2855.063670] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.1/0003:3938:1032.0008/input/input25
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 2855.120266] hid-generic 0003:3938:1032.0008: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:12.0-1/input1
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: checking bus 6, device 3: "/sys/devices/pci0000:00/0000:00:12.0/usb6/6-1"
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: bus: 6, device: 3 was not an MTP device
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 11:03:31 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active
Jun 21 11:04:32 kyle-HP-Envy-dv6-Notebook-PC signond[11132]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 11:04:42 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 11:04:42 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1578 seconds.
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 11:10:09 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 11:17:01 kyle-HP-Envy-dv6-Notebook-PC CRON[29530]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 11:29:55 kyle-HP-Envy-dv6-Notebook-PC signond[14450]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 11:36:27 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 11:36:28 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1381 seconds.
Jun 21 11:43:07 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jun 21 11:43:07 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1409 seconds.
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 11:59:29 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 12:17:01 kyle-HP-Envy-dv6-Notebook-PC CRON[12262]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 12:18:32 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 7352.251200] perf interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 12:22:58 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1762 seconds.
Jun 21 12:22:59 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 12:22:59 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 12:24:44 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 12:24:44 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 12:25:38 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 12:25:38 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 12:25:41 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 12:25:41 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 12:27:45 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jun 21 12:27:45 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 21 12:27:53 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 12:27:53 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 12:27:56 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 12:27:56 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, not active [unchanged]
Jun 21 12:43:02 kyle-HP-Envy-dv6-Notebook-PC signond[15045]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 12:52:21 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1780 seconds.
Jun 21 13:01:16 kyle-HP-Envy-dv6-Notebook-PC signond[6906]: ../../../../src/signond/signondaemon.cpp 390 init Failed to SUID root. Secure storage will not be available.
Jun 21 13:01:23 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:01:23 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 13:01:24 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jun 21 13:01:24 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jun 21 13:01:24 kyle-HP-Envy-dv6-Notebook-PC console-kit-daemon[2380]: GLib-CRITICAL: Source ID 23 was not found when attempting to remove it
Jun 21 13:01:24 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 9922.527137] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,data=ordered,commit=600
Jun 21 13:01:25 kyle-HP-Envy-dv6-Notebook-PC kernel: [ 9922.828978] EXT4-fs (sda8): re-mounted. Opts: data=ordered,commit=600
Jun 21 13:01:25 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Failed.
Jun 21 13:01:26 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:01:26 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active [unchanged]
Jun 21 13:01:27 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:01:27 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active [unchanged]
Jun 21 13:17:01 kyle-HP-Envy-dv6-Notebook-PC CRON[28422]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 13:21:21 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jun 21 13:21:21 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPREQUEST of 192.168.6.224 on wlan0 to 192.168.6.1 port 67 (xid=0x28090f43)
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC dhclient: DHCPACK of 192.168.6.224 from 192.168.6.1
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info> (wlan0): DHCPv4 state changed renew -> renew
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   address 192.168.6.224
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   plen 24 (255.255.255.0)
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   gateway 192.168.6.1
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   server identifier 192.168.6.1
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   lease time 3600
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '192.168.6.1'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.2'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   nameserver '64.134.255.10'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   domain name 'mcd03615.pit.wayport.net'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC NetworkManager[1313]: <info>   wins '192.168.6.1'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC dbus[470]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0
Jun 21 13:22:01 kyle-HP-Envy-dv6-Notebook-PC dhclient: bound to 192.168.6.224 -- renewal in 1635 seconds.
Jun 21 13:25:06 kyle-HP-Envy-dv6-Notebook-PC kernel: [11343.125728] usb 6-1: USB disconnect, device number 3
Jun 21 13:25:06 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 17
Jun 21 13:25:06 kyle-HP-Envy-dv6-Notebook-PC acpid: input device has been disconnected, fd 18
Jun 21 13:25:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:25:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 13:25:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:25:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 13:25:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:25:07 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11344.920131] usb 6-1: new full-speed USB device number 4 using ohci-pci
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.086964] usb 6-1: New USB device found, idVendor=3938, idProduct=1032
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.086973] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.086978] usb 6-1: Product: 2.4G RF Keyboard & Mouse
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.086982] usb 6-1: Manufacturer: MOSART Semi.
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.093890] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.0/0003:3938:1032.0009/input/input26
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.148317] hid-generic 0003:3938:1032.0009: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:12.0-1/input0
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.153617] input: MOSART Semi. 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.1/0003:3938:1032.000A/input/input27
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC kernel: [11345.209366] hid-generic 0003:3938:1032.000A: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G RF Keyboard & Mouse] on usb-0000:00:12.0-1/input1
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: checking bus 6, device 4: "/sys/devices/pci0000:00/0000:00:12.0/usb6/6-1"
Jun 21 13:25:08 kyle-HP-Envy-dv6-Notebook-PC mtp-probe: bus: 6, device: 4 was not an MTP device
Jun 21 13:25:09 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:25:09 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
Jun 21 13:25:09 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: Laptop mode 
Jun 21 13:25:09 kyle-HP-Envy-dv6-Notebook-PC laptop-mode: enabled, active
```

---

### Post by oscar-tiderman on 2015-06-23
Seems to me like your power saving script is putting your USB ports in power saving mode, that would cause it to stop charging, would also cause some trouble with e.g. a wireless mouse receiver via USB. You have any custom scripts for power saving? Try running powertop and check if your USB ports are in "Good" or "Bad" state, you probably want to put the one you connect your phone to in "Bad" state. It seems strange though that your laptop goes in and out of power saving mode that often, but yes something has definitely changed in power handling with 15.04, mine is not triggered at all any more, still searching for some answers. Hope it helps.

---

### Post by thomas-morehead131 on 2015-06-24
Well, I did have the package "laptop-mode-tools" installed and active, but I removed it thinking it would help my issue, and since my USB devices are fine. I thought that package was a good thing to have running :/

---

