---
title: "EFI PXE Boot - Nothing happens after DHCPACK"
date: 2023-11-15
forum: General Help
---

### Post by hustluh on 2023-11-15
Hello everyone!

I'm at my wits end trying to establish a functioning PXE booting methodology for my company to successfully deploy new VMs more efficiently.

Currently, we are using a Foreman instance (I also have access to Cobbler, but it isn't established) to "create" the host. This builds a pxelinux.cfg file for the MAC address, and gains an IP address via DHCP.

When I go into VMWare and spin up the VM, the DHCP process runs, verifies the IP is good, then just drops off and kicks me out into the Boot Manager, where I have the options of EFI Virtual disk (0.0) [no media], EFI VMware Virtual SATA CDROM Drive (0.0) [no media], and EFI Network (nothing happens).

My DHCP config file currently reads as such:

```
default-lease-time 43200;
max-lease-time 86400;


not authoritative;




ddns-update-style none;


option domain-name "spectric.dev";
option domain-name-servers dns.spectric.dev;
option ntp-servers none;


allow booting;
allow bootp;


option fqdn.no-client-update    on;  # set the "O" and "S" flag bits
option fqdn.rcode2            255;
option pxegrub code 150 = text;








# required for UEFI HTTP boot
if substring (option vendor-class-identifier, 0, 10) = "HTTPClient" {
option vendor-class-identifier "HTTPClient";
}
# promote vendor in dhcpd.leases
set vendor-string = option vendor-class-identifier;
# next server and filename options
next-server 10.48.30.102;
option architecture-type code 93 = unsigned integer 16;
if option architecture-type = 00:06 {
  filename "grub2/grubia32.efi";
} elsif option architecture-type = 00:07 {
  filename "grub2/grubx64.efi";
} elsif option architecture-type = 00:09 {
  filename "grub2/grubx64.efi";
} else {
  filename "pxelinux.0";
}


log-facility local7;


include "/etc/dhcp/dhcpd.hosts";
# spectric.dev
subnet 10.48.30.0 netmask 255.255.255.0 {
  pool
  {
    range 10.48.30.50 10.48.30.100;
    deny all clients;
  }
  option subnet-mask 255.255.255.0;
  option routers 10.48.30.255;
  option domain-search "spectric.dev";
}

```

TFTP is ran via tftpd-hpa, and served via /srv/tftp (our /var space is limited). All of the files are found there that should be sources (i.e. grub2/grubx64.efi), and I have tftpd-hpa pointing to /srv/tftp as the root directory.

Nothing shows in logs past the DHCPACK flagged establishment of the IP to MAC.

I am hopeful this forum could be a resource to finally solve my 2-month endeavor.

---

### Post by hustluh on 2023-11-27
Anyone have any input/advice to try? Here is my tcpdump of the activity:

```
root:~# tcpdump -i ens160 port 67 or port 68 -e -n -vv
tcpdump: listening on ens160, link-type EN10MB (Ethernet), capture size 262144 bytes
22:58:42.312622 00:0c:29:43:12:d5 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 389: (tos 0x0, ttl 64, id 50402, offset 0, flags [none], proto UDP (17), length 375)
    0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:0c:29:43:12:d5, length 347, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Client-Ethernet-Address 00:0c:29:43:12:d5
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Discover
            MSZ Option 57, length 2: 1472
            Parameter-Request Option 55, length 35:
              Subnet-Mask, Time-Zone, Default-Gateway, Time-Server
              IEN-Name-Server, Domain-Name-Server, Hostname, BS
              Domain-Name, RP, EP, RSZ
              TTL, BR, YD, YS
              NTP, Vendor-Option, Requested-IP, Lease-Time
              Server-ID, RN, RB, Vendor-Class
              TFTP, BF, GUID, Option 128
              Option 129, Option 130, Option 131, Option 132
              Option 133, Option 134, Option 135
            GUID Option 97, length 17: 0.86.77.151.201.146.26.10.66.6.241.183.233.172.67.18.213
            NDI Option 94, length 3: 1.3.0
            ARCH Option 93, length 2: 7
            Vendor-Class Option 60, length 32: "PXEClient:Arch:00007:UNDI:003000"
22:58:42.312951 00:0c:29:e5:da:db > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 342: (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
    10.48.30.50.67 > 255.255.255.255.68: [udp sum ok] BOOTP/DHCP, Reply, length 300, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Your-IP 10.48.30.89
          Server-IP 10.48.30.50
          Client-Ethernet-Address 00:0c:29:43:12:d5
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Offer
            Server-ID Option 54, length 4: 10.48.30.50
            Lease-Time Option 51, length 4: 2053495
            Subnet-Mask Option 1, length 4: 255.255.255.0
            Domain-Name-Server Option 6, length 4: 10.48.30.50
            Domain-Name Option 15, length 12: "spectric.dev"
            BR Option 28, length 4: 10.48.30.255
22:58:42.315032 00:0c:29:0c:f1:f9 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 342: (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
    10.48.30.102.67 > 255.255.255.255.68: [udp sum ok] BOOTP/DHCP, Reply, length 300, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Your-IP 10.48.30.89
          Server-IP 10.48.30.102
          Client-Ethernet-Address 00:0c:29:43:12:d5
          file "grub2/grubx64.efi"
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Offer
            Server-ID Option 54, length 4: 10.48.30.102
            Lease-Time Option 51, length 4: 43200
            Subnet-Mask Option 1, length 4: 255.255.255.0
            Default-Gateway Option 3, length 4: 10.48.30.255
            Domain-Name-Server Option 6, length 4: 10.48.30.50
            Domain-Name Option 15, length 12: "spectric.dev"
22:58:43.361465 00:09:0f:09:01:12 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 377: (tos 0x10, ttl 16, id 0, offset 0, flags [none], proto UDP (17), length 363)
    10.48.30.1.67 > 255.255.255.255.68: [udp sum ok] BOOTP/DHCP, Reply, length 335, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Your-IP 10.48.30.104
          Client-Ethernet-Address 00:0c:29:43:12:d5
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Offer
            Server-ID Option 54, length 4: 10.48.30.1
            Lease-Time Option 51, length 4: 604800
            Subnet-Mask Option 1, length 4: 255.255.255.0
            Default-Gateway Option 3, length 4: 10.48.30.1
            Domain-Name-Server Option 6, length 12: 10.48.30.50,1.1.1.3,1.0.0.3
            NTP Option 42, length 4: 10.48.30.1
            RN Option 58, length 4: 302400
            RB Option 59, length 4: 529200
            T224 Option 224, length 33: 70.71.49.48.48.70.84.75.50.49.48.48.52.54.56.49.70.71.49.48.48.70.84.75.50.49.48.48.52.57.49.52.0
22:58:46.129783 00:0c:29:43:12:d5 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 401: (tos 0x0, ttl 64, id 50403, offset 0, flags [none], proto UDP (17), length 387)
    0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:0c:29:43:12:d5, length 359, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Client-Ethernet-Address 00:0c:29:43:12:d5
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Request
            Server-ID Option 54, length 4: 10.48.30.102
            Requested-IP Option 50, length 4: 10.48.30.89
            MSZ Option 57, length 2: 65280
            Parameter-Request Option 55, length 35:
              Subnet-Mask, Time-Zone, Default-Gateway, Time-Server
              IEN-Name-Server, Domain-Name-Server, Hostname, BS
              Domain-Name, RP, EP, RSZ
              TTL, BR, YD, YS
              NTP, Vendor-Option, Requested-IP, Lease-Time
              Server-ID, RN, RB, Vendor-Class
              TFTP, BF, GUID, Option 128
              Option 129, Option 130, Option 131, Option 132
              Option 133, Option 134, Option 135
            GUID Option 97, length 17: 0.86.77.151.201.146.26.10.66.6.241.183.233.172.67.18.213
            NDI Option 94, length 3: 1.3.0
            ARCH Option 93, length 2: 7
            Vendor-Class Option 60, length 32: "PXEClient:Arch:00007:UNDI:003000"
22:58:46.130130 00:0c:29:e5:da:db > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 342: (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
    10.48.30.50.67 > 255.255.255.255.68: [udp sum ok] BOOTP/DHCP, Reply, length 300, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Your-IP 10.48.30.89
          Server-IP 10.48.30.50
          Client-Ethernet-Address 00:0c:29:43:12:d5
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: ACK
            Server-ID Option 54, length 4: 10.48.30.50
            Lease-Time Option 51, length 4: 2053491
            Subnet-Mask Option 1, length 4: 255.255.255.0
            Domain-Name-Server Option 6, length 4: 10.48.30.50
            Domain-Name Option 15, length 12: "spectric.dev"
            BR Option 28, length 4: 10.48.30.255
22:58:46.130264 00:0c:29:0c:f1:f9 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 342: (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
    10.48.30.102.67 > 255.255.255.255.68: [udp sum ok] BOOTP/DHCP, Reply, length 300, xid 0x4a79134f, Flags [Broadcast] (0x8000)
          Your-IP 10.48.30.89
          Server-IP 10.48.30.102
          Client-Ethernet-Address 00:0c:29:43:12:d5
          file "grub2/grubx64.efi"
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: ACK
            Server-ID Option 54, length 4: 10.48.30.102
            Lease-Time Option 51, length 4: 43200
            Subnet-Mask Option 1, length 4: 255.255.255.0
            Default-Gateway Option 3, length 4: 10.48.30.255
            Domain-Name-Server Option 6, length 4: 10.48.30.50
            Domain-Name Option 15, length 12: "spectric.dev"

```

---

