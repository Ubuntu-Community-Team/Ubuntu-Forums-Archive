---
title: "Remote Desktop Help"
date: 2012-10-25
forum: General Help
---

### Post by 1971 on 2012-10-25
Hi,

I have Lubuntu 12.10 and want to connect to it via RDP on my Windows 8 PC. I installed the XRDP package from the instructions here.

[http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/](http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/)

However when I try to connect from the Win8 PC by both Lubuntu Host name and IP it cannot find the Lubuntu machine. I have created a second user account on Lubuntu as well.

I can ping the Lubuntu from my windows but cannot connect

Thank You for any help

---

### Post by steeldriver on 2012-10-26
Is the RDP port (3389 iirc) open for inbound connections on the target machine?

---

### Post by 1971 on 2012-10-26
> **steeldriver said:**
> Is the RDP port (3389 iirc) open for inbound connections on the target machine?

how do i check that?

cheers

---

### Post by 1971 on 2012-10-26
> **steeldriver said:**
> Is the RDP port (3389 iirc) open for inbound connections on the target machine?

OK can connect now to login screen when I try to login with either the main account or second account I created on the Lubuntu box I get the error

[IMG]http://hillclimbnsw.org.au/im.jpg[/IMG]
[IMG]http://icbweb.com/im.jpg[/IMG][IMG]http://www.icbweb.com/im.jpg[/IMG]

I even log out of the Lubuntu box and get the same error

Thanks

---

### Post by steeldriver on 2012-10-27
I'm confused what you're trying to do here - do you have an SSH tunnel from the remote RDP port to port 3350 on your client machine - or are you really trying to connect to a session on the same host as the client?

---

### Post by 1971 on 2012-10-27
> **steeldriver said:**
> I'm confused what you're trying to do here - do you have an SSH tunnel from the remote RDP port to port 3350 on your client machine - or are you really trying to connect to a session on the same host as the client?

What I am trying to do is log onto the Lubuntu box from my Windows 8 box via RDP. All I did was follow the instructions on the link I put on the first post. There are two separate machines. I don't understand what you mean.

Thank you for trying maybe it can be resolved.

Cheers

---

### Post by steeldriver on 2012-10-27
what I'm confused about is why your sessman screengrab is showing the localhost loopback address (127.0.0.1) rather than the IP address of the target machine

if that's a result of ssh tunneling all well and good (it *will* show the localhost in that case) - but I would suggest getting the thing working without tunneling first provided you are behind a router / NAT, i.e. specify the LAN IP of the target machine (the same IP you use to ping it)

---

### Post by 1971 on 2012-10-27
> **steeldriver said:**
> what I'm confused about is why your sessman screengrab is showing the localhost loopback address (127.0.0.1) rather than the IP address of the target machine

if that's a result of ssh tunneling all well and good (it *will* show the localhost in that case) - but I would suggest getting the thing working without tunneling first provided you are behind a router / NAT, i.e. specify the LAN IP of the target machine (the same IP you use to ping it)

As far as I know I don't use or have setup SSH Tunneling. I' just using the default settings on both machines. In the RDP client program on the Windows box I am trying to connect to the IP I got from using ifconfig on the Lubuntu box.

I don't know where to look to address this, the Lubuntu or Windows box. My Router/Modem is a Netgear CG3100 as configured by my ISP but works fine using RDP windows to windows box

Many thanks

---

### Post by steeldriver on 2012-10-27
sounds like you are reading the 'lo' (loopback) interface details from ifconfig - ignore those and find the IP address associated with the real network interface (usually eth0 or eth1 for wired - wlan0 or somesuch if you are using wireless) on the target machine

post your ifconfig output here if you need help

---

### Post by 1971 on 2012-10-27
> **steeldriver said:**
> sounds like you are reading the 'lo' (loopback) interface details from ifconfig - ignore those and find the IP address associated with the real network interface (usually eth0 or eth1 for wired - wlan0 or somesuch if you are using wireless) on the target machine

post your ifconfig output here if you need help

As a thought I tried connecting to the Lubuntu box from my Windows 7 Laptop. Just to make sure there was not some stupid problem with the Windows 8 Desktop PC. Unfortunately I got the same error word for word. I am very much a on and off again user with Linux as a full desktop OS install but use Linux live CD's for Windows troubleshooting weekly. Last time I had Ubuntu as full install on a desktop (Hardy I think) I used vino from memory to connect to a Windows terminal server (The reverse of what I am doing now) I seem to remember some configuration required on the Ubuntu box (Can't remember what though) but it was minimal and worked flawlessly. Fore this project I just followed the instructions on that link I provided but it did not mention any "extra" configuration or installation of programs/dependencies.

Here is the output for ifconfig. I have been using 192.168.0.5. Many thanks


p@p-G31M-S2L:~$ sudo ifconfig
[sudo] password for p: 
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:1e:ae:3c  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe1e:ae3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13639 (13.6 KB)  TX bytes:12662 (12.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23052 (23.0 KB)  TX bytes:23052 (23.0 KB)

---

