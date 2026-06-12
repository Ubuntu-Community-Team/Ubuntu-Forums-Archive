---
title: "Ubuntu – “Activation of network connection failed” wifi works but sometimes it stops"
date: 2022-09-02
forum: General Help
---

### Post by master-55555 on 2022-09-02
[B][SIZE=3][FONT=times new roman]I tried everything but it doesn't work wifi of network failed error it works for 1 hour then this error comes and wifi disappears
  wlp3s0 is connected but after sudo lshw -C network it seems that enp2s0 is connected.






subhan@subhan-comp:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: f0:2f:74:4c:ec:7b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.048.00-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 ioport:e000(size=256) memory:fc904000-fc904fff memory:fc900000-fc903fff
  *-network
       description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 94:08:53:64:fa:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=5.15.0-46-generic firmware=N/A ip=192.168.1.82 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:81 ioport:d000(size=256) memory:fc800000-fc80ffff



sudo nmcli connection show
NAME             UUID                                  TYPE                                      DEVICE          
ALHN-E738 2      ee6e758a-570b-4c32-ae65-59c8c473f509  wifi            wlp3s0          
br-1540dc100ab8  07a04c6e-3406-45e3-8fe7-3582be67c10e  bridge    br-1540dc100ab8 
br-1e89040960f2  f423243c-fc26-4dba-87b5-5762d69d38c4  bridge    br-1e89040960f2 
br-4c35e4c03d42  73146eee-4cfa-415b-bcf0-32c98ec697bd  bridge    br-4c35e4c03d42 
br-59a597e6774c  ad0a12fe-32c7-44a5-a5ea-c3e686651aec  bridge    br-59a597e6774c 
br-5c510e51036f  a9c9ee51-7316-458b-bde3-465cbf76abc3  bridge    br-5c510e51036f 
br-62b05783c88f  49b1c332-b6b4-4288-be19-24edc64ea571  bridge    br-62b05783c88f 
br-73d3fbdf14aa  eab12e2d-8186-4bd7-ada4-b0b4023afec7  bridge    br-73d3fbdf14aa 
br-84d990d5c139  546adc94-73f2-47d4-98eb-2d0de69a438b  bridge    br-84d990d5c139 
br-8aeca049bbe8  1450f687-ff11-4477-9db1-9fbe7dc9b831  bridge    br-8aeca049bbe8 
br-8c826c1d8a39  c54b812f-1555-4c0f-8dd1-ff1c953ca8a5  bridge    br-8c826c1d8a39 
br-b7f109fbdb17  cce03201-fd31-4ae4-abe1-6864d2e80c63  bridge    br-b7f109fbdb17 
br-bf66b1604eee  925adda5-3e71-44e2-8896-e3d1d4c80516  bridge    br-bf66b1604eee 
br-d747d2a926cc  81b20c15-4242-4a9b-926b-650a60c340c2  bridge    br-d747d2a926cc 
br-e79031311dbc  4fe74df9-3765-4b9b-b9fe-51e1501a815d  bridge    br-e79031311dbc 
br-ef3ed8ecda41  4e4c6bc5-5e5a-47eb-8552-957cde6942ce  bridge    br-ef3ed8ecda41 
br-f8a9ad1573d9  619e0807-c280-440c-a917-805810135609  bridge    br-f8a9ad1573d9 
docker0          88b33baa-786c-40c2-8cd8-8f8516a1fa04  bridge    docker0         
70mai_d02_1f33   d6144797-7ed1-4c0b-9d22-de6b6495ff2d  wifi      --              
ALHN-C967        3f72db28-5ae0-4d3e-929d-5dd83eaccf53  wifi      --              
ALHN-E738        cc90ba03-3641-410d-849a-4f30d8bdb25c  wifi      --              
ALHN-E738 1      e445e4ae-d1b1-475e-b487-8a3a290b1286  wifi      --              
Azadliq_150a     7f70c692-1587-4c9b-9b1b-53f9e2a26309  wifi      --              
Azerbaycan       f994e94a-e0d9-4def-bdab-4506ae638bab  wifi      --              
Birlink-23       499c5ed9-990a-4d6a-a643-4b295e8550fd  wifi      --              
BirLink_5        dffa52a3-884e-4a23-b0c8-7f84bff3f536  wifi      --              
INNOLAND         b75eac9a-80dd-403d-9c9f-6e0a7921c6d5  wifi      --              
Mobile           72739b02-f64f-4d2e-a4c4-cec29ac57b79  wifi      --              
netplan-enp2s0   7ea6f90b-3495-3533-948a-ef0035687c34  ethernet  --              
[/FONT][/SIZE][/B]
[LIST=1]
[*]**[SIZE=3][FONT=times new roman]Receb            c1b0d7ed-a231-4dd8-bf5b-2dffcda72905  wifi      --[/FONT][/SIZE]**
[/LIST]
[B][SIZE=3][FONT=times new roman]


