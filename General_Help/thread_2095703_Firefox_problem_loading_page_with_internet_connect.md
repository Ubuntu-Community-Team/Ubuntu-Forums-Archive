---
title: "Firefox problem loading page with internet connection."
date: 2012-12-17
forum: General Help
---

### Post by Heinzelmannchen on 2012-12-17
This problem is very frustrating, everytime i'm the internet it occurs. I have no idea what is causing it and wasn't able find a solution to it here. I'm able to connect to the internet it's just every so often firefox stops working for 2-5 minutes and displays problem loading page error. My laptop says i still have a connection to the internet when this happens so i don't think it's that. Anyone have any ideas on how to fix this or experience something similar? I'm sorry if i was supposed to post info but idk what that would be as i'm still generally new to linux. If so just tell me and i'll edit this.

---

### Post by Pjotr123 on 2012-12-17
- Configure your Firefox right:
[https://sites.google.com/site/easylinuxtipsproject/firefox](https://sites.google.com/site/easylinuxtipsproject/firefox)

- If that doesn't help: what Ubuntu version are you using? And supply an overview of your hardware like this:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

---

### Post by Heinzelmannchen on 2012-12-17
> **Pjotr123 said:**
> - Configure your Firefox right:
[https://sites.google.com/site/easylinuxtipsproject/firefox](https://sites.google.com/site/easylinuxtipsproject/firefox)

- If that doesn't help: what Ubuntu version are you using? And supply an overview of your hardware like this:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

 I feel dumb for not stating i have ubuntu 12.1 

heres my hardware:

 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 07/07/2010
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-scsi
       physical id: 3
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=rts5139

---

### Post by Pjotr123 on 2012-12-18
Please supply the hardware list in the form as described in the web link that I gave you.... This is unusable. :)

Damit wir dieses Problem halbwegs gründlich durchschauen können.

---

### Post by Heinzelmannchen on 2012-12-18
> **Pjotr123 said:**
> Please supply the hardware list in the form as described in the web link that I gave you.... This is unusable. :)

Damit wir dieses Problem halbwegs gründlich durchschauen können. Danke fur deine helfen. Bitte entschuldigung meine Deutsch grammatik, es ist sehr schlecht. ;) Aber es ist spassig zu spricht Deutsch. I think it could possibly be a connection problem because when i was downloading something from the software center it said error no internet connection at the same time firefox had problem loading page error. It's strange though because according to network manager i'm connected the whole time.

---

### Post by Wim Sturkenboom on 2012-12-18
When the problem occurs, the first thing I do is to ping a site like google.com

```

wim@aa0:~$ ping google.com
PING google.com (197.80.128.55) 56(84) bytes of data.
64 bytes from google.com (197.80.128.55): icmp_req=1 ttl=56 time=48.2 ms
64 bytes from google.com (197.80.128.55): icmp_req=2 ttl=56 time=76.6 ms
64 bytes from google.com (197.80.128.55): icmp_req=3 ttl=56 time=75.6 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 48.222/66.837/76.675/13.171 ms

```
If you don't get a reply, it might be a dns issue. You can check that by pinging by ip-address instead of by name (but you need to know the address, so write it down somewhere when the setup works normal).
```

wim@aa0:~$ ping 197.80.128.55
PING 197.80.128.55 (197.80.128.55) 56(84) bytes of data.
64 bytes from 197.80.128.55: icmp_req=1 ttl=56 time=66.5 ms
64 bytes from 197.80.128.55: icmp_req=2 ttl=56 time=70.1 ms
^C
--- 197.80.128.55 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 66.502/68.327/70.153/1.844 ms

```
If you get a reply while you did not get a reply with the earlier command, it's a DNS issue.

What is useful to know is how you connect. 3G directly connected to your computer; cable to a router/modem; wifi to router/modem.
If a router is involved, you can ping that if you know the ip-address (find it when everything works normal); e.g.
```

wim@aa0:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_req=1 ttl=64 time=1.16 ms
64 bytes from 192.168.2.1: icmp_req=2 ttl=64 time=1.37 ms
^C
--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.161/1.268/1.376/0.113 ms

```
If you get a reply, at least that part of the communication path works (between PC and router).

