---
title: "ltsp problem"
date: 2015-08-24
forum: General Help
---

### Post by asusv2 on 2015-08-24
I just can't get this terminal server to work, every time I try to boot a client with PXE from the ltsp server I get this error massage.

[IMG]http://1.1m.yt/-y68dHzAS.jpg[/IMG][B]

ifconfig
[/B]```

eth0    inet addr:192.168.10.133  Bcast:192.168.10.255  Mask:255.255.255.0

```

the **/etc/ltsp/dhcpd.conf** file
```

authoritative;

subnet 192.168.10.0 netmask 255.255.255.0 {
    range 192.168.10.20 192.168.10.40;
    option domain-name "example.com";
    option domain-name-servers 8.8.8.8;
    option broadcast-address 192.168.10.255;
    option routers 192.168.10.2;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "ltsp/i386/pxelinux.0";
    } else {
        filename "ltsp/i386/nbi.img";
    }
}

```

the **/etc/default/tftpd-hpa** file
```

RUN_DAEMON="yes"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"
TFTP_OPTIONS="--verbosity 5"

```

**(changed all folders and subfolders to 777)**
```

**ls -l /opt/ltsp **
drwxrwxrwx 20 root root 4096 avg 23 22:17 i386
drwxrwxrwx  2 root root 4096 avg 24 00:56 images

**ls -l /var/lib/tftpboot**
drwxrwxrwx 3 root root 4096 avg 24 15:08 ltsp

```

[B]/etc/init.d/tftpd-hpa status
/etc/init.d/openbsd-inetd status[/B]
```

tftpd-hpa.service - LSB: HPA's tftp server
   Loaded: loaded (/etc/init.d/tftpd-hpa)
   Active: active (running)

openbsd-inetd.service - LSB: Start or stop the inetd daemon.
   Loaded: loaded (/etc/init.d/openbsd-inetd)
   Active: active (running)

```

updated the image (multiple times, without problems)
sudo ltsp-build-client --arch i386
sudo ltsp-update-sshkeys
sudo ltsp-update-image

...no firewall running

---

### Post by asusv2 on 2015-08-24
forgot logs

```

Aug 24 20:13:19 user-virtual-machine dhcpd: DHCPDISCOVER from 00:0c:29:d5:b7:ad via eth0
Aug 24 20:13:19 user-virtual-machine dhcpd: DHCPOFFER on 192.168.10.21 to 00:0c:29:d5:b7:ad via eth0
Aug 24 20:13:21 user-virtual-machine dhcpd: DHCPREQUEST for 192.168.10.21 (192.168.10.133) from 00:0c:29:d5:b7:ad via eth0
Aug 24 20:13:21 user-virtual-machine dhcpd: DHCPACK on 192.168.10.21 to 00:0c:29:d5:b7:ad via eth0
Aug 24 20:13:21 user-virtual-machine in.tftpd[3962]: RRQ from 192.168.10.21 filename /ltsp/i386/pxelinux.0
Aug 24 20:13:21 user-virtual-machine in.tftpd[3962]: sending NAK (2, Forbidden directory) to 192.168.10.21
Aug 24 20:13:21 user-virtual-machine in.tftpd[3963]: RRQ from 192.168.10.21 filename /ltsp/i386/pxelinux.0
Aug 24 20:13:21 user-virtual-machine in.tftpd[3963]: sending NAK (2, Forbidden directory) to 192.168.10.21

```

---

