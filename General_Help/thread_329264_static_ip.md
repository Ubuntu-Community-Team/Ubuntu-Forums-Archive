---
title: "static ip"
date: 2007-01-01
forum: General Help
---

### Post by Doug11 on 2007-01-01
I'm trying to setup port forward for my utorrent. Can someone point me in the right direction as to get my static ip or how to set one up if I don't already have one.

---

### Post by ayoli on 2007-01-01
Menu System>Administration>Network
select the connection you're using, click "properties" button on the right and see(or set) your ip here.

another way: in a terminal type in:
```
ifconfig
```
will show you all your network interfaces config

---

### Post by Doug11 on 2007-01-01
eth1      Link encap:Ethernet  HWaddr 00:16:CE:32:FD:D6  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe32:fdd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


So when I go into my router settings,, where it says to enter static ip,,would I enter in the 192.168.0.101,,which is more like the ip of my router,,or would it be the actual ip of my machine which is not shown here,,but starts like this  142.177.xxx.xx

---

### Post by blackmh on 2007-01-01
Manually assign IP address to computer (must be in same subnet as router) and just forward needed ports to assigned IP address.

---

### Post by Doug11 on 2007-01-02
OK,, Tried a few diferent things but could'nt get anything to work. Right now in my network config, i have it set up for Automatic Configeration(DHCP). Do I have to change to static ip in this section,,and if so,,whcih ip should i enter for IP Address,,my router IP (192,168.0.101) or my machine IP (142.178.xxx.xx),,subnet should just be the 255.255.255.255 and the default gateway is from what i understand the same as the above IP.   
Now,,once I have this part figured out, I then have to go into my router settings and enter my private IP,,which should be my static IP, which I'm not quite sure shold be. Any help greatly appreciated. Thx.   
The reason being for all this is I need to do a port forward for Utorrent.

---

### Post by ayoli on 2007-01-02
142.178.xxx.xxx is a public range so this must be your public IP (usually assigned by your isp). 

assuming your router ip is 192.168.0.101, your local subnet is 192.168.0.0 &nd subnet mask is 255.255.255.0. 

so your machines on your local network should have an ip in your local subnet range (from 192.168.0.1 to 192.168.0.254 except 101 which is your router).

hope that helps.

---

### Post by bodhi.zazen on 2007-01-02
Static IP
	[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

[http://www.ubuntuforums.org/showthread.php?&t=313282](http://www.ubuntuforums.org/showthread.php?&t=313282)

---

### Post by Doug11 on 2007-01-02
Thanks Bodhi,,,that second thread worked great. Wonder why i didnt come across that when i did my search?

---

### Post by bodhi.zazen on 2007-01-02
> **Doug11 said:**
> Thanks Bodhi,,,that second thread worked great.

You are most welcome ;)


> Wonder why i didnt come across that when i did my search?

To make me look smarter then I am of course :p

---

