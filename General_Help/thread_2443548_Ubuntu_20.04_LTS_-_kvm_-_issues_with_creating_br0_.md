---
title: "Ubuntu 20.04 LTS - kvm - issues with creating br0 bridge"
date: 2020-05-17
forum: General Help
---

### Post by upuntumonnen on 2020-05-17
Hi,  I upgraded to Ubuntu 20.04 LTS yesterday. Everything works great out of the box but I have issues creating br0 bridge for kvm. I need the bridged connection in order to set up different guest services on LAN. I've configured this before multiple times but 20.04 has something different.   Tried steps  I have installed bridge-utils along with other kvm and virt-manager tools.  ```
sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager
```  I restored my "/etc/network/interfaces" from previous 18.04 installation.  ```
cat /etc/network/interfaces # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback  # The primary network interface #auto enp5s0 #iface enp5s0 inet dhcp  auto br0 iface br0 inet dhcp         bridge_ports enp5s0         bridge_fd 9         bridge_hello 2         bridge_maxage 12         bridge_stp off
```  I the rebooted my device and checked my interfaces. No br0 found. Before br0 was automatically created this way. ```
$ ip a : lo:  mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00     inet 127.0.0.1/8 scope host lo        valid_lft forever preferred_lft forever     inet6 ::1/128 scope host        valid_lft forever preferred_lft forever 2: enp5s0: 
 mtu 1500 qdisc fq_codel state UP group default qlen 1000     link/ether 18:31:bf:27:26:d4 brd ff:ff:ff:ff:ff:ff     inet 192.168.1.47/24 brd 192.168.1.255 scope global dynamic noprefixroute enp5s0        valid_lft 83484sec preferred_lft 83484sec     inet6 fe80::2f67:e473:91bb:6dcb/64 scope link noprefixroute        valid_lft forever preferred_lft forever 3: virbr0:  mtu 1500 qdisc noqueue state DOWN group default qlen 1000     link/ether 52:54:00:7b:70:e1 brd ff:ff:ff:ff:ff:ff     inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0        valid_lft forever preferred_lft forever 4: virbr0-nic: 
 mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000     link/ether 52:54:00:7b:70:e1 brd ff:ff:ff:ff:ff:ff
```   ```
$ ifconfig enp5s0: flags=4163  mtu 1500         inet 192.168.1.47  netmask 255.255.255.0  broadcast 192.168.1.255         inet6 fe80::2f67:e473:91bb:6dcb  prefixlen 64  scopeid 0x20         ether 18:31:bf:27:26:d4  txqueuelen 1000  (Ethernet)         RX packets 55089  bytes 67037864 (67.0 MB)         RX errors 0  dropped 0  overruns 0  frame 0         TX packets 29733  bytes 2796266 (2.7 MB)         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0  lo: flags=73  mtu 65536         inet 127.0.0.1  netmask 255.0.0.0         inet6 ::1  prefixlen 128  scopeid 0x10         loop  txqueuelen 1000  (Local Loopback)         RX packets 7742  bytes 625936 (625.9 KB)         RX errors 0  dropped 0  overruns 0  frame 0         TX packets 7742  bytes 625936 (625.9 KB)         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0  virbr0: flags=4099  mtu 1500         inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255         ether 52:54:00:7b:70:e1  txqueuelen 1000  (Ethernet)         RX packets 0  bytes 0 (0.0 B)         RX errors 0  dropped 0  overruns 0  frame 0         TX packets 0  bytes 0 (0.0 B)         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```  I've tried different settings in the "/etc/network/interfaces" file but they don't seems to hold. For example, following doesn't work:  ```
# The primary network interface # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback  auto enp5s0 iface enp5s0 inet dhcp
```  but following works (I don't think this should work) ```
 # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback  # The primary network interface #auto enp5s0 #iface enp5s0 inet dhcp  auto virbr0 iface virbr0 inet dhcp         bridge_ports enp5s0         bridge_fd 9         bridge_hello 2         bridge_maxage 12         bridge_stp off 
```    Any help with this is greatly appreciated. Apologies if I forgot to post something that is usually required here. Just ask and I'll deliver :)

---

### Post by upuntumonnen on 2020-05-17
Quick addition.  When I say that the last example works ("but following works (I don't think this should work) "), I mean that I at least get a working IP address for enp5s0 that I can use to access internet. The br0 bridge is still missing.  ```
$ cat /etc/network/interfaces  # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback  # The primary network interface #auto enp5s0 #iface enp5s0 inet dhcp  auto virbr0 iface virbr0 inet dhcp         bridge_ports enp5s0         bridge_fd 9         bridge_hello 2         bridge_maxage 12         bridge_stp off
```  ```
 ip a 1: lo:  mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00     inet 127.0.0.1/8 scope host lo        valid_lft forever preferred_lft forever     inet6 ::1/128 scope host         valid_lft forever preferred_lft forever 2: enp5s0: 
 mtu 1500 qdisc fq_codel state UP group default qlen 1000     link/ether 18:31:bf:27:26:d4 brd ff:ff:ff:ff:ff:ff     inet 192.168.1.47/24 brd 192.168.1.255 scope global dynamic noprefixroute enp5s0        valid_lft 76040sec preferred_lft 76040sec     inet6 fe80::2f67:e473:91bb:6dcb/64 scope link noprefixroute         valid_lft forever preferred_lft forever 3: virbr0:  mtu 1500 qdisc noqueue state DOWN group default qlen 1000     link/ether 52:54:00:7b:70:e1 brd ff:ff:ff:ff:ff:ff     inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0        valid_lft forever preferred_lft forever 4: virbr0-nic: 
 mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000     link/ether 52:54:00:7b:70:e1 brd ff:ff:ff:ff:ff:ff
```

---

### Post by upuntumonnen on 2020-05-23
The answer was Netplan. Thank you for playing.

---

### Post by TheFu on 2020-05-23
> **upuntumonnen said:**
> The answer was Netplan. Thank you for playing.

Could you please post your working netplan YAML file?  Netplan replaced ifupdown in 2017. The fact that the interfaces worked at all in 18.04 surprises me.  Did you upgrade or install fresh?

Also, can you please mark this thread as solved?  "Thread Tools" button just above the 1st post.  Save the volunteers some time. Please.

---

### Post by upuntumonnen on 2020-05-31
Thanks [**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685").

I had a freshly installed 18.04 and I did a clean fresh install from 18.04 to 20.14. I assume that my configurations worked in 18.04 because it had ifup and ifdown. 20.04 doesn't seem to have these.

Here are my working netplan configurations:

```
cat /etc/netplan/01-network-manager-all.yaml
# Let NetworkManager manage all devices on this system
#network:
#  version: 2
#  renderer: NetworkManager

network:
  version: 2
  renderer: networkd 
  ethernets:
     enp5s0:
        dhcp4: true
  bridges:
     br0:
       interfaces: [enp5s0]
       dhcp4: true
       optional: true

```

```

cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

These settings disable Network Manager graphical options but they definitely work and I'm used to setting up my system this way.

---

