---
title: "Internet Connection"
date: 2007-12-11
forum: General Help
---

### Post by spikehackerinc on 2007-12-11
Hey there guys... :D I just got Ubuntu in the post this morning and looks great!!!

I have run into a little problem. I cannot get my internet running, my ISP drivers are only for windows. Unless there is a way to execute .exe in linux... Which i'm not sure will work anyway.

So I hope someone can maybe help me set up my connection manually or give me drivers that work... 

I'm from South Africa using WBS, Iburst service. If that can be of any help... I wasn't sure where I should post this, so please just head me on in the right direction... 

Thank you very much and looking forward to using Ubuntu. :popcorn:

---

### Post by eggdeng on 2007-12-11
You need to specify your connection type, ie modem, wired ethernet card, wireless ethernet.
Take a look in System -> Administration -> Networking to see if any network interfaces are present. You will find general help at [http://https://help.ubuntu.com/7.10/internet/C/connect.html]("http://https://help.ubuntu.com/7.10/internet/C/connect.html")

---

### Post by NotRoot:-) on 2007-12-11
You should open a terminal, ( Applications, Accessories, Terminal ) and type
ifconfig -a

you should see something like this:
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:25:23:76:EB  
          inet addr:10.45.40.109  Bcast:10.45.40.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe23:76eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2396832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3073013255 (2.8 GiB)  TX bytes:149252973 (142.3 MiB)
          Base address:0x2080 Memory:e8100000-e8120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)

u610user@YRUHere:~$ 

lo is your loopback interface.  eth0 is the ethernet interface used for internet connections.

in the terminal,  type    netstat -nra to see you default Gateway.

This all assumes that you are using ethernet.

I have heard of a program called Wine, to run windows applications in Linux.  But I have never used it.
It seams strange to need drivers to access your ISP.  Maybe try asking them for Linux drivers?

---

### Post by p_quarles on 2007-12-11
You *don't* need drivers to access your ISP. The only drivers you need are for the network interface card itself. If it's an ethernet connection, the problem should be easy to fix. If it's wireless, you may need to install the correct driver for the card (not for the ISP).

The only time you would need additional software to access your ISP is if they use a Windows-specific authentication program. Aside from dial-up access, I've never heard of anyone doing this: most authentication programs (for WiFI, etc.) are web applications, which are OS-independent. 

In any case, let us know what kind of internet access you are using, and run the command that NotRoot mentioned to get more information about the problem.

---

### Post by Dark Hornet on 2007-12-11
p_quarles  is right, you DO NOT need drivers to access your ISP.  What type of connection are you on...wireless, cable, ISDN (i hope not :) ), dsl, etc.

---

