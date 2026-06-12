---
title: "Installing LTSP on Hoary"
date: 2005-05-21
forum: General Help
---

### Post by warpedmind on 2005-05-21
Hi All, 

Trying to get LTSP running.

I have already gotten everything installed, DHCP is running and serving
IPs.

I am stuck on FTP.  PXE says it can't find the kernel file

I have followed the ubuntu wiki for LTSP, and LTSP documentation
[http://www.ubuntulinux.org/wiki/LTSPHowTo](http://www.ubuntulinux.org/wiki/LTSPHowTo)
[http://nodezero.blogspot.com/2005/04/ltsp-powered-by-ubuntu.html](http://nodezero.blogspot.com/2005/04/ltsp-powered-by-ubuntu.html)
[http://www.ltsp.org/documentation/ltsp-4.1/ltsp-4.1.3-en.html](http://www.ltsp.org/documentation/ltsp-4.1/ltsp-4.1.3-en.html)

all is good till they get to the configuring all the conf files. 

here is my dhcpd.conf

#DHCP.conf
default-lease-time            21600;
max-lease-time                21600;
ddns-update-style none;
allow booting;
allow bootp;

option subnet-mask            255.255.255.0;
option broadcast-address      192.168.0.255;
option routers                192.168.0.254;
option domain-name-servers    192.168.0.254;
option domain-name            "nbgcoffice.lan";
option root-path              "192.168.0.254:/opt/ltsp/i386";
option option-128 code 128 = string;
option option-129 code 129 = text;

shared-network WORKSTATIONS {
  subnet 192.168.0.0 netmask 255.255.255.0 {
     range dynamic-bootp 192.168.0.100 192.168.0.253;
     use-host-decl-names       on;
     option log-servers        192.168.0.254;

     # trick from Peter Rundle <peter.rundle@au.interpath.net>
     if substring (option vendor-class-identifier, 0, 9) = "PXEClient"
     {
        filename      "/var/lib/tftpboot/lts/pxe/pxelinux.0";
          # NOTE: kernels are specified in /tftpboot/lts/pxe/pxelinux.cfg/
     }
     else
     {
        filename    "/var/lib/tftpboot/lts/vmlinuz-2.6.9-ltsp-3";
     }
  }
}


Thanks for any help you all can offer.

Warpedmind

---

