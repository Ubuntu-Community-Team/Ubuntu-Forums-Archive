---
title: "Lubuntu 16.04 as a backup server?"
date: 2017-04-25
forum: General Help
---

### Post by matteoraggi on 2017-04-25
Hi, I would like to use an old notebook as a backup server, connecting to it one or more external usb hard disk and receive the data to backup trough WIFI and or LAN.
The clients sending the data are 2 windows 10 laptops and 2 lubuntu 16.04 laptops.  Which software would you recommend me for this configuration?

---

### Post by TheFu on 2017-04-25
baculua, but don't use wifi. It will take days.  Bacula is non-trivial to setup, but with Windows, there isn't much choice. [https://www.digitalocean.com/community/tutorials/how-to-install-bacula-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-bacula-server-on-ubuntu-14-04)

Also, if your backup storage is USB2, it will be really slow.

If you can, use USB3 or eSATA for the backup storage and GigE networking for the "server."  Wired networking for the clients will make a huge difference too.

If you are willing to backup Linux systems differently, a tool like rdiff-backup can be nice. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) has a good overview and examples.  "Pull" the backups (security reasons), from the clients.

I've never used bacula. We don't keep any data on Windows machines here. All there data is placed onto Unix/Linux storage and backed up directly from those systems.

---

### Post by Tadaen_Sylvermane on 2017-04-25
I know it's not a proper backup tool but I use just plain rsync for my linux laptop over ssh and file history on windows 10 pointed at a samba share on the server. works great.

---

