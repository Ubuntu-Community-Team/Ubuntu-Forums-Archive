---
title: "wired connection not working"
date: 2015-11-07
forum: General Help
---

### Post by Capiru on 2015-11-07
I have installed ubuntu 15.10 as a dual boot alongside windows 10, and on my windows 10 os i also have ubuntu 15.10 installed as a virtual machine. So here's the problem: when i boot into ubuntu my wired connection does not work ( and i do not have wireless just fyi ), but, when i login into windows my wired connection in both windows and vm work fine. I installed both with the same ubuntu dvd. I have a TG580 router if this helps, and if i try to login into my router using mozilla on the linux boot, not even that works.

heres a couple things that i tried so far: formatting linux, booting from a live cd, booting from a live cd from a different version (14.04), copying the firmware file from the virtual machine (which is working) into an usb and then sudo cp -u -a usb /lib/firmware/ and then a reboot, when that didn't work : sudo cp -a usb /lib/firmware/ into another reboot, tried fiddling with sudo ipconfig eth0 down/up but didn't work as well, tried sudo dhclient eth0 but seemed like my terminal stopped working (received the command and gave no response and accepted no more commands, dunno if it's supposed to work that way), tried turning my router on/off, rebooting.

---

### Post by TheFu on 2015-11-07
Inside the VM, the Linux OS only sees a virtual NIC, not the actual NIC*inside the machine.

From the linux boot,  run **sudo  lshw    -C   network** and post  those results back  here. Please use code tags.

---

### Post by Capiru on 2015-11-07
sudo lshw -C network
```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 06
       serial: fc:aa:14:2e:bc:a4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:30 ioport:e000(size=256) memory:fe900000-fe900fff memory:d0000000-d0003fff

```
ifconfig
```
enp6s0    Link encap:Ethernet  HWaddr fc:aa:14:2e:bc:a4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fe2e:bca4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:235 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12408 (12.4 KB)  TX bytes:13660 (13.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75380 (75.3 KB)  TX bytes:75380 (75.3 KB)



```

and when i ran sudo dhclient enp6s0 it said something like RMNETWORK answers: File exists or file found something like that (My usb became corrupted and lost the file, but it was something like that with one line)
@edit:
this is also the second time my usb becomes corrupted when i bring stuff from linux to windows, is there any drivers i'm missing?

---

### Post by TheFu on 2015-11-07
Likely driver issue with that specific NIC and version.
[http://ubuntuforums.org/showthread.php?t=2301202&p=13383205#post13383205](http://ubuntuforums.org/showthread.php?t=2301202&p=13383205#post13383205)

---

### Post by Capiru on 2015-11-07
This did not work on 15.10, but i figured the drives were for 14.04, so i formatted into 14.04 and tried again and worked, though it did overwrite my dual boot file when i installed 14.04 over 15.10, looking into fixing that now.
@edit
downloaded boot-repair and now everything works fine again, thanks.

---

### Post by TheFu on 2015-11-07
s/drives/drivers/ - correct? Best if that confusion isn't left.

Would have thought the fix would have made it into the 15.10 kernel. I understand it was submitted upstream, though I don't touch non-LTS releases.

If solved, please change that in the thread tools.

---

