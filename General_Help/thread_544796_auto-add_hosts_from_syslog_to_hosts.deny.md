---
title: "auto-add hosts from syslog to hosts.deny???"
date: 2007-09-06
forum: General Help
---

### Post by 3rods on 2007-09-06
Can anyone recommend a good way to automatically add repeated, failed login attempts to my FTP to hosts.deny? 

Here is a sample of my syslog:

```
Sep  6 12:30:51 user pure-ftpd: (?@000-063-360.area3.spcsdns.net) [INFO] New connection from 000-063-360.area3.spcsdns.net
Sep  6 12:30:51 user pure-ftpd: (?@000-063-360.area3.spcsdns.net) [WARNING] Authentication failed for user [dick]
Sep  6 12:32:51 user pure-ftpd: (?@000-063-360.area3.spcsdns.net) [INFO] Logout.

```

I have denyhosts installed, but this only seems to work if the attacker tries to brute the ssh first, then I can deny all. Is there anything that works with FTP or other services? 

I'm not worried about eventual DoS because I have physical access to the box. 

I've heard of IPTABLES and I hear it's better to drop the packets to save bandwidth, but I'm not really sure how to automate that either.

Any help would be, well, helpful..:p

---

### Post by PriceChild on 2007-09-06
First off, don't use ftp, its insecure, use sftp instead.

I haven't explicitly checked... but what about fail2ban?

---

### Post by 3rods on 2007-09-06
That might do it. 

What sever do you recommmend for SFTP? Or, do you mean for me to use pureftp, but install/generate an SSL cert?

---

### Post by 3rods on 2007-09-06
I found a great program called ossec that takes care of everything. It seems denyhosts is prone to exploits which are currently not fixed. OSSEC seems to be pretty cool. It's not just active defense, it's does a whole lot more. 

I think the website is OSSEC.net, but I'm sure a quick google will find it.

---

### Post by calraith on 2008-01-25
fail2ban is also good for denying brute force attempts to services other than and including sshd.  It's in the repos.  Just sudo apt-get install fail2ban, salt /etc/fail2ban/jail.conf to taste, and enjoy!

---

