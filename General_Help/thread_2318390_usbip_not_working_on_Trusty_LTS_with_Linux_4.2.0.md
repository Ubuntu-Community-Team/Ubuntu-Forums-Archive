---
title: "usbip not working on Trusty LTS with Linux 4.2.0"
date: 2016-03-25
forum: General Help
---

### Post by matthew02 on 2016-03-25
I recently upgraded the kernel on my headless server and now I cannot get usbip to work. I upgraded the kernel to get more robust btrfs support and do not intend to revert this change. I am on **14.04.4 LTS** and have had this server running for several years with no issues using usbip. My kernel version is **4.2.0-34-generic**. I have loaded the kernel modules **usbip_host** and **usbip_core**. I have installed **linux-tools-generic-lts-wily** and tried the usbip binaries from that. I have downloaded the Trusty source and compiled the userspace tools directly. Nothing makes any difference. I am in the process of downloading the Wily source to try and compile from that. In the meantime, if anyone has any suggestions, I would be very grateful. Thanks!

Following is the output of ***usbipd -d*** (which appears to be running fine)
```

libusbip: debug: usbip_host_driver.c:189:[refresh_exported_devices] bind usbip-host.ko to a usb device to be exportable!
usbipd: info: starting usbipd (usbip-utils 1.1.1)
usbipd: debug: usbipd.c:375:[listen_all_addrinfo] opening 0.0.0.0:3240
usbip: debug: usbip_network.c:253:[usbip_net_set_v6only] setsockopt: IPV6_V6ONLY
usbipd: info: listening on 0.0.0.0:3240
usbipd: debug: usbipd.c:375:[listen_all_addrinfo] opening :::3240
usbipd: info: listening on :::3240
usbipd: debug: usbipd.c:538:[do_standalone_mode] listening on 2 addresses
usbipd: debug: usbipd.c:569:[do_standalone_mode] heartbeat timeout on ppoll()
usbipd: debug: usbipd.c:569:[do_standalone_mode] heartbeat timeout on ppoll()
usbipd: debug: usbipd.c:569:[do_standalone_mode] heartbeat timeout on ppoll()
...

```

Then the output of ***usbip list -l***
```

Local USB devices
=================
 - busid 1-5 (04f9:0040)
   Brother Industries, Ltd : unknown product (04f9:0040)
         1-5:1.0 -> usblp

 - busid 2-1 (04c5:11a2)
   Fujitsu, Ltd : unknown product (04c5:11a2)
         2-1:1.0 -> unknown

 - busid 4-3 (045e:009d)
   Microsoft Corp. : Wireless Optical Desktop 3.0 (045e:009d)
         4-3:1.0 -> usbhid
         4-3:1.1 -> usbhid

```

And then ***usbip --debug bind -b 2-1***
```

usbip: debug: usbip.c:135:[run_command] running command: `bind'
usbip: debug: usbip_bind.c:162:[unbind_other] 2-1:1.0 -> unknown
usbip: debug: utils.c:65:[modify_match_busid] write "add 2-1" to /sys/bus/usb/drivers/usbip-host/match_busid
usbip: debug: usbip_bind.c:101:[bind_usbip] bind driver at 2-1:1.0 failed
usbip: error: could not bind device to usbip-host
usbip: debug: utils.c:65:[modify_match_busid] write "del 2-1" to /sys/bus/usb/drivers/usbip-host/match_busid

```

---

### Post by matthew02 on 2016-03-26
Compiling the usbip userspace tools from the Wily source did actually work, but I did a little more research and found out that usbip is now in the linux-tools package (no need to compile anything).
```
$ sudo apt-get install linux-tools-generic-lts-wily
```
The binaries for usbip and usbipd can be found under ***/usr/lib/linux-lts-wily-tools-4.2.0-34/***. Those are both version 2.0 and seem to be working fine.

---

