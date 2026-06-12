---
title: "Internet not working"
date: 2008-01-27
forum: General Help
---

### Post by philip_bretton on 2008-01-27
Hi

I am a relative Linux newbie so you might need to be gentle with me.

Have been running Ubuntu now for 3 months no problems but this morning I was importing a post script file into Scribus and had Firefox browsing a website at the same time and Pidgin open. Scribus started to hog system resources to the point that nothing else would work and I eventually had to perform a hard reset of the system. When I booted up again I could not access the internet through Firefox or Pidgin.

I have tried other browsers (Amaya and Galeon) and none of them work either. I tried reinstalling Firefox, that did not work, uninstalled it and reinstalled it and that did not work.

The remote pages download but as soon as it gets to the end of the download the application crashes and closes. Pidgin just tries to connect and fails continually.

I have tried browsing local pages and these work fine but as soon as I try a remote page the same thing happens - the status shows me that it is connecting, connected, downloading then crash Firefox shuts down.

FTP works fine as does Synaptics package manager.

Please help!!

Thanks

Brett

---

### Post by seventhc on 2008-01-27
Can you try this and post the output please.
open a terminal and try both of these seperatly.
```
ping yahoo.com
ping 66.94.234.13
```

---

### Post by philip_bretton on 2008-01-27
brett@brett-laptop:~$ ping yahoo.com
ping: unknown host yahoo.com
brett@brett-laptop:~$ ping 66.94.234.13
PING 66.94.234.13 (66.94.234.13) 56(84) bytes of data.
64 bytes from 66.94.234.13: icmp_seq=1 ttl=52 time=339 ms

---

### Post by seventhc on 2008-01-27
OK, it looks as if you can't ping by name but you can by IP. I would check your settings. If you have a router check that too, basically this looks like a DNS issue, check that it's set to DHCP.
If you were to put 66.94.234.13 into your browser address bar you will get yahoo, but you aren't resolving domain names, which is why you can't ping yahoo.com

Are you connecting through wireless or wired?
In case your not sure where you network settings might be go to
System>Administration>Network
then highlight the connection you are using and click properties. From there you can check your settings, If it's from within you router, well since I don't know what you have I don't know the menu . ;)

---

### Post by philip_bretton on 2008-01-27
The DHCP server on the router is definitely working because there are 10 other (Windows) machines in the room working fine.

My laptop is definitely having problems with the DHCP though because it is having problems logging onto the network when I reboot it - if I boot in Windows XP (Dual boot) then I have no problems getting onto the network or navigating to any site.

Also it seems strange to me that Firefox (and the other borksers) all crash when they try to access pages - its not like they come back with an error page or anything (which I could understand) but to crash out seems a little extreme.

---

### Post by philip_bretton on 2008-01-27
I just checked the system log when it tries to create a connection and it gets the following messages:
state is now 1 (starting) for interface eth1 
Jan 27 19:49:06 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jan 27 19:49:09 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jan 27 19:49:13 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jan 27 19:49:14 brett-laptop kernel: [ 2348.696000] eth1: no IPv6 routers present
Jan 27 19:49:18 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jan 27 19:49:23 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 27 19:49:30 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 27 19:49:37 brett-laptop dhclient: No DHCPOFFERS received.
Jan 27 19:49:37 brett-laptop dhclient: Trying recorded lease 192.168.254.8

But then sometimes it will get past this and connect but then when I try to browse the browser will crash.

---

### Post by seventhc on 2008-01-27
Sorry, I've been gone for a while, just got back. Can I ask what was the script that you were importing?

So this is a networked computer, and all work but this 1 machine..correct?
And how are the network settings set up in your computer? Are the others on DHCP or are they hard coded?

---

### Post by philip_bretton on 2008-01-28
Everything is DHCP - nothing is hard coded.

Also I tried the ping test again and I can ping both yahoo.com and its IP address successfully (sometimes) but even when I can ping yahoo.com the browser still crashes when it tries to read a remote page.

The network settings all appear to be correct. 

Am going to try with a static IP and see if that changes anything.

---

### Post by philip_bretton on 2008-01-30
Finally got Firefox working again by reinstalling Ubuntu - had to move my home folder to a new partition as well so that was a real learning curve. 

Takes 3 days to download the updates here in Ghana so its been a long project now the only problem is that the wireless adapter refuses to connect but I'll open a seperate thread for that one.

---

