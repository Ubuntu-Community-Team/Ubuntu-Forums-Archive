---
title: "network problem 10.04 ==&gt; 12.04"
date: 2012-10-19
forum: General Help
---

### Post by deserthowler on 2012-10-19
I did the upgrade and it went sort of well 
[http://ubuntuforums.org/showthread.php?t=2068666]("http://ubuntuforums.org/showthread.php?t=2068666").

I did some searching on the problem but apparently can't find the right terms.  I'm sure I'm not the only one having this problem.

This is the error message I get at boot:

    [LIST]
[*]waiting for network configuration ...
[*]waiting up to 60 more seconds for network configuration
[*]booting system without full network configuration
[/LIST]

When I tried the live CD everything worked OK.  I'm using a Dell 1420n and ran Ubuntu on this box since 7.04 with very few problems.

Here is my network card info from lspci:
> 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

ifconfig yields:> 
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:fc:f0:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1610 (1.6 KB)  TX bytes:1610 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:7a:15:7b  
          inet addr:192.168.10.102  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe7a:157b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2951456 (2.9 MB)  TX bytes:656596 (656.5 KB)

I am multibooting with Mint 13 and Ubuntu 10.04 and having no problems with either.

I can connect with either WiFi or ethernet cable and things work but I have the boot error.  It just takes longer to boot with Ubuntu on the hard drive than with the live CD.

Earl

---

### Post by deserthowler on 2012-10-23
About time to give it a bump I guess.

Earl

---

### Post by Impavidus on 2012-10-23
I had a similar problem. Have a look at [http://ubuntuforums.org/showthread.php?t=2070965](http://ubuntuforums.org/showthread.php?t=2070965)

---

### Post by deserthowler on 2012-10-31
I tried the solution you provided in the link.  No luck.  In fact it totally messed up my internet connection.  Mint 13 works on the same computer so I know it's not a hardware problem.  Guess I'll try it again later, just to see how it works out.

Earl

---

### Post by pqwoerituytrueiwoq on 2012-10-31
i had this happen to me when i setup a system from the mini.iso
i know i googed the message text, dont recall what i did to fix it

you can edit the script that waits for that
/etc/init/failsafe.conf

```
    30        # waiting on it to start.
    31        $PLYMOUTH message --text="Waiting for network configuration..." || :
    32        sleep 40
    33    
[B]    34        $PLYMOUTH message --text="Waiting up to 60 more seconds for network configuration..." || :
    35        sleep 59[/B]
    36        $PLYMOUTH message --text="Booting system without full network configuration..." || :
    37    
    38        # give user 1 second to see this message since plymouth will go

```comment out the bold lines (put a # symbol at the start of the line)

have you tried this:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1043244/comments/6](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1043244/comments/6)

---

### Post by deserthowler on 2012-11-01
Booted this morning and everything works fine. :confused: I have no idea what happened, if it was an update or what.

Earl

---

