---
title: "VMWare Workstation 5.0 and DC++"
date: 2005-11-02
forum: General Help
---

### Post by jnk on 2005-11-02
Hi.

I've installed VMWare Workstation 5.0 in Ubuntu 5.10.
I've got the network to work thanks to this forum.
Installed WinXP on my virtual machine so that I can use DC++,
the only windows application that I realy miss...

Anyway, when I start DC++ I get this error msg:
"Failed to create port mappings. Please setup your NAT yourself."
Okey, DC++ works, but only in passive mode, I need to be in active mode.
I want to run DC on port 9669 both TCP and UDP.
I have forwarded this ports to my host machine in the router.

I've figured out that I need to config the [b]/etc/vmware/vmnet8/nat/nat.conf[/] file.
Setup a port forwarding in this file, but just dont know how.
My nat.conf looks like this.
```
# Linux NAT configuration file
[host]
# NAT gateway address
ip = 172.16.36.2
netmask = 255.255.255.0
# or ip = 172.16.36.2/24

# enable configuration; disabled by default for security reasons
#configport = 33445

# VMnet device if not specified on command line
device = /dev/vmnet8

# Allow PORT/EPRT FTP commands (they need incoming TCP stream...)
activeFTP = 1

# Allows the source to have any OUI.  Turn this one if you change the OUI
# in the MAC address of your virtual machines.
#allowAnyOUI = 1

[udp]
# Timeout in seconds, 0 = no timeout, default = 60; real value might
# be up to 100% longer
timeout = 60

[incomingtcp]
# Use these with care - anyone can enter into your VM through these...

# fulDC
9669 = 172.16.36.128:6996

# FTP (both active and passive FTP is always enabled)
#      ftp localhost 8887
#8887 = 172.16.36.128:21

# WEB (make sure that if you are using named webhosting, names point to
#     your host, not to guest... And if you are forwarding port other
#     than 80 make sure that your server copes with mismatched port 
#     number in Host: header)
#      lynx http://localhost:8888
#8888 = 172.16.36.128:80

# SSH
#      ssh -p 8889 root@localhost
#8889 = 172.16.36.128:22

[incomingudp]
# UDP port forwarding example
#6000 = 172.16.36.128:6001

```

The fulDC line is for my DC client.
Please help. ;)

---

### Post by beefsprocket on 2005-11-02
Have you tried using the upnp option in the advanced settings dialog? Another thing to try is running dc++ under the new wine that was recently released ([http://winehq.org/)](http://winehq.org/)). For that matter, have you thought about trying linuxdc++? Give it a try, the new version seems much more functional than it has been in the past, to the point where I think that it may be more useful on linux than windows. There are plenty of posts around detailing how to compile and install it. Worth a look ;)

---

### Post by jnk on 2005-11-02
I've tried with and without the upnp option. I'm pretty sure it's a config matter in VMWare and not DC++.
Going to try the new Wine release, hope it works better with DC++ (fulDC actualy) than the previous versions.
Yes, I've tried LinuxDC++ (Wulfor Reloaded) but it was a bit to buggy, crashed all the time.
And I cant use a dc client that crashes, DC is far to important for me. ;)

---

