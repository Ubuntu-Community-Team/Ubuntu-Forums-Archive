---
title: "Torrent Issue in Feisty"
date: 2007-06-08
forum: General Help
---

### Post by srunni on 2007-06-08
Hi,

I recently upgraded to Kubuntu Feisty from Kubuntu Dapper. Ever since, I've been having an issue with torrents, where they are running very fast, but will regularly drop to 0 kB/s upload and download for ~10 seconds each time. This has happened with both Azureus and KTorrent, and doesn't happen in Windows XP with Azureus set to exactly the same settings. I have all the basic stuff, like port forwarding, download/upload limiting, etc. set correctly. I spent some time on the Azureus IRC help channel trying to solve the problem, and all I got was this from my kernel log: ```
 Jun 7 18:23:35 kakkarot kernel: [16921.186035] NETDEV WATCHDOG: eth0: transmit timed out
``` This seems to be a Feisty-only issue - does anyone have a possible solution?

Thanks in advance for the help!!

---

### Post by Sockerdrickan on 2007-06-09
[http://transmission.m0k.org/](http://transmission.m0k.org/) ;)

---

### Post by zvacet on 2007-06-09
Transmission is great but missing basic function.From torrent you can not select wich files you want to download and wich not.For example if you find torrent with 100 linux ebooks you can not select on or two.You have to download them all.I think that is one of reasons why transmission is not accepted widely.If developers correct this it will be nice.

---

### Post by Sockerdrickan on 2007-06-09
Actually that is the Only reason why most people don't use it so it isn't very feature-less than other torrent programs :P

---

### Post by kelvin spratt on 2007-06-09
i have absolutely no problems with Ktorrent their was a Java problem with the blue frog in April. And their was a small problem with Ktorrent at the same time but downloading Ktorrent from their web site cured that and to be honest Ktorrent runs very well indeed and that from a ex blue frog user.

---

### Post by srunni on 2007-06-09
The issue is not with the client, it's with Kubuntu. I've done extensive testing in an attempt to find the source of the issue, and it seems to be that Kubuntu is doing something that is causing my router (WRT54G running DD-WRT) to periodically lock up. I'm looking for a solution to the issue in the OS itself, not in the particular client. And if Transmission can't select only some files to download, there's no way I'm using it anyway. KTorrent's lack of features was what motivated me to switch to Azureus in the first place. I used KTorrent on Kubuntu Dapper without any issues, and when I reinstalled with Feisty, I gave Azureus a shot, and now neither of the clients work without my connection dying every few minutes. Also, it might be interesting to know that this only happens when I'm torrenting heavily AND browsing the web.

---

