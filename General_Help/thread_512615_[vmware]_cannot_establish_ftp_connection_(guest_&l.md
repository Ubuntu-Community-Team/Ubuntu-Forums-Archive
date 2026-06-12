---
title: "[vmware] cannot establish ftp connection (guest &lt;-&gt; host)"
date: 2007-07-29
forum: General Help
---

### Post by Jumbalaspi on 2007-07-29
Hi, i've installed VMware server and i set up a Winxp virtual machine on my kubuntu. Everything went fine, xp is working, i've got internet connection, i can surf the web, client pings my host machine and vice-versa but i can't set up a ftp connection. I can connect to my host machine's ftp server (proftpd) from other pcs in my LAN but when i try connecting from my xp client (iexplorer and filezilla) it connects to the server but connection time out before login. Then i tried setting up an ftp server on xp (filezilla server) and i had the same error connecting from my host. I don't know what to do, everything is ok (ping, ip, internet connection, windows firewall disabled...) but it doesn't seem to work... what do you think i should try to do?

Any suggestion will be appreciated!

---

### Post by Jumbalaspi on 2007-07-29
solved.

this is a bug listed on launchpad, it seems to be an issue related to my ethernet card. I switched to vmware player 2.0 (downloaded from [www.vmware.com](www.vmware.com) , not the one from feisty repositories) and now it seems to work

---