I have a setup with a router and a modem. If I determine that it's a DNS issue, I usually disconnect and reconnect on my router so the connection gets refreshed. If that does not work, I reboot my router and modem (they are on the same power switch). If that does not work, I reboot my PC. And if that does notwork,I call the ISP. There might be better solutions, though.

PS
You need to test all steps when everything works, so you know the expected behavior.

---

### Post by Heinzelmannchen on 2012-12-20
> **Wim Sturkenboom said:**
> When the problem occurs, the first thing I do is to ping a site like google.com

```

wim@aa0:~$ ping google.com
PING google.com (197.80.128.55) 56(84) bytes of data.
64 bytes from google.com (197.80.128.55): icmp_req=1 ttl=56 time=48.2 ms
64 bytes from google.com (197.80.128.55): icmp_req=2 ttl=56 time=76.6 ms
64 bytes from google.com (197.80.128.55): icmp_req=3 ttl=56 time=75.6 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 48.222/66.837/76.675/13.171 ms

```If you don't get a reply, it might be a dns issue. You can check that by pinging by ip-address instead of by name (but you need to know the address, so write it down somewhere when the setup works normal).
```

wim@aa0:~$ ping 197.80.128.55
PING 197.80.128.55 (197.80.128.55) 56(84) bytes of data.
64 bytes from 197.80.128.55: icmp_req=1 ttl=56 time=66.5 ms
64 bytes from 197.80.128.55: icmp_req=2 ttl=56 time=70.1 ms
^C
--- 197.80.128.55 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 66.502/68.327/70.153/1.844 ms

```If you get a reply while you did not get a reply with the earlier command, it's a DNS issue.

What is useful to know is how you connect. 3G directly connected to your computer; cable to a router/modem; wifi to router/modem.
If a router is involved, you can ping that if you know the ip-address (find it when everything works normal); e.g.
```

wim@aa0:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_req=1 ttl=64 time=1.16 ms
64 bytes from 192.168.2.1: icmp_req=2 ttl=64 time=1.37 ms
^C
--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.161/1.268/1.376/0.113 ms

```If you get a reply, at least that part of the communication path works (between PC and router).

I have a setup with a router and a modem. If I determine that it's a DNS issue, I usually disconnect and reconnect on my router so the connection gets refreshed. If that does not work, I reboot my router and modem (they are on the same power switch). If that does not work, I reboot my PC. And if that does notwork,I call the ISP. There might be better solutions, though.

PS
You need to test all steps when everything works, so you know the expected behavior.

Thanks for the response, i didn't get a reply after pinging google.com Then i got one from my ip so i guess it's a DNS problem. Is there a permanent fix besides reconnecting to router, or restarting computer?  I could try calling my isp but it'd be nice if i could better understand what causes the problem. I have my connection set up on a modem and router too. :)

---

### Post by Heinzelmannchen on 2012-12-22
Restarting the router and modem seems to work. This is only a temporary fix though i'd like to find a solution to the problem.  But why is it that i only have this problem on linux? On windows everything works fine.

---

### Post by netgooroo on 2012-12-22
> **Heinzelmannchen said:**
> Restarting the router and modem seems to work. This is only a temporary fix though i'd like to find a solution to the problem.  But why is it that i only have this problem on linux? On windows everything works fine.

I would suggest you do all your updates for your install via update manager or, via the command line. Sudo apt-get upgrade

If after you have made sure that your install is fully updated and, you still have this issue, I would suggest installing Chromium. You can download it in the package manager. 

Hope that helps.

netgooroo

---

### Post by Wim Sturkenboom on 2012-12-22
> **netgooroo said:**
> ..., you still have this issue, I would suggest installing Chromium. 
How will installing chromium fix DNS issues?

---

### Post by lmellen on 2012-12-22
I have the same problem on a dell XPS ubuntu 12.10 64bit. It seems there is a bug in firefox 17.0.1. I found a lot of complaints at the mozilla website, but no real fix. The next version of firefox is due out next month. 
If you want go to synaptic and remove all of firefox, then; again using snaptic; install chromium. Chromium works well. When the next version of firefox is out you can reverse the process and try firefox again. Hope this works for you. -Larry:p

---

### Post by Heinzelmannchen on 2012-12-26
I still encounter the problem when using google chrome. It seems to be happening more often now.

---

