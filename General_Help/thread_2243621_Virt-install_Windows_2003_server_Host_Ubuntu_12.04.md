---
title: "Virt-install Windows 2003 server Host Ubuntu 12.04 server"
date: 2014-09-10
forum: General Help
---

### Post by Baldry on 2014-09-10
Hey guys i am stuck with a problem here and i hope i found the right place for it. I am trying to install windows 2003 server with virt-install on a Ubuntu 12.04 server. So far i got the VM running (install started look at pic) but thats only a screenshot from my virsh command. I cant connect to it. I am using my ubuntu server over putty. 
virt-install --connect qemu:///system --hvm -n win2k3 -r 1024 -f  /lib/libvirt/images/windows.qcow2 -s 30 -c /home/user/cd1.iso --vnc  --noautoconsole --os-type windows --os-variant win2k3  --network=bridge:br0
thats the command i use to create the VM  and it does run but i cant connect to it because i dont know the IP. it does create a vnet2 on my ubuntu so if i type ifconfig i can see the mac adresse but no ip

vnet2     Link encap:Ethernet  Hardware Adresse xxxxxxxxxx
          inet6-Adresse: xxxxxxxxxxxxxxx Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:43268 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:500
          RX-Bytes:0 (0.0 B)  TX-Bytes:14551751 (14.5 MB)
( i am sorry but i have a german version)

i tryied to connect with vcn-viewer but the problem is i dont know what ip to type. i cant connect over virsh connect/console because there is no console to connect. so what do i do?
screenshot is attached so you can see that the installalation started.

---

### Post by Baldry on 2014-09-10
anyone? i just dont know what to do anymore. i need this windows server! and it must run on the ubuntu server :/

---

### Post by yancek on 2014-09-10
With VirtualBox running on my Linux machine and knowing what the MAC address is, I get the ip address with:  arp -a as you can see below, first line is VBox 2nd line the host.

> arp -a
? (192.168.0.5) at 08:00:27:c7:d0:82 [ether] on eth0
? (192.168.0.1) at 10:5f:06:23:8a:c0 [ether] on eth0


---

### Post by Baldry on 2014-09-11
if i type that i only see my maschien + the server. and its br0 not eth0 here. tried that befor too. seems like not many people did that with a server :( i just hope someone with some help will answer :D

---

### Post by Baldry on 2014-09-11
I didnt want to do that but i had to it seems like. i created a Ubuntu Desktop VM und connectet to the vm with 
virt-viewer -c qemu+ssh://ip/system Vm . I want to create and do all the work over the Server but it seems like that doesnt work. i am now on my way to install the windows.Thanks anyway

---

