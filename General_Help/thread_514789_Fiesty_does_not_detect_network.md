---
title: "Fiesty does not detect network"
date: 2007-08-01
forum: General Help
---

### Post by Justbill on 2007-08-01
I recently installed "Fiesty Fawn". I had been using "Dapper", succesfully for quite some time. When I installed "Dapper", it automatically detected and configured to my broadband conection. I am using a wired router. "Fiesty" can't seem to make the connection. Is there a terminal command, to get the system to configure the network, or ethernet card, or whatever the problem is? 

When I ran "Fiesty" from the cd, the internet worked fine, after the install, no internet.

Thank You 
Justbill

---

### Post by Shib on 2007-08-01
sudo ifup eth0

that should give you some sort of error message if it's not working right.

also, can you please paste the output of "sudo ifconfig"?

---

### Post by Shib on 2007-08-01
oh, read this thread -> [http://ubuntuforums.org/showthread.php?t=514648](http://ubuntuforums.org/showthread.php?t=514648)

as well to make sure it's not that exact same issue that we just solved :)

---

### Post by Justbill on 2007-08-01
here is that output:


bill@bill-desktop:~$ sudo ifup eth0
Password:
ifup: interface eth0 already configured
bill@bill-desktop:~$ sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29196 (28.5 KiB)  TX bytes:29196 (28.5 KiB)

bill@bill-desktop:~$ 



I have to leave for work, thanks for your help! I will try some more later

Justbill

---

### Post by Shib on 2007-08-01
odd... try doing a "ifdown eth0" then "ifup eth0"...

also, what does "sudo cat /etc/network/interfaces" give you?

other things... wire's plugged in and the lights are lit up right? and is there something ethernet related in your "lspci"?

ifconfig should of shown you _something_ for eth0... hmm...

also might want to try a "ifconfig eth0" and a "dhclient eth0" as well...

strange issue! I love it! :)

---

### Post by Justbill on 2007-08-01
Well, I have checked all cat 5 wires, the lights are on (however it seems no one is home) on my router, and on my ethernet card. In my first post I had said that my internet worked from the live cd, well I have since tried that again and............no internet. I am tempted tp start taking things apart at this point :-) 

I did run your previous sugestions and here is the output:


bill@bill-desktop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 10542
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:12:17:5a:6f:73
Sending on   LPF/eth0/00:12:17:5a:6f:73
Sending on   Socket/fallback
bill@bill-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:12:17:5a:6f:73
Sending on   LPF/eth0/00:12:17:5a:6f:73
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@bill-desktop:~$ sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43056 (42.0 KiB)  TX bytes:43056 (42.0 KiB)

bill@bill-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:12:17:5a:6f:73
Sending on   LPF/eth0/00:12:17:5a:6f:73
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@bill-desktop:~$ this sucks!
bash: this: command not found
bill@bill-desktop:~$ 

I am at a loss what to do, maybe try re-installing? I don't know.

Thanks for all your help
Justbill

---

### Post by Justbill on 2007-08-01
O.K. The latest:

I have re-installed 7.0.4 , still no internet! To eliminate the idea of a wiring problem, I dis-connected my  computer's cat5 cable, from the ethernet card in the back of the machine, and connected it to my sons laptop,and.........and.........and.......(win xp is soooooo slow) finally, internet connection! So this eliminates a problem with the wiring or the router, as the laptop connected. I have not checked any further  on the ethernet card, other than, when I re-connected the cat 5 cable, the lights on the card came on. So, that only leaves me with the idea that this has to be a configuration problem. I am using a "Leviton" 4 port internet gateway. Is it possible the "Fiesty" is not "seeing" the router? I took 6.06 off, to install 7.04, and the old operating system was having no trouble with the internet. 

This box is a:
HP pavillion 6630
500Mhz celeron
128Mb ram

At a Total Loss
Justbill

---

### Post by Shib on 2007-08-01
what are the last 5-10 lines of output from

"sudo dmesg"

and 

"sudo cat /var/log/messages"

might (oh please help us no) be a driver/hardware issue....

---

### Post by confused57 on 2007-08-01
> **Justbill said:**
> O.K. The latest:

