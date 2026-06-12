---
title: "internet does not work after browsing in windows boot"
date: 2007-12-02
forum: General Help
---

### Post by rob1101 on 2007-12-02
well when i browse the internet on my windows partition and then reboot in to Ubuntu 7.10, I cannot connect to the internet with Ubuntu, unless I power down the PC and unplug it for a few seconds then every thing works perfectly. 

does anyone know why this is happening? or more importantly how i can fix it?

---

### Post by p_quarles on 2007-12-02
It sounds like Windows is shutting off the NIC during the shutdown sequence. You should be able to turn this off in the Windows networking settings, but I don're recall exactly how this is done. 

To manually enable the NIC from the command line, you can do this:
```
ifconfig -a
```
That will list all your network interfaces. An ethernet port will usually be listed as "eth0," but doublecheck.

Once you know the logical name of your NIC, you can turn it on by typing:
```
sudo ifup eth0
```
If you're unable to figure out how to prevent Windows from shutting it off, you could always add this command to the Ubuntu startup sequence.

---

### Post by rob1101 on 2007-12-04
thx

---

### Post by rob1101 on 2007-12-04
actually i thought it woked but it didnt i tried to start up NIC from the terminal like you said and this is what i got. 

```

[robert@robert-desktop:~]$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:09:25:FD:04  
          inet6 addr: fe80::211:9ff:fe25:fd04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x4d00 

eth0:avah Link encap:Ethernet  HWaddr 00:11:09:25:FD:04  
          inet addr:169.254.4.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x4d00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6356 (6.2 KB)  TX bytes:6356 (6.2 KB)

[robert@robert-desktop:~]$ sudo ifup eth0
[sudo] password for robert:
Ignoring unknown interface eth0=eth0.
[robert@robert-desktop:~]$ sudo ifup eth0:avah
Ignoring unknown interface eth0:avah=eth0:avah.
[robert@robert-desktop:~]$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
[robert@robert-desktop:~]$ sudo ifup lo
ifup: interface lo already configured
[robert@robert-desktop:~]$ 

```

what did i do wrong?

---

### Post by p_quarles on 2007-12-04
You didn't do anything wrong. What's happening is that the connection to the LAN isn't working as normal, and it's giving you a zeroconf network address (169.254.4.155). I could be wrong, but I believe this configuration works only if you directly connected to the WAN (i.e., no router).

My guess is that this has something to do with how Windows is interacting with the NIC. I experienced a similar issue when I was dual-booting (and I think it was around the time I switched to 7.10 pre-release). I fixed it by assigning a static IP address to the Ubuntu installation.

In any case, one thing to check here before trying to fix it. If you can post your interface configuration file, that will help troubleshoot. 
```
cat /etc/network/interfaces
```

---

### Post by rob1101 on 2007-12-04
```

[robert@robert-desktop:~]$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

[robert@robert-desktop:~]$ 


```

---

### Post by p_quarles on 2007-12-04
> **rob1101 said:**
> ```

[robert@robert-desktop:~]$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

[robert@robert-desktop:~]$ 


```
Okay, well that definitely shows the problem. It's not configuring your NIC at *all*. 

This is the standard configuration:
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```You can edit those lines into the file by running:
```
sudo nano /etc/network/interfaces
```Add them to the bottom. You should be able to test this without restarting your system, by restarting the network:
```
sudo /etc/init.d/networking restart
```If that doesn't work, go ahead and reboot to see if that makes a difference (it shouldn't, but it's good to be thorough). 

Finally, what kind of interface are you using? Is this integrated ethernet, or is it a PCI card? If you're not sure, I can show you how to find out.

---

### Post by rob1101 on 2007-12-04
i did what you said above. rebooted anyway to windows to browse the web for a sec rebooted in to ubuntu to see if it worked and it didn't. 

this is what i atempted to try to get it working

```

[robert@robert-desktop:~]$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:09:25:FD:04  
          inet6 addr: fe80::211:9ff:fe25:fd04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xed00 

eth0:avah Link encap:Ethernet  HWaddr 00:11:09:25:FD:04  
          inet addr:169.254.4.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3902 (3.8 KB)  TX bytes:3902 (3.8 KB)

[robert@robert-desktop:~]$ sudo ifup eth0
[sudo] password for robert:
ifup: interface eth0 already configured
[robert@robert-desktop:~]$ 

```

 i had to shutdown and unplug my pc for a few seconds and then boot back up. 

and im using integrated Ethernet. it comes straight from the MOBO

---

### Post by p_quarles on 2007-12-04
Okay. I'm guessing that setting a static address will solve this. Quick question first: has this NIC worked okay with other Linux installations? I ask because I am aware of some situations where people couldn't get their onboard ethernet working. It's very rare, but if you've never gotten this one to work correctly in Linux, then you can't rule that out. 

First thing is you need to figure out your LAN IP range and your router's IP address. If you don't know these, you can get them by logging into your router's configuration page. LANs come in three categories, each of which specifies a range of addresses, like 192.168.0.1 through 192.168.255.255. Your router is usually going to be the device ending in "1."

Once you have that, you need to edit /etc/network/interfaces again. Replace the word "dhcp" (in the addition I gave you) with "static." Now add the following three lines (to the end of the file):
```
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
```
Note that you will need to replace the number in "address" with one that fits your LAN IP range, and replace the one in "gateway" with the IP address of your router.

---

### Post by rob1101 on 2007-12-08
> **p_quarles said:**
> Okay. I'm guessing that setting a static address will solve this. Quick question first: has this NIC worked okay with other Linux installations? I ask because I am aware of some situations where people couldn't get their onboard ethernet working. It's very rare, but if you've never gotten this one to work correctly in Linux, then you can't rule that out. 

First thing is you need to figure out your LAN IP range and your router's IP address. If you don't know these, you can get them by logging into your router's configuration page. LANs come in three categories, each of which specifies a range of addresses, like 192.168.0.1 through 192.168.255.255. Your router is usually going to be the device ending in "1."

Once you have that, you need to edit /etc/network/interfaces again. Replace the word "dhcp" (in the addition I gave you) with "static." Now add the following three lines (to the end of the file):
```
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
```Note that you will need to replace the number in "address" with one that fits your LAN IP range, and replace the one in "gateway" with the IP address of your router.

yes i have gotten the Ethernet to work before in linux. and how do i get to my routers configuration page?

---

### Post by p_quarles on 2007-12-08
> **rob1101 said:**
> yes i have gotten the Ethernet to work before in linux. and how do i get to my routers configuration page?
You can get there by typing its network address in your web browser. It's most likely:
```
192.168.0.1
```
since that's the default gateway address for most networks. If that doesn't work, there are some ways of finding it.

---

### Post by rob1101 on 2007-12-15
sorry im just getting back to this now, its been a little busy lately. 

any way that ip did not work, how can i find out what mine is?

---

### Post by rob1101 on 2007-12-17
bump

---

### Post by p_quarles on 2007-12-17
Okay, just did a quick search on how to find your router IP using Windows (since that's where the network seems to be functioning correctly). Start > Run > Command -- at the prompt type:
```
ipconfig
```
It should spit out several address, and the "gateway" is your router's address. Once you have that, you will hopefully be able to get around this problem.

---

