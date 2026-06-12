---
title: "Automatic Backups Seagate Personal Cloud on Ubuntu 16.04"
date: 2016-09-14
forum: General Help
---

### Post by annafur on 2016-09-14
I bought a Seagate Personal Cloud hard drive mainly to save backups and transfer files between laptops. I was told the software was supported on Ubuntu. Unfortunately, this is not the case. Today I got the following message from Seagate :
'Unfortunately the Seagate Dashboard backup software is not supported on the Ubuntu operating system. You may be able to find a 3rd party software for Ubuntu that would allow you to run backups. As long as whatever software you choose can back up to a network device you are welcome to use it. '

Do you have any suggestion?? Thank you.

---

### Post by TheFu on 2016-09-14
Last week, it was discovered that seagate cloud software had been hacked and over 100,000 devices were being used in a botnet.
[http://www.slashgear.com/seagate-nas-drives-can-be-hacked-through-simple-telnet-hole-08402370/](http://www.slashgear.com/seagate-nas-drives-can-be-hacked-through-simple-telnet-hole-08402370/) There are others.

In short, if you care about security, don't use consumer devices thinking they will automatically provide security. They do not. If you don't connect to a seagate online account and don't put the device on the interent, it should be fine.  Would be smart to setup firewall rules in your router to PREVENT the seagate device from **any** internet access at all. Don't want it phoning home to get fresh instructions from the botnet guys.

How to use these depends on the actual protocol(s) they support.  If they support NFS, that would be my first choice, then rsync, then CIFS - in that order.  Next you need to pick backup software that is compatible with the protocol(s) available and the file system type used.  If the file systems are Unix/Linux-based, then you'll have more choices for backup software.  

If you provide a link to the detailed specs for the device, we might be able to make better suggestions.

[https://www.hackread.com/trojan-turns-linux-devices-into-botnet/](https://www.hackread.com/trojan-turns-linux-devices-into-botnet/)
[https://www.hackread.com/bitcoin-mining-malware-infects-seagate-central/](https://www.hackread.com/bitcoin-mining-malware-infects-seagate-central/)
[http://www.scmagazine.com/linux-botnet-observed-launching-powerful-ddos-attacks/article/441750/](http://www.scmagazine.com/linux-botnet-observed-launching-powerful-ddos-attacks/article/441750/)

I don't buy consumer stuff (including HDDs) from Seagate anymore.
Why not? [https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/](https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/)

---

### Post by annafur on 2016-09-14
Thank you very much for your useful information. I'm thinking of taking it back to the shop and ask for a refund.

---

### Post by TheFu on 2016-09-14
> **annafur said:**
> Thank you very much for your useful information. I'm thinking of taking it back to the shop and ask for a refund.

If the purpose is just to have a network backup device, I don't know that anything in the same price range can compete.  Just don't let it connect to the internet, ever.  That applies to anything from d-link, netgear, linksys, cisco, tp-link, .... basically, don't expect local cloud storage to be any more secure than remote cloud storage.

"Automatic" is easy for Linux systems. Just use **cron**.

Backups are easy for Linux systems.  There are 50+ different backup solutions. If you stay away from the GUI versions, then running those from cron is trivial. I use **rdiff-backup**, but have used back-in-time, rbackup, rsnapshot and a few others over the years.  My backup storage is Linux (

I never expect anything purchased to "just work" with Linux. Even when they claim to work, I've been burned with HW purchases (their idea of "support" was for a kernel 3+ yrs old). We tend to build our own. 

For many people, this command will be sufficient for a trivial, 1-copy, network backup:
```

$ rsync -avz /etc $HOME {$SERVER_LOGIN}@${SERVER_IP}:/Backup/
```

Run that daily, weekly, and you'll have a mirror of the system settings and stuff in your HOME.  There are optimizations, like excluding cache files from email and browsers.  Creating a list of packages installed on the system. Backing up web sites and databases, but most end users don't think about those things.

---

