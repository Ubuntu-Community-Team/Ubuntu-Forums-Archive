---
title: "I get the signal(wireless), but I can't go to anywhere"
date: 2008-06-27
forum: General Help
---

### Post by Ioky on 2008-06-27
I just install xubuntu in my laptop with IEEE 802.11b Wi-Fi. And last night, when I browsing the web, I just get dis-connect. the signal get pick up(It actually can pick up many other network.) However, I just can't doing anything with the internet. any one have any idea, what goes wrong? When I try my wireless with Live CD, it works fine. I am pretty new to Linux wireless thing, it is my first time using wireless with Linux. but I just can't figure it out what actually goes wrong.

Intel PRO/Wireless 2100 wireless adapter

Thanks

---

### Post by Ioky on 2008-06-27
anyone?

---

### Post by johanhartman on 2008-06-27
Is the network you want to use encrypted. I set up my wireless last night and the same thing happened. I fixed it by setting up the network in System >> Administration >> Network, I opened the wireless section and entered the encryption details, seems to be working fine now.

Before that I used network manager to set it up (accessed through the network icon on the top right), this would see networks and their strengths but wouldn't connect.

If you set it up like I do and hover over the network icon on the top right it should say "Manual Configuration". I'd say if you haven't tried that yet its worth a go, otherwise try [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") though its a little long winded.

---

### Post by p_quarles on 2008-06-27
Well, you didn't say what wireless adapter you're using, but regardless, this is something I've seen before. You may able to fix it by restarting networking on the system:
```
sudo /etc/init.d/networking restart
```
Let us know what happens after you run that.

---

### Post by Ioky on 2008-06-27
> **p_quarles said:**
> Well, you didn't say what wireless adapter you're using, but regardless, this is something I've seen before. You may able to fix it by restarting networking on the system:
```
sudo /etc/init.d/networking restart
```
Let us know what happens after you run that.

It is build-in adapter, Intel PRO/Wireless 2100. haha sorry, I think I should mention that at the beginning.

I tried, it doesn't work.... 

Thanks though.

---

### Post by Gunman1982 on 2008-06-27
Check by running 'sudo iwconfig' (if it tells you unknown command install the package wireless-tools with synaptic) to which network your laptop is trying to connect. Check if the essid is set and the string behind 'Access Point:' doesn't say 'Not associated'

or post the output here (make sure that you remove the string behind 'Encryption Key' if there is one) and in addition post the string of 'iwlist eth1 scanning' so we can see which access points are available and if they are openly accessible.

---

### Post by Ioky on 2008-06-27
ioky@Varius:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:84:3B:BE   
          Bit Rate=2 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=72/100  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

ioky@Varius:~$ iwlist eth1 scanning
eth1      No scan results

That is what I get. I mean as I say, before, I do get signal but I just can't go to any site or downloading anything

haha I am such noob on wireless things. Thanks for helping me out

---

### Post by Gunman1982 on 2008-06-27
Mhhh what puzzles me is that your iwlist says 'No scan results' can you try to run it again? sometimes it just misses some beacons. Do you have a button on your laptop to activate or deactivate wireless lan? Check if it is on and if yes than please give an output of the command 'ifconfig eth1'.

---

### Post by plucky on 2008-06-27
Scanning is a privileged operation

Try ```
sudo iwlist eth1 scan
```


Good Luck

---

### Post by Gunman1982 on 2008-06-27
ah sry forgot to mention the sudo.

---

### Post by Ioky on 2008-06-27
eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:0F:50:02
                    ESSID:"05B408577194"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:53  Signal level:0  Noise level:0
                    Extra: Last beacon: 216ms ago
          Cell 02 - Address: 00:13:10:1B:71:54
                    ESSID:"Chidori"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 212ms ago
          Cell 03 - Address: 00:13:10:73:95:5A
                    ESSID:"ptak"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:31  Signal level:0  Noise level:0
                    Extra: Last beacon: 0ms ago
          Cell 04 - Address: 00:0C:41:84:3B:BE
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:31  Signal level:0  Noise level:0
                    Extra: Last beacon: 208ms ago

That is what I getting, I doesn't see any problem. but I just can't to net .... haha funny day

---

### Post by jpryor68 on 2008-06-27
> **Ioky said:**
> ioky@Varius:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:84:3B:BE

From the above, it looks like you are successfully (not only getting the signal from, but also) connecting to your access point. So the problem is either (1) with your access point's connection to the internet, or (2) with your access point not giving you an IP address.

Evidence against (1) is that you are able to connect to the network via the Live CD; however the problem may be intermittent.

If the problem is (2), this is what usually fixes it for me:
```
sudo dhclient eth1
```

If that doesn't fix your problem, do the following and post the results back here:

```
sudo ifconfig eth1
```

---

### Post by Ioky on 2008-06-27
ioky@Varius:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:3a:b5:02
Sending on   LPF/eth1/00:0c:f1:3a:b5:02
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.104 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.104 from 192.168.1.1
bound to 192.168.1.104 -- renewal in 33768 seconds.
ioky@Varius:~$ sudo ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0c:f1:3a:b5:02  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe3a:b502/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16023 (15.6 KB)  TX bytes:12958 (12.6 KB)
          Interrupt:11 Base address:0x2000 Memory:cfffe000-cfffefff 

That is what I got. The thing is something when i pick the signal, it can go to a web, but after a while, it start can't to anyway. I just hope that is it not the hardware's problem. But when I try the wireless with Live CD it always work, don't know why.

Really, I have ZERO idea, it is just like the wireless MAGICALLY doesn't work. haha

---

### Post by Ioky on 2008-06-27
so lost in the middle of the forest

---

### Post by Ioky on 2008-06-27
I got this when I do ping

ioky@Varius:~ ping google.com

ping: unknown host google.com

---

### Post by Ioky on 2008-06-28
no one know what is going on?

---

### Post by p_quarles on 2008-06-28
Go easy on the bumping. If someone knows, they will answer. Bumping more than once every 24 hours, though, is impolite.

---

### Post by IcemanV9 on 2008-06-28
Looks like you are connected to the internet (see post #13). Your /etc/resolv.conf might be the problem since you cannot ping any website (google.com). If it is empty, then put this in /etc/resolv.conf file for testing purpose only.
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Here's a good [[COLOR="Orange"]wiki[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") on wireless troubeshooting.

---

### Post by jpryor68 on 2008-06-28
> **IcemanV9 said:**
> Looks like you are connected to the internet (see post #13). Your /etc/resolv.conf might be the problem since you cannot ping any website (google.com). If it is empty, then put this in /etc/resolv.conf file for testing purpose only.
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```



I'm also favoring the diagnosis that you're connecting fine, you just have a problem with name lookups.

If this is in fact the problem, then you should get errors from commands like these:

```
host www.google.com
ping -c3 www.google.com

```
but this should work fine:

```
ping -c3 74.125.47.99

```
(That's one of the [www.google.com](www.google.com) addresses.)

As to how to fix the problem, you'll need to start looking at /etc/resolv.conf as the previous poster said.

Do you have the resolvconf package installed? If so that takes over management of the /etc/resolv.conf file. Check its documentation in /usr/share/doc.

Normal practice with wifi routers is to set one's nameservers on the router itself, and just have a line like:

```
nameserver 192.168.1.1

```
in /etc/resolv.conf.

For troubleshooting, though, you can try manually entering nameservers in the /etc/resolv.conf file first, until you get a working configuration. Then think about trying to get your machine to get its nameservers from the router.

---

### Post by Ioky on 2008-06-29
Thanks all the help guys, I am sorry to be so hurry earlier. Though I still haven't solve my problem, but I try it until it works

---

### Post by Ioky on 2008-07-01
I don't know what is actually the problem is in my case. But I am thinking to upgrade my wireless adapter anyway so hope that help a little bit. I just wonder could it be just because my adapter doesn't have good support with the my network today, it is a very old 802.11b only adapter, so. I don' t know, sometime I can go the net, with some connection(not the one I have.) Since I basically can do nothing else, I hope upgrading my network adapter can solve the problems, Thanks every one for the help.

---

### Post by Ioky on 2008-07-01
I finally fix my problem, I need to go into the router and and change it to 802.11b+ only in order to get it work. now it works fine.

Thanks a lot guy.

---

