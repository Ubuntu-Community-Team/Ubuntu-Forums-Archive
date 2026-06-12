---
title: "How to set my adsl"
date: 2006-09-19
forum: General Help
---

### Post by Clifweb on 2006-09-19
I wish to find how to set my adsl connection: Below are the instruction that I got to set it on windows xp 

IP address: 10.0.0.1
Subnet Mask: 255.0.0.0
Default Gateway: 10.0.0.138

Preferred DNS server: 194.158.37.196
Alternate DNS server: 194.158.37.211

2.Select Connect to the network at my workplace
3.Select Virtual Private Connection
4.Company Name field, type ‘maltaNET ADSL’
5.Host name or IP Address, type in ‘10.0.0.138’ 
6.Click on the ‘Properties’ button
7.click on ‘Security’
8.security settings to ‘Advanced (Custom settings)’, and click on the ‘Settings’ 
9. is set to ‘Optional Encryption (connect even if no encryption)’ and that the only allowed protocol is ‘Unencrypted Password (PAP)’
10.ure the type of VPN is PPTP VPN. Click on ‘Settings’. Remove all the check marks from the options available, and click on OK.
11.Username username@maltanet
12.password and connect 
How to enter these setting in ubuntu

---

### Post by stefe on 2006-10-17
Need same help here. M doing a search, but still using LiveCD and cannot configure settings properly.

New to Linux, I only know basic things...

Already did a couple of searches, but am not able to find anything as close as this thread.

Many thanks

---

### Post by stefe on 2006-10-21
try linux.org.mt 

there are the instructions. Am still trying to install pptpconfig.

I can connect to tje server, but as yet cannot surf the Net. Wonder why?

Stefe

---

### Post by Lord Illidan on 2006-10-21
Hi guys, nice to see some more Maltese on this forum.

Try and go to System - Administration - Network Tools and work your way from there. Also, what kind of modem you have? USB modem?

Secondly, I wonder if you can use DHCP, it makes matters easier. Ask maltanet about it.

---

### Post by stefe on 2006-11-10
maltanet are not very helpful... First they say they will not support Linux based systems. Then after three weeks, they email back saying that I could use my modem to connect as an always on system.

In the meantime, managed to access internet using pon.

The reason I could not access my internet was that I needed was to re-reoute all traffic thru the new tunnel:
sudo route ip default

Should you need more help, pm me

Any other maltese / malta guys?

Stephen

---

### Post by arley on 2006-11-10
well if u are able to connect to the server trying pinging an outside internet host, first try with the ip then using the dns name. If the IP works but not the DNS name, try adding the dns into your /etc/resolv.conf

---

### Post by fragos on 2006-11-10
Some DSL venders like AT&T in the US have a modem registration proceed that requires a proprietary Microsoft program.  It may be easier to get things set up if you have a friend with a Windows laptop plug into your modem and run the registration proceedure.  They actualy told me I had to buy Windows to use the Internet -- talk about stupid.

---

### Post by PILGU on 2006-12-21
Hi Guys, this is how I did it, and it works.

Setting up ADSL connection

go to :- system >administration >Networking

select NIC (eth 0) >properties > choose static ip address.

set ip 10.0.0.1, & subnet mask 255.255.255.0
 
selct activate >OK >close.

After that, in a terminal run 
 ```
sudo pppoeconf
```

choose everything “YES”

As for User Name  *username*@maltanet    
& *password.*  your log on password

when finished in terminal run ```
plog
``` and ```
ifconfig ppp0
``` to confirm connection is running.

for a better explenation follow link below, where I got my help.
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Good luck

I'm from Malta too

---

