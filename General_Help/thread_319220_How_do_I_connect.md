---
title: "How do I connect?"
date: 2006-12-15
forum: General Help
---

### Post by UKPunk on 2006-12-15
Hi everyone,
Please excuse my ignorance if this is a stupid question.
I've just installed Ubuntu 6.06 from the CD to run alongside windows. Although I can connect to the internet in Windows, I've got no connection in Ubuntu. Presumably I need to configure Ubuntu, but haven't got a clue where to start. Thanks in advance for your help and assistance.

---

### Post by bollix47 on 2006-12-15
Start with:

System - Administration - Networking

Is your connection listed?
Is it enabled?  i.e. Does it have a checkmark in the small box on the left?

If not enabled click on the connection, then click on properties and click on "Enable this connection".

---

### Post by pandu.rs on 2006-12-15
Well, if u still cant figure out what to do.. lets see what is configured.

in ubuntu run the following commands and paste its output

1. sudo ifconfig -a
2. netstat -nr

In windows run the following commands (when ur connected to internet) and paste its output

1. ipconfig /all
2. netstat -nr

Also do u know if ur ISP assigns IP using DHCP?

---

### Post by UKPunk on 2006-12-17
Hi Guys,
Sorry I took so long....kids and Christmas etc.
I think I've got the info regarding what's configured.

**In Windows**
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\DaveandAngie>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : elmden-b4i8grmj
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : NVIDIA nForce MCP Networking Control
ler
        Physical Address. . . . . . . . . : 00-0C-76-37-D8-D3

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 802.11g USB 2.0 adapter
        Physical Address. . . . . . . . . : 00-0B-6B-6A-61-4D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.87
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 16 December 2006 18:31:33
        Lease Expires . . . . . . . . . . : 17 December 2006 18:31:33

C:\Documents and Settings\DaveandAngie>netstat -nr

Route Table
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 0c 76 37 d8 d3 ...... NVIDIA nForce MCP Networking Controller - Packet
 Scheduler Miniport
0x3 ...00 0b 6b 6a 61 4d ...... 802.11g USB 2.0 adapter - Packet Scheduler Minip
ort
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1    192.168.1.87       25
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.1.0    255.255.255.0     192.168.1.87    192.168.1.87       25
     192.168.1.87  255.255.255.255        127.0.0.1       127.0.0.1       25
    192.168.1.255  255.255.255.255     192.168.1.87    192.168.1.87       25
        224.0.0.0        240.0.0.0     192.168.1.87    192.168.1.87       25
  255.255.255.255  255.255.255.255     192.168.1.87               2       1
  255.255.255.255  255.255.255.255     192.168.1.87    192.168.1.87       1
Default Gateway:       192.168.1.1
===========================================================================
Persistent Routes:
  None

C:\Documents and Settings\DaveandAngie>


**In Ubuntu**
qwestor@afenaf:~$ sudo ifconfig -a
eth0    Link encap:Ethernet  HWaddr 00:0C:76:37:D8:D3
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
        Interrupt:177 Base address:0x6000

eth2    Link encap:Ethernet  HWaddr 00:0B:6B:6A:61:4D
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0b)  TX bytes:0 (0.0b)

lo       Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 ScopeHost
        UP LOOPBACK RUNNING MTU:16436  Metric:1
        RX packets:295 errors:0 dropped:0 overruns:0 frame:0
        TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:21844 (21.3KiB)  TX bytes:21844 (21.3KiB)

sit0    Link encap:IPv6-in-IPv4
        NOARP  MTU:1480  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:0 (0.0b)  TX bytes:0 (0.0b)

qwestor@afenaf:~$ netstat -nr
Kernal IP routing table
Destination    Gateway     Genmask      Flags  MSS Window irtt Iface
qwestor@afenaf:~$



With the Ubuntu stuff, after managing to configure my printer I printed off the results and then typed it in. I only mention this in case there's any typos in there. As you can tell I really am an absolute newbie! To be honest I understand very little of the above although I am working on that.

thanks again for all your help.

---

### Post by UKPunk on 2006-12-17
Sorry Bollix47,
I forgot to mention that the connection is listed and enabled.:???:

---

### Post by houstonbofh on 2006-12-17
What kind of WiFi card (stick) is it?

---

### Post by UKPunk on 2006-12-17
Please excuse my ignoarance but how would i find that out?:redface:

---

### Post by UKPunk on 2006-12-17
I'm not sure if this is what you mean but I'm on Orange (aka Wanadoo, aka freeserve) using an Inventel wireless connection. (Am I making any sense?)
It's just a thought but is it possible that Windows firewall could be the problem or am I talking out of my backend?

---

### Post by mr_boo1711 on 2006-12-17
Hi Guys,

I'm new to Linix too - only downloaded and installed ubuntu today.  Well impressed so far but i'm getting the same problem as you UKPunk - I cant get my Wifi (Which is built in to the Asus MB) to come up on my list of network devices and I can enable it ok.  But my Belking router doesnt appear on the SSID list and when manually typed in it still doesnt connect.  

I'm ok with windows, but Linux is making me feel like a bit of a thicko!! lol ;)

I suspect UKPunk and myself are having the same issue, so if anyone has any advice then please tell - likewise, if I solve the issues or come up with any ideas then i'll let you guys know.

Steve

---

### Post by UKPunk on 2006-12-17
Thanks very much mr_boo1711.
I'm off to bed now but I'll check back tomorrow to see if anyone's come up with a solution. I'll also see what I can find on how to's etc.

---

### Post by mr_boo1711 on 2006-12-18
> **mr_boo1711 said:**
>  I cant get my Wifi (Which is built in to the Asus MB) to come up on my list of network devices and I can enable it ok.

Apologies for the typo - I meant to say I CAN get my wifi connection device to come up, and I CAN enable it ok..   

Whoops! :oops:

---

