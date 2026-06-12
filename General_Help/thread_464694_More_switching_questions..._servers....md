---
title: "More switching questions... servers..."
date: 2007-06-04
forum: General Help
---

### Post by cprofitt on 2007-06-04
As some of you have seen I am preparing to switch away from Microsoft...

I currently run some of their servers and want to switch to Apache (or some other web server) and a file server.

The file server will be internal network only (for family use) and the web server is my sandbox.

I need to learn the following about Apache:

1)  How to install and configure
2)  How to secure it from potential hacks
3)  How to build/publish sites to it
4)  ... anything else I may not know but should that you can think of.

I need to learn the following about file servers:

1)  What are my options
2)  Are their file systems that allow me to have ACLs like in Netware or NTFS
3)  Is there a way to have users logon and get a mount point in a logon script
4)  What, if any, security steps should I take
5)  ... anything else I may not know but should that you can think of.

I am more than happy to get pointed in a direction and read, read, read.

I am hoping to make the switch in 30-45 days and will be doing the research between now and then.

Thanks

---

### Post by simonn on 2007-06-05
Google:

Apache howto

The configuration files are pretty much the same for any OS Apache is on.

An alternative http server is lighttpd.

With file sharing, what are you sharing with? If you are sharing with windows PCs you really need to use Samba to do it. If you are sharing with other unix boxen (including Mac OS X)  then NFS is another option (even Apple Talk would be an option).

Samba is possibly the most widely compatible (except using FTP), so google:

Samba Howto

---

### Post by cprofitt on 2007-06-05
Are thee no specific files on how to do those things using Ubuntu?

---

### Post by phantomdata on 2007-06-20
Actually, getting a LAMP server setup w/ Ubuntu is crazy simple.  There's an option at install time (it prompts you) to set one up (You know, Apache, mySql and PHP).

As to file servers, you'll be looking at samba ([http://samba.org](http://samba.org)) for that.  The how-tos on their site are extremely useful and have served me well through the years.  There are most certainly permissions associated both with Samba and the local filesystem that you'll be paying attention to.

As to security?  My biggest suggestion is to lock down the web server as best possible (chroot jail and safe programming practices in PHP are my biggest points here).  Also, look into iptables for firewall support and Snort for and IDS.  I also always change SSH to operate on a non-standard port so that it doesn't get hit by the kiddies.

You may want to just start by picking up a basic Linux Systems Administrator guide.  Sadly, I don't have any recommendations on that note.  Good luck on your journey!

---

