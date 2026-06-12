---
title: "Ubuntu as NTP server on isolated network unable to change NTP server"
date: 2022-08-25
forum: General Help
---

### Post by mikefletcher85 on 2022-08-25
I have an isolated network where I have some IP cameras on it. I also have an Ubuntu (21.04 LTS)computer on the network as well. Because there is no internet access on this network the cameras all have different times and likes to drift. The problem is that the cameras have a limited list of hard coded NTP server and I cannot specify my own server. The default on the cameras is currently pool.ntp.org. My thought was to tell the cameras to use the Ubuntu computer as a DNS server and hijack/redirect the requests to pool.ntp.org to the NTP server running on Ubuntu. 

I do have the NTP server running now on Ubuntu, I also installed bind9 but I got lost in the documents. Maybe there is an easier way? Or maybe someone can help me with setting up the DNS server? There is nothing else on this network and the camera's definatly dont need DNS/internet for any other reason.

---

### Post by TheFu on 2022-08-25
> **mikefletcher85 said:**
> I have an isolated network where I have some IP cameras on it. I also have an Ubuntu (21.04 LTS)computer on the network as well. Because there is no internet access on this network the cameras all have different times and likes to drift. The problem is that the cameras have a limited list of hard coded NTP server and I cannot specify my own server. The default on the cameras is currently pool.ntp.org. My thought was to tell the cameras to use the Ubuntu computer as a DNS server and hijack/redirect the requests to pool.ntp.org to the NTP server running on Ubuntu. 

I do have the NTP server running now on Ubuntu, I also installed bind9 but I got lost in the documents. Maybe there is an easier way? Or maybe someone can help me with setting up the DNS server? There is nothing else on this network and the camera's definatly dont need DNS/internet for any other reason.

21.04 is not an LTS. Support for that release ended Jan 2022. A new "server" install today should be either 20.04 or 22.04. Your choice. If a DE/GUI is included, know that most 20.04 DE Ubuntu distros will end support next April. They only have 3 yrs of support in their "LTS".  The non-GUI "Server" and default, Gnome3 DE in "Ubuntu Desktop" get 5 yrs.  The release notes for each DE flavor have the details on their support periods.  LTS != 5 yrs of support for most users.

BIND is the enterprise DNS server. There are others, which are much easier.  DNSMasq can be used as a light DNS. [https://www.howtoforge.com/how-to-setup-local-dns-server-using-dnsmasq-on-ubuntu-20-04/](https://www.howtoforge.com/how-to-setup-local-dns-server-using-dnsmasq-on-ubuntu-20-04/) Many home routers have a DNS feature too.  My router includes NTP information in the DHCP lease information.

BTW, NTP is being replaced [https://www.phoronix.com/news/Fedora-Down-With-NTP-SCP](https://www.phoronix.com/news/Fedora-Down-With-NTP-SCP) by a newer protocol, but it is likely that your cameras cannot support the newer, more secure, protocol.  I use chrony client/server for my home network - since 1995, MS-Windows can't keep time.  I was seeing 15 minutes of drift daily, before I started running my own NTPd on the LAN here.  Oddly, the exact same hardware running Linux didn't have any issues keeping accurate time to the sub-msec level.  I decided that 1 system ould run the chrony server and get time for the LAN and that all other systems would get their time from it.  My time server is that formerly-MS-Windows system that couldn't keep time.

---

### Post by mikefletcher85 on 2022-08-25
Sorry, I meant to say I had 22.04 LTS.

I ended up fiddling with bind9 a bit more an eventually got the cameras to sync with the server. Not sure what I had wrong but its working now. I couldnt use the setting in my router because its not accessible from that network, I knew it had to be possible with Ubuntu but I had never had to set up my own DNS server before so it was a bit of a learning curve.

---

### Post by TheFu on 2022-08-26
I last used BIND around 2002 and was hacked through it due to being a mount behind on patches and having DNS available to the internet when that wasn't necessary.  Be very careful.

They got in with the named userid and only had limited access to files that that was a daemon account. They could only write to files in /tmp/  and created a deep, hiding set of directories and used that foothold to gain access to other accounts. Gaining access to other accounts didn't work and 1 of the methods they used generated thousands of alerts which I saw a few hours later - it was a Saturday morning.  I unplugged the system from the internet and proceeded to delve into what they'd done.  Thankfully, I had an off-line backup and was able to compare all files on the system to what my backups created a week earlier contained.  I didn't have backup religion at the time, so it was dumb luck. I created a list of new, deleted and changed files quickly and saw exactly what they were doing.  Killed all their processes, took down named processes (BIND) and removed the files they'd loaded.
When setting up BIND, there are a few best practices, like for any internet-facing versions, make that a read-only client of the master BIND instance that is well protected, behind multiple firewalls.  [https://kb.isc.org/docs/bind-best-practices-authoritative](https://kb.isc.org/docs/bind-best-practices-authoritative) Take those recommendations from the BIND team serious.

---

