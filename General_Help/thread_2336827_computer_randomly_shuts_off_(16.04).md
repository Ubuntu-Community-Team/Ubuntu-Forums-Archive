---
title: "computer randomly shuts off (16.04)"
date: 2016-09-11
forum: General Help
---

### Post by mickyscandal on 2016-09-11
my computer is a Toshiba satellite click 2 (l35w-b3204). I've been  dealing with this for a while now (since i installed Linux). my computer  will just power off out of nowhere like someone just held the power  button down. I've read several posts that all agree that it's probably  an overheating issue but at least for me, that is not the case. after  setting up and running lm-sensors everything seems in order. my cores  are 37-41 degress C and soc-dts0-virtual is 40 degrees. I found one  other possible fix online which was changing a line in /etc/default/grub  (cant remember which one the post said) but that just ended up breaking  more than it fixed.      does anyone have any ideas of what could be the problem, or at least  just a starting point to start looking into? thanks in advance for any  help.

---

### Post by ian-weisser on 2016-09-11
Here's your starting point: /var/log/syslog. Look there for clues around the time of a poweroff.

It's important to understand that Ubuntu has several ways to poweroff the system, but ALL of them leave log entries.
There is NOT a poweroff-without-leaving-any-log-entry function. Never has been. Never will be. If there is no log entry, then you have some kind of hardware failure.

---

### Post by mickyscandal on 2016-09-12
ok so I just spent a bunch of time getting to know the syslog file and trying to find a point where it had crashed. i pinted the last 50 lines before the restart and this is what i get..

> Sep 11 12:58:33 Mickys-scandal-laptop kernel: [ 1139.501211] usb 1-3: device descriptor read/64, error -71
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Sep 11 12:58:34 Mickys-scandal-laptop 05efi: debug: /dev/sda7 is ext2 partition: exiting
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Sep 11 12:58:34 Mickys-scandal-laptop 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Sep 11 12:58:34 Mickys-scandal-laptop 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Sep 11 12:58:34 Mickys-scandal-laptop macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Sep 11 12:58:34 Mickys-scandal-laptop 20microsoft: debug: Skipping legacy bootloaders on UEFI system
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Sep 11 12:58:34 Mickys-scandal-laptop 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Sep 11 12:58:34 Mickys-scandal-laptop 83haiku: debug: /dev/sda7 is not a BeFS partition: exiting
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Sep 11 12:58:34 Mickys-scandal-laptop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Sep 11 12:58:34 Mickys-scandal-laptop 50mounted-tests: debug: /dev/sda8 type not recognised; skipping
Sep 11 12:58:34 Mickys-scandal-laptop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1139.717162] usb 1-3: device descriptor read/64, error -71
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1139.932858] usb 1-3: new full-speed USB device number 79 using xhci_hcd
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1139.932966] usb 1-3: Device not responding to setup address.
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1140.136797] usb 1-3: Device not responding to setup address.
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1140.340576] usb 1-3: device not accepting address 79, error -71
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1140.452482] usb 1-3: new full-speed USB device number 80 using xhci_hcd
Sep 11 12:58:34 Mickys-scandal-laptop kernel: [ 1140.452605] usb 1-3: Device not responding to setup address.
Sep 11 12:58:35 Mickys-scandal-laptop kernel: [ 1140.656391] usb 1-3: Device not responding to setup address.
Sep 11 12:58:35 Mickys-scandal-laptop kernel: [ 1140.860150] usb 1-3: device not accepting address 80, error -71
Sep 11 12:58:35 Mickys-scandal-laptop kernel: [ 1140.860239] usb usb1-port3: unable to enumerate USB device
Sep 11 12:58:48 Mickys-scandal-laptop kernel: [ 1153.586245] usb 1-3: new full-speed USB device number 81 using xhci_hcd
Sep 11 12:58:48 Mickys-scandal-laptop kernel: [ 1153.698148] usb 1-3: device descriptor read/64, error -71
Sep 11 12:58:48 Mickys-scandal-laptop kernel: [ 1153.913978] usb 1-3: device descriptor read/64, error -71
Sep 11 12:58:48 Mickys-scandal-laptop kernel: [ 1154.129830] usb 1-3: new full-speed USB device number 82 using xhci_hcd
Sep 11 12:58:48 Mickys-scandal-laptop kernel: [ 1154.241806] usb 1-3: device descriptor read/64, error -71
Sep 11 12:58:48 Mickys-scandal-laptop kernel: [ 1154.457562] usb 1-3: device descriptor read/64, error -71
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1154.673376] usb 1-3: new full-speed USB device number 83 using xhci_hcd
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1154.673605] usb 1-3: Device not responding to setup address.
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1154.877361] usb 1-3: Device not responding to setup address.
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1155.081061] usb 1-3: device not accepting address 83, error -71
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1155.192977] usb 1-3: new full-speed USB device number 84 using xhci_hcd
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1155.193181] usb 1-3: Device not responding to setup address.
Sep 11 12:58:49 Mickys-scandal-laptop kernel: [ 1155.397030] usb 1-3: Device not responding to setup address.
Sep 11 12:58:50 Mickys-scandal-laptop kernel: [ 1155.600659] usb 1-3: device not accepting address 84, error -71
Sep 11 12:58:50 Mickys-scandal-laptop kernel: [ 1155.600716] usb usb1-port3: unable to enumerate USB device
Sep 11 12:48:40 Mickys-scandal-laptop rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="816" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Sep 11 12:58:53 Mickys-scandal-laptop rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="816" x-info="http://www.rsyslog.com"] exiting on signal 15.
Sep 11 12:59:42 Mickys-scandal-laptop rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="935" x-info="http://www.rsyslog.com"] start

I really don't see anything there that would cause a crash. i don't even see anything about a crash. now granted, I don't really understand most of what I see there. maybe someone here can find an entry in here to point me in the right direction? I know the last post pretty much said if i can't find it in the log that it has to be a hardware issue but when I'm booted into windows I've never had anything like that happened since I've owned the computer, so that leads me to believe that it couldn't be hardware.
    Also, one more thing I noticed when going through the syslog files is that the most recent entries are from yesterday (09/11). I've definitely used the computer a fair amount today and even booted/restarted a couple times, so there should be entries from today, correct?

---

