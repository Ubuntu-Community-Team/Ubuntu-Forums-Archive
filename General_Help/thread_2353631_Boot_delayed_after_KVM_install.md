---
title: "Boot delayed after KVM install"
date: 2017-02-23
forum: General Help
---

### Post by monkeywrench2 on 2017-02-23
I have installed KVM with the following:
```
sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils qemu-system virt-manager
```

I then changed /etc/network/interfaces to contain the following:

```
auto lo 
iface lo inet loopback 
 
auto eth0 
iface eth0 inet manual 
 
auto br0 
iface br0 inet dhcp 
        bridge_ports eth0 
        bridge_stp off 
        bridge_fd 0 
        bridge_maxwait 0
```


When I reboot the computer after the KVM install and changes to the config file, it takes a long time to book. (6 or 7 minutes)  KVM works (mostly)
a partial output of dmesg is as follows:

```
[    2.991093] r8169 0000:02:00.0 enp2s0: link down
[    2.991095] r8169 0000:02:00.0 enp2s0: link down
[    2.991164] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    3.005805] ses 6:0:0:1: Attached Enclosure device
[    5.588990] r8169 0000:02:00.0 enp2s0: link up
[    5.588995] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[    5.772989] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1c.0/0000:01:00.1/sound/card1/input17
[    5.773072] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1c.0/0000:01:00.1/sound/card1/input18
[    5.773117] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1c.0/0000:01:00.1/sound/card1/input19
[    5.773160] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1c.0/0000:01:00.1/sound/card1/input20
[    5.905037] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   18.290833] random: crng init done
[  306.738211] ip_tables: (C) 2000-2006 Netfilter Core Team
[  306.746067] ip6_tables: (C) 2000-2006 Netfilter Core Team
[  306.757317] Ebtables v2.0 registered
[  306.971945] virbr0: port 1(virbr0-nic) entered blocking state
[  306.971946] virbr0: port 1(virbr0-nic) entered disabled state
[  306.971999] device virbr0-nic entered promiscuous mode
[  307.120048] nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
[  307.161879] virbr0: port 1(virbr0-nic) entered blocking state
[  307.161881] virbr0: port 1(virbr0-nic) entered listening state
[  307.256587] virbr0: port 1(virbr0-nic) entered disabled state
[  307.258481] device virbr0-nic left promiscuous mode
[  307.258499] virbr0: port 1(virbr0-nic) entered disabled state
[  323.931080] nouveau 0000:01:00.0: disp: 0x5ca3[0]: INIT_GENERIC_CONDITON: unknown 0x07
[  324.016896] nouveau 0000:01:00.0: disp: 0x5ca3[0]: INIT_GENERIC_CONDITON: unknown 0x07
[  628.547475] Bridge firewalling registered
```


I have always had trouble trying to get KVM to work.  Only once has it ever installed without messing up boot times and as far as I know I installed it exactly as described here on that
occasion as well.  
I just don't know enough about any of this to have a clue as to what to do about it.  Any help would be much appreciated.
Thanks.

---

### Post by DuckHook on 2017-02-23
Your port is not "eth0". dmesg reports it as "enp2s0". By using "eth0" in /etc/network/interfaces you are asking Network Manager to bridge to a non-existent port. Your long boot is due to the system waiting for Network Manager to time out before loading actual values that work.

I'm surprised that networking works for you at all in your VMs.

---

