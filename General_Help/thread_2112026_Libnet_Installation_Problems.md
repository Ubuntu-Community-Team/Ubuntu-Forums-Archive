---
title: "Libnet Installation Problems"
date: 2013-02-03
forum: General Help
---

### Post by dansofe0r on 2013-02-03
Hello experienced ubuntu enthusiasts. I am trying to install Libnet-1.0.2a in my /usr/lib folder. I have a later version of libnet installed that I got from the ubuntu software center. So, when I try to 'make && make install' I get the following: 
```

/usr/lib/Libnet-1.0.2a$ sudo make && make install
ar -cr lib/libnet.a src/libnet_resolve.o src/libnet_socket.o src/libnet_checksum.o src/libnet_prand.o src/libnet_version.o src/libnet_write_ip.o src/libnet_insert_ipo.o src/libnet_insert_tcpo.o src/libnet_error.o src/libnet_link_sockpacket.o src/libnet_packet_mem.o src/libnet_build_ip.o src/libnet_build_tcp.o src/libnet_build_udp.o src/libnet_build_arp.o src/libnet_build_ethernet.o src/libnet_build_icmp.o src/libnet_build_igmp.o src/libnet_build_dns.o src/libnet_build_snmp.o src/libnet_build_rip.o src/libnet_build_ospf.o src/libnet_build_vrrp.o src/libnet_asn1.o src/libnet_hex_dump.o src/libnet_if_addr.o src/libnet_port_list.o 
ranlib lib/libnet.a
make: stat: src/libnet_resolve.o: Permission denied
make: *** No rule to make target `src/libnet_resolve.o', needed by `libnet'.  Stop.

```

Do I need to install in a different directory? I currently have the Libnet-1.0.2a folder in the usr/lib folder.  I have also already executed ./configure. 
Do I need to uninstall the other newer version of libnet? 

Thank you.

---

