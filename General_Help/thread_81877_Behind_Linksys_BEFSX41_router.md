---
title: "Behind Linksys BEFSX41 router"
date: 2005-10-25
forum: General Help
---

### Post by PoK on 2005-10-25
Hi Everyone,

I have Ubuntu Breezy installed, but Internet is not working for me behind Linksys BEFSX41 router. Only [www.google.com](www.google.com) works, nothing else!
apt also not working, or it is very slow..

Otherwise I can ping any hosts ([www.debian.org)](www.debian.org)), and nslookup also works.

Without Router, and setting up PPPOE connection: Internet and apt is working fine!

I tried:
- Firefox speed up steps
- Fix IP
- Another Linux distro: UHU live 1.2 - same situation
No luck...

Thanks,
PoK

---

### Post by dbott67 on 2005-10-25
Try the following:[LIST=1]
[*]Reboot/restart your Linksys Router and then restart your Ubuntu computer
[*]Check your firmware to see if it's the latest version; if not, update it and then try again
[*]If you have recently updated your firmware, try reverting to the previous versio (or just reset the router to factory settings --- just don't forget to make note of your ISP settings).[/LIST]The other thing to look for is the IP settings, particularly whether you're using DHCP or static IP, what your actual IP is, your subnet mask and gateway settings:[LIST=1]
[*]Are you using DHCP or static IP when connected to router?
[*]While connected to the router, type ifconfig and post the output here.
[*]Do the same while directly connected to the DSL modem.[/LIST]I've seen strange issues before where a computer's network settings get munged (particularly the DNS setting --- although, it appears that you can ping a hostname), as well as occasionally the routing table gets a weird entry (which needs to be deleted).

The other issue could be related to MTU settings on the router. Mine is currently set to 1500 --- the wrong setting can cause all sorts of really weird issues, such as attachments not being able to be sent/received etc.

MTU problems may result in degraded network service, but may not affect some users' abilities to access the required applications, so sometimes MTU problems go unreported. Other times, MTU problems cause severe lags in network logon times, cause email attachments and other functions within Outlook to fail, and cause applications to stop functioning entirely. Note that, by default, the MTU on Windows operating systems is 1500 (Ethernet) and that a change to 1492 may resolve some, but not all, problems. I'm not sure what it is in Ubuntu (or how to check, but I'll google it and post what I find).

**The MTU must be set to the same setting on all your PC NICs and router.**

-Dave

---

### Post by FDupont on 2005-10-25
Maybe you could try upgrading your Router's firmware. 

Fred Dupont

---

### Post by PoK on 2005-10-25
Hi,

One more thing to mention: I have no problems under Windows...

- I tried with the original firmware version, and currently with the latest (official) as well.
- I did the router reset earlier.
- I use DHCP, but I also tried using fix IP.
- My /etc/resolv.conf includes the ISP DNS servers.


ifconfig (no router):

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:95:95:9B  
          inet6 addr: fe80::20c:6eff:fe95:959b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:378513 (369.6 KiB)  TX bytes:68754 (67.1 KiB)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126105 (123.1 KiB)  TX bytes:126105 (123.1 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:81.183.157.232  P-t-P:145.236.238.185  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:367099 (358.4 KiB)  TX bytes:51855 (50.6 KiB)


and ifconfig (using Linksys router):

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:95:95:9B  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe95:959b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16603 (16.2 KiB)  TX bytes:13676 (13.3 KiB)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123949 (121.0 KiB)  TX bytes:123949 (121.0 KiB)

Regards,
PoK

---

### Post by dbott67 on 2005-10-25
I notice that the MTU for eth0 is 1500.  Check to make sure that your Linksys Router also has MTU=1500.

You might also want to comment out your ISP's nameserver from /etc/resolv.conf and add one that says:
```
nameserver 192.168.1.1 (or whatever the IP of your router is)
```

-Dave

---

### Post by PoK on 2005-10-25
Hi,

I already tried to use my router ip in /etc/resolv.conf without success..

There is no option for MTU in the router, or I could not find it out where..

How can I change my eth0 interface instead, to use 1492 MTU.

Regards,
PoK

---

### Post by dbott67 on 2005-10-25
[FONT=Arial, Helvetica][SIZE=2]From [Linksys Website]("http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=386&p_created=1084210366&p_sid=en45_WSh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTAmcF9wcm9kcz0xLDAmcF9jYXRzPSZwX3B2PTEuMTsyLnUwJnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9zY2ZfbGFuZz0xJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9TVRV&p_li=&p_topview=1"):[/SIZE][/FONT]
> [FONT=Arial, Helvetica][SIZE=2]To find the proper MTU Size, you&#8217;ll have to do a special ping of the destination you&#8217;re trying to go to. A destination could be another computer, or a URL.

[/SIZE][/FONT]   [FONT=Arial, Helvetica][SIZE=2]1. Click on the **Start** button, then select the **Run** option.[/SIZE][/FONT]
  [FONT=Arial, Helvetica][SIZE=2]2. In the &#8220;Open&#8221; field type in **command** (If you&#8217;re using *Windows 2K/NT/XP* use **CMD** instead).[/SIZE][/FONT]
  [FONT=Arial, Helvetica][SIZE=2]3. Once the window opens, you&#8217;ll need to do a special ping.  It should be formatted:

[/SIZE][/FONT]   [FONT=Arial, Helvetica][SIZE=2]**ping** [url] [-f] [-l] [MTU value] **[Enter]** 

an example would be:
**ping** **yahoo.com &#8211;f &#8211;l 1472** <result = fragmented packet>[/SIZE][/FONT]
  [FONT=Arial, Helvetica][SIZE=2]**ping yahoo.com &#8211;f &#8211;l 1462** <result = fragmented packet>[/SIZE][/FONT]
  [FONT=Arial, Helvetica][SIZE=2]**ping yahoo.com &#8211;f &#8211;l 1452** <result = reply>

[/SIZE][/FONT]   [FONT=Arial, Helvetica]You should always start at 1472 and work your way down by 10 each time. Once you get a reply, go up by 2 until you get a fragmented packet. Take that value and add 28 to the value to account for the various TCP/IP headers. For example, lets say that 1452 was the proper value, the actual MTU size would be 1480, which is the optimum for the network we&#8217;re working with.

[/FONT]   [FONT=Arial, Helvetica]4.[SIZE=2] Once you&#8217;ve found the optimum MTU size open up your browser, usually Internet Explorer, which is located on your desktop (Or on the Start menu in Windows XP).[/SIZE][/FONT]
  [FONT=Arial, Helvetica]5.[SIZE=2] Once Internet Explorer has opened input[/SIZE][/FONT] [[FONT=Arial, Helvetica]http://192.168.1.1/Filters.htm[/FONT]]("http://192.168.1.1/Filters.htm") [FONT=Arial, Helvetica]into the &#8220;Address&#8221; bar.[/FONT]
  [FONT=Arial, Helvetica]6.[SIZE=2] You will be prompted for a User Name and Password.  Leave the User Name blank and input **admin** as the password then click **OK**.[/SIZE][/FONT]
  [FONT=Arial, Helvetica]7.[SIZE=2] Once you&#8217;ve done this you should find your self on the Filters tab.  Scroll down to the bottom and look for &#8220;MTU&#8221;.  **Enable** the option and input the optimum value you got earlier.  So for our example this would be **1480**.  After that value has been inputted click **Apply** then **Continue** and you&#8217;re done.

[/SIZE][/FONT]   [FONT=Arial, Helvetica]**NOTE: ** If you don&#8217;t have a &#8220;MTU&#8221; option please goto[/FONT] [[FONT=Arial, Helvetica]http://www.linksys.com/download[/FONT]]("http://www.linksys.com/download") [FONT=Arial, Helvetica]and select the model number of the router you have and the OS you&#8217;re using. Then click on &#8220;Firmware&#8221; and follow the upgrade instructions.[/FONT]
 -Dave

---

### Post by dbott67 on 2005-10-25
[quote=PoK]There is no option for MTU in the router, or I could not find it out where..[/quote]

Points 5, 6 & 7 of my above post should take you to the MTU settings section.

> How can I change my eth0 interface instead, to use 1492 MTU.

From what I've been able to gather so far, you can change the MTU in Linux using the 'ifconfig' command.  Check your man pages for full details, but I think the command would be:
```
sudo ifconfig eth0 mtu 1492
```
-Dave

---

### Post by PoK on 2005-10-26
Hi,

Yesterday I decided to downgrade my 1.50.18 firmware, because anything you told me to do was not working the way it should have been.

Downgrading my firmware was also not successful, but I managed to kill the router in some way. I could ping the router, but I could not reach it on http.:confused: 

Today, after I downloaded a linksys tftp software (for Windows), I was able to upgrade the firmware successfully! This time I used version 1.51.00. Than I tried the router using linux (apt, and surfing the net), and all of a sudden my problems were solved! :D 

I did not set MTU on my router nor my ethernet card!

To summerize things: my problems was simply because of a wrong firmware version.
**Don't forget I used only official versions!!!**
And on [www.linksys.com](www.linksys.com) you can only find the problematic 1.50.18 firmware! Do not use it!

These links will come in handy:
[http://pages.videotron.com/flogator/](http://pages.videotron.com/flogator/)
[ftp://ftp.linksys.com/pub/network/befsx41_Tftp.exe](ftp://ftp.linksys.com/pub/network/befsx41_Tftp.exe)
[http://www.broadbandreports.com/forum/linksys](http://www.broadbandreports.com/forum/linksys)

Thanks you all!
PoK

---

### Post by dbott67 on 2005-10-26
Glad you got it working!

-Dave

---