sudo  nano /etc/netplan/*.yaml

renderer: NetworkManager
  ethernets:
    enp2s0:
      .....
     ......


[/FONT][/SIZE][/B]**[SIZE=3][FONT=times new roman]ip a[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 127.0.0.1/8 scope host lo[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet6 ::1/128 scope host [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether f0:2f:74:4c:ec:7b brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 94:08:53:64:fa:c9 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.1.82/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp3s0[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft 83635sec preferred_lft 83635sec[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet6 fe80::8c3e:94d5:7566:7f99/64 scope link noprefixroute [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]4: br-8aeca049bbe8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:81:18:1b:c7 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.22.0.1/16 brd 172.22.255.255 scope global br-8aeca049bbe8[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]5: br-b7f109fbdb17: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:a7:01:bc:31 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.20.0.1/16 brd 172.20.255.255 scope global br-b7f109fbdb17[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]6: br-e79031311dbc: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:26:05:eb:e4 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.32.1/20 brd 192.168.47.255 scope global br-e79031311dbc[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]7: br-1540dc100ab8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:e2:22:1b:eb brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-1540dc100ab8[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]8: br-4c35e4c03d42: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:7e:b8:b9:ac brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.80.1/20 brd 192.168.95.255 scope global br-4c35e4c03d42[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]9: br-59a597e6774c: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:47:75:be:45 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.128.1/20 brd 192.168.143.255 scope global br-59a597e6774c[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]10: br-d747d2a926cc: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:30:64:8e:93 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.24.0.1/16 brd 172.24.255.255 scope global br-d747d2a926cc[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]11: br-f8a9ad1573d9: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:7a:46:d5:48 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.48.1/20 brd 192.168.63.255 scope global br-f8a9ad1573d9[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]12: br-73d3fbdf14aa: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:bf:59:40:6f brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.112.1/20 brd 192.168.127.255 scope global br-73d3fbdf14aa[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]13: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:54:d1:87:17 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]14: br-bf66b1604eee: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:b0:f4:e3:3c brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.28.0.1/16 brd 172.28.255.255 scope global br-bf66b1604eee[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]15: br-1e89040960f2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:59:98:d2:80 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.23.0.1/16 brd 172.23.255.255 scope global br-1e89040960f2[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]16: br-5c510e51036f: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:0e:f7:22:c1 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.21.0.1/16 brd 172.21.255.255 scope global br-5c510e51036f[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]17: br-62b05783c88f: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:44:3d:07:4b brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.64.1/20 brd 192.168.79.255 scope global br-62b05783c88f[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]18: br-84d990d5c139: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:e5:35:3b:3f brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 192.168.96.1/20 brd 192.168.111.255 scope global br-84d990d5c139[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]19: br-8c826c1d8a39: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:86:c8:68:49 brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.29.0.1/16 brd 172.29.255.255 scope global br-8c826c1d8a39[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]20: br-ef3ed8ecda41: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default [/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    link/ether 02:42:55:e8:73:ee brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]    inet 172.19.0.1/16 brd 172.19.255.255 scope global br-ef3ed8ecda41[/FONT][/SIZE]**
**[SIZE=3][FONT=times new roman]       valid_lft forever preferred_lft forever[/FONT][/SIZE]**




Please help me

---