### Post by Wim Sturkenboom on 2012-12-27
I'm not familiar with DNS; I just know what it does. One possible reason for your problems is that your ISP's DNS servers are not up to the task. Using other DNS servers like OpenDNS or Google might solve your issue; you need to configure your router as far as I know.

The below link contains the IP addresses for the above mentioned DNS servers; I'm not sure if you need to register for OpenDNS; there is a registration page but I'm not sure if it's required.

[http://forum.gardenroute.com/showthread.php?1507-Suggested-DNS-Servers](http://forum.gardenroute.com/showthread.php?1507-Suggested-DNS-Servers)

Note that others might be able to advise better.

---

### Post by Heinzelmannchen on 2012-12-28
> **Wim Sturkenboom said:**
> I'm not familiar with DNS; I just know what it does. One possible reason for your problems is that your ISP's DNS servers are not up to the task. Using other DNS servers like OpenDNS or Google might solve your issue; you need to configure your router as far as I know.

The below link contains the IP addresses for the above mentioned DNS servers; I'm not sure if you need to register for OpenDNS; there is a registration page but I'm not sure if it's required.

[http://forum.gardenroute.com/showthread.php?1507-Suggested-DNS-Servers](http://forum.gardenroute.com/showthread.php?1507-Suggested-DNS-Servers)

Note that others might be able to advise better. I just enabled OpenDNS so far its working great thanks for the advice ):P Hopefully it stays this way

---

### Post by Wim Sturkenboom on 2012-12-29
Glad to hear it seems to be working; keep an eye on it for a while and if you think that the problem is solved, you can mark the thread as solved using the thread tools just above the first post on this page.

---

### Post by Heinzelmannchen on 2012-12-30
> **Wim Sturkenboom said:**
> Glad to hear it seems to be working; keep an eye on it for a while and if you think that the problem is solved, you can mark the thread as solved using the thread tools just above the first post on this page.
I just got problem loading page on firefox again :-( Does anyone know why this problem only seems to happen on linux? My other laptop with windows works fine all the time.

---

### Post by Calinou on 2012-12-30
> **Heinzelmannchen said:**
> Restarting the router and modem seems to work. This is only a temporary fix though i'd like to find a solution to the problem.  But why is it that i only have this problem on linux? On windows everything works fine.

Try using Ethernet instead of Wi-fi, sometimes Wi-fi is badly supported on Linux. Ethernet is also slightly faster. 8)

---

### Post by Wim Sturkenboom on 2012-12-30
I'm out of options and therefore out of here; sorry.

---

### Post by Heinzelmannchen on 2013-01-06
> **Calinou said:**
> Try using Ethernet instead of Wi-fi, sometimes Wi-fi is badly supported on Linux. Ethernet is also slightly faster. 8) Whats the point in having a laptop if you need to plug it in to a router? Kind of defeats the purpose IMO. I'd like to get this problem fixed but have no idea what is causing it. Being the huge linux noob i am i have no idea what to do so would really appreciate your guys help. Surely there is people that are running linux on their laptops without this obnoxious problem. Anyone? at least point me in the right direction.

---

### Post by Heinzelmannchen on 2013-01-21
I disabled IPV6 set IPV4 to DHCP(addresses only) and added 2 DNS addresses. I did this through edit connections. At first it seemed to have worked i wasnt getting any problem loading page errors. Then it occasionally got worse, i just figured i'd deal with it since i ran out of options.

 Now the problem is just as bad as before every couple minutes i need to reload pages.  In the morning when i logged in no connections showed, so i restarted my laptop and found my connection but it was renamed with a 2 at the end of it. I'm thinking it might have to do with the BCM4313 network chip but I'm not sure, i had problems with connecting because of this before but reinstalled ubuntu and everything works fine(besides this darn problem loading page error.) Can anyone relate or help me figure this out. It is really frustrating...

---

### Post by Heinzelmannchen on 2013-01-22
I seemed to have temporarily disabled the problem by disabling IPV6, setting IPV4 to automatic DHCP address and filling out the BSSID. The problem i'm having now is that it doesn't automatically connect to the Internet connection upon logging in. I have to do all the steps over and enter password. This is a lot better than before but i would still like to get this problem dealt with.

 If anyone feels like helping me (because i know for a fact you guys can help me with this problem) please post back. Like i said i'm a noob so i apologize if i'm missing any info i'd be more than happy to post anything i'm missing.

---

