---
title: "Random freezes"
date: 2016-07-29
forum: General Help
---

### Post by igb887 on 2016-07-29
I am running my machine with ubuntu 16.04 24/7 amd recently I have been getting freezes every 3-5 days. I just come to a frozen screen and only hard restart works (raising elephants doesnt work). Below you can see a part from my /var/log/syslog, the freeze occured at 22:26:06 when there is a long line of "[COLOR=#000000][FONT=&quot]\00\00\00\00\00\00\" characters. [/FONT][/COLOR]I have no idea what could be causing this, any suggestions?



```


Jul 28 22:22:22 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.22 52:54:00:3a:16:f3
Jul 28 22:22:22 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.22 52:54:00:3a:16:f3 sample-0111
Jul 28 22:22:33 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.87 52:54:00:91:e7:92
Jul 28 22:22:33 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.87 52:54:00:91:e7:92 sample-0111
Jul 28 22:22:37 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.235 52:54:00:c7:d8:5c
Jul 28 22:22:37 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.235 52:54:00:c7:d8:5c sample-0111
Jul 28 22:22:43 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.65 52:54:00:b2:15:9c
Jul 28 22:22:43 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.65 52:54:00:b2:15:9c admin-PC
Jul 28 22:23:09 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.67 52:54:00:66:68:26
Jul 28 22:23:09 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.67 52:54:00:66:68:26 admin-PC
Jul 28 22:23:32 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.245 52:54:00:e1:2c:b4
Jul 28 22:23:32 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.245 52:54:00:e1:2c:b4 sample-0111
Jul 28 22:23:34 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.72 52:54:00:70:1d:51
Jul 28 22:23:34 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.72 52:54:00:70:1d:51 sample-0111
Jul 28 22:24:02 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.199 52:54:00:c5:2a:e7
Jul 28 22:24:02 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.199 52:54:00:c5:2a:e7 sample-0111
Jul 28 22:24:09 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.59 52:54:00:34:92:c5
Jul 28 22:24:09 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.59 52:54:00:34:92:c5 sample-0111
Jul 28 22:24:56 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.233 52:54:00:d7:65:a4
Jul 28 22:24:56 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.233 52:54:00:d7:65:a4 sample-0111
Jul 28 22:25:43 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.2 52:54:00:d7:df:87
Jul 28 22:25:43 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.2 52:54:00:d7:df:87 sample-0111
Jul 28 22:25:48 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.14 52:54:00:ff:94:7e
Jul 28 22:25:48 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.14 52:54:00:ff:94:7e sample-0111
Jul 28 22:25:57 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.135 52:54:00:06:41:ae
Jul 28 22:25:57 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.135 52:54:00:06:41:ae admin-PC
Jul 28 22:26:06 tomas-vie dnsmasq-dhcp[1783]: DHCPREQUEST(virbr0) 192.168.122.71 52:54:00:e5:e7:18
Jul 28 22:26:06 tomas-vie dnsmasq-dhcp[1783]: DHCPACK(virbr0) 192.168.122.71 52:54:00:e5:e7:18 sample-0111
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Jul 29 03:05:03 tomas-vie rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1074" x-info="http://www.rsyslog.com"] start
Jul 29 03:05:03 tomas-vie rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Jul 29 03:05:03 tomas-vie rsyslogd: rsyslogd's groupid changed to 108
Jul 29 03:05:03 tomas-vie rsyslogd: rsyslogd's userid changed to 104
Jul 29 03:05:03 tomas-vie systemd-modules-load[452]: Inserted module 'lp'
Jul 29 03:05:03 tomas-vie systemd-modules-load[452]: Inserted module 'ppdev'
Jul 29 03:05:03 tomas-vie systemd-modules-load[452]: Inserted module 'parport_pc'
Jul 29 03:05:03 tomas-vie systemd[1]: Started udev Kernel Device Manager.
Jul 29 03:05:03 tomas-vie systemd[1]: Starting Remount Root and Kernel File Systems...
Jul 29 03:05:03 tomas-vie systemd[1]: Starting LSB: QEMU KVM module loading script...
Jul 29 03:05:03 tomas-vie systemd[1]: Started Remount Root and Kernel File Systems.
Jul 29 03:05:03 tomas-vie systemd[1]: Starting udev Coldplug all Devices...
Jul 29 03:05:03 tomas-vie systemd[1]: Starting Flush Journal to Persistent Storage...
Jul 29 03:05:03 tomas-vie systemd[1]: Starting Load/Save Random Seed...
Jul 29 03:05:03 tomas-vie systemd[1]: Reached target Local File Systems (Pre).
Jul 29 03:05:03 tomas-vie systemd[1]: Started Load/Save Random Seed.
Jul 29 03:05:03 tomas-vie systemd[1]: Started Flush Journal to Persistent Storage.
Jul 29 03:05:03 tomas-vie qemu-kvm[495]:  * Configuring kvm qemu-kvm
Jul 29 03:05:03 tomas-vie qemu-kvm[495]:    ...done.
Jul 29 03:05:03 tomas-vie systemd[1]: Started LSB: QEMU KVM module loading script.
Jul 29 03:05:03 tomas-vie systemd[1]: Started udev Coldplug all Devices.
Jul 29 03:05:03 tomas-vie systemd[1]: Starting Show Plymouth Boot Screen...
Jul 29 03:05:03 tomas-vie rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 29 03:05:03 tomas-vie mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-13"
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] Linux version 4.4.0-31-generic (buildd@lgw01-16) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2.1) ) #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 (Ubuntu 4.4.0-31.50-generic 4.4.13)
Jul 29 03:05:03 tomas-vie mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14"
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=b132cd08-bfef-4d60-81a0-53774be25bc3 ro quiet splash
Jul 29 03:05:03 tomas-vie mtp-probe: bus: 3, device: 2 was not an MTP device
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] KERNEL supported cpus:
Jul 29 03:05:03 tomas-vie mtp-probe: bus: 3, device: 3 was not an MTP device
Jul 29 03:05:03 tomas-vie kernel: [    0.000000]   Intel GenuineIntel
Jul 29 03:05:03 tomas-vie kernel: [    0.000000]   AMD AuthenticAMD
Jul 29 03:05:03 tomas-vie kernel: [    0.000000]   Centaur CentaurHauls
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Jul 29 03:05:03 tomas-vie rsyslogd-2007: action 'action 10' suspended, next retry is Fri Jul 29 03:05:33 2016 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
Jul 29 03:05:03 tomas-vie ureadahead[438]: ureadahead:/home/tomas/.cache/upstart/dbus.log: No such file or directory
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Jul 29 03:05:03 tomas-vie systemd-udevd[632]: Process '/lib/udev/hdparm' failed with exit code 5.
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] x86/fpu: Using 'eager' FPU context switches.
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 29 03:05:03 tomas-vie systemd-udevd[669]: Process '/lib/udev/hdparm' failed with exit code 5.
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000078ea9fff] usable
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x0000000078eaa000-0x000000007b01afff] reserved
Jul 29 03:05:03 tomas-vie ureadahead[438]: ureadahead:/home/tomas/.cache/upstart/window-stack-bridge.log: No such file or directory
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x000000007b01b000-0x000000007b076fff] ACPI data
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x000000007b077000-0x000000007bed9fff] ACPI NVS
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x000000007beda000-0x000000008fffffff] reserved
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed44fff] reserved
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000207fffffff] usable
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 29 03:05:03 tomas-vie systemd-udevd[616]: Process '/lib/udev/hdparm' failed with exit code 5.
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] SMBIOS 2.8 present.
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. Z10PE-D16 WS/Z10PE-D16 WS, BIOS 3204 12/18/2015
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 29 03:05:03 tomas-vie kernel: [    0.000000] e820: last_pfn = 0x2080000 max_arch_pfn = 0x400000000



```

---