I have re-installed 7.0.4 , still no internet! To eliminate the idea of a wiring problem, I dis-connected my  computer's cat5 cable, from the ethernet card in the back of the machine, and connected it to my sons laptop,and.........and.........and.......(win xp is soooooo slow) finally, internet connection! So this eliminates a problem with the wiring or the router, as the laptop connected. I have not checked any further  on the ethernet card, other than, when I re-connected the cat 5 cable, the lights on the card came on. So, that only leaves me with the idea that this has to be a configuration problem. I am using a "Leviton" 4 port internet gateway. Is it possible the "Fiesty" is not "seeing" the router? I took 6.06 off, to install 7.04, and the old operating system was having no trouble with the internet. 

This box is a:
HP pavillion 6630
500Mhz celeron
128Mb ram

At a Total Loss
Justbill

May not work, but you could open a terminal and try:
```
sudo /etc/init.d/networking restart
```

---

### Post by Justbill on 2007-08-02
OK, the last 10 lines of sudo dmesg:

[31149.753950]  [<c02c9221>] devinet_ioctl+0x551/0x6c0 
[31149.753995]  [<c0283f3b>] dev_ifsioc+0xeb/0x360 
[31149.754011]  [<c01f2099>] copy_to_user+0x29/0x50 
[31149.754099]  [<c0277e9f>] sock_ioctl+0xbf/0x210 
[31149.754122]  [<c0277de0>] sock_ioctl+0x0/0x210 
[31149.754143]  [<c018269b>] do_ioctl+0x2b/0x90 
[31149.754171]  [<c018275c>] vfs_ioctl+0x5c/0x2a0 
[31149.754200]  [<c0182a12>] sys_ioctl+0x72/0x90 
[31149.754226]  [<c01031f0>] sysenter_past_esp+0x69/0xa9 
[31149.754292]  ======================= 





the last 10 lines of sudo cat /var/log/messages:

Aug  2 04:30:10 bill-desktop kernel: [31149.753924]  [dev_change_flags+252/304] dev_change_flags+0xfc/0x130 
Aug  2 04:30:10 bill-desktop kernel: [31149.753950]  [devinet_ioctl+1361/1728] devinet_ioctl+0x551/0x6c0 
Aug  2 04:30:10 bill-desktop kernel: [31149.753995]  [dev_ifsioc+235/864] dev_ifsioc+0xeb/0x360 
Aug  2 04:30:10 bill-desktop kernel: [31149.754011]  [copy_to_user+41/80] copy_to_user+0x29/0x50 
Aug  2 04:30:10 bill-desktop kernel: [31149.754099]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210 
Aug  2 04:30:10 bill-desktop kernel: [31149.754122]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210 
Aug  2 04:30:10 bill-desktop kernel: [31149.754143]  [do_ioctl+43/144] do_ioctl+0x2b/0x90 
Aug  2 04:30:10 bill-desktop kernel: [31149.754171]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0 
Aug  2 04:30:10 bill-desktop kernel: [31149.754200]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90 
Aug  2 04:30:10 bill-desktop kernel: [31149.754226]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9 
Aug  2 04:30:10 bill-desktop kernel: [31149.754292]  ======================= 








also networking restart did not work, but thanks for the idea.

thanks 
Justbill

---

### Post by Selage on 2007-08-02
Can you give us a view of your interfaces file

[QUOTE=]what does "sudo cat /etc/network/interfaces" give you?
[/QUOTE]

Greetz

---

### Post by Justbill on 2007-08-02
well, here is the output from sudo cat /etc/network/interfaces :

bill@bill-desktop:~$ sudo cat /etc/network/interfaces 
Password: 
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 

bill@bill-desktop:~$ 

I hope this sheds some light on this problem. 

Justbill

---

### Post by Justbill on 2007-08-02
Well, at this point I think we can eliminate a hardware problem. I am currently posting this from the box that I have "Feisty" installed on, that won't connect to the internet! I downloaded, and burnt the latest offering from "PCLinux" on my other machine, and am currently running the live cd in the box that has "Feisty" installed, and...............I have internet connection. Which only leaves me to conclude that it is an issue with "Feisty". I am half tempted to go ahead and install "PCLnux", but, I have used Ubuntu for a couple of years now, and have become attached to it (sentimental sap that i am :-) ).

So I have not given up on "Feisty", I think now we can narrow things down a bit though. The ethernet card, the wiring, and the router obviously work.

Thanks for all the help, and suggestions so far!!!!
I am sure through the process of elimination we will get "Feisty" working.

Thanks 
Justbill

---

