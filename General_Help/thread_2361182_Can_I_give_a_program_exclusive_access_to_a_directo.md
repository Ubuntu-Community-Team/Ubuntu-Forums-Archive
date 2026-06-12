---
title: "Can I give a program exclusive access to a directory for saving a backup?"
date: 2017-05-13
forum: General Help
---

### Post by Robbyx on 2017-05-13
I have been thinking about the problem of ransom ware and wondering if I could protect a specified directory or partition from being encrypted or deleted by rogue software. Is there a ready made solution? 

Assuming there is not an easy solution: Is there a way of stipulating that  only a particular program can access a directory, file or device? I think the udev rules may be of help, but I would need to see some worked examples to be more confident. 

Here are some links i have been looking at:


[https://askubuntu.com/questions/887339/restrict-access-to-all-usb-ports-to-user-account-in-ubuntu-16-04#889958]("https://askubuntu.com/questions/887339/restrict-access-to-all-usb-ports-to-user-account-in-ubuntu-16-04#889958")

[http://manpages.ubuntu.com/manpages/trusty/man7/udev.7.html#contenttoc3]("http://manpages.ubuntu.com/manpages/trusty/man7/udev.7.html#contenttoc3")

Robin

---

### Post by TheFu on 2017-05-13
Dude.  Versioned backups solves the ransomeware issue completely. There are a few tricks.
a) You need a secured backup server that cannot be reached by the internet directly. Best if it isn't on the LAN with other machines that connect to the internet either.  We have a separate LAN just for backups and management (server admin) use.
b) Backups need to be "pulled" by the backup server, not "pushed" from the client machines.  This means the backup server has credentials to access each of the clients.
c) Don't use directly attached or network shared storage for the backup storage.  Clients shouldn't have any write access to the backup storage.  This is very important. After all, backups run as root (or root equiv), so no storage on the machine can be hidden.
d) Versioned backups are necessary.  I like automatic, daily, versioned, backups with rdiff-backup.  For high-risk systems, keep 120 days of backups. For lower risk systems, just 60 days.  The amount of storage needed for this is really quite small - 1.1x - 1.2x the original size, it depends on how much data changes over time and how much cruft is included in the backups.
e) Media files are NOT included in these backups.  Media that doesn't change much, like for a home theatre or media center (Plex Server) only gets a mirror backup.  The OS files on that box get the 60-120 day versioned backups, but not the media directories.  I just don't have the storage to blow on those things.

Simple.  If you want to learn how to do all this, there are some how-tos all over the place.  
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) has a great rdiff-backup page.
Category5.tv - has [LVM snapshot and rdiff-backup videos]("https://www.youtube.com/watch?v=ng2mtVwoRtc") for Ubuntu.  It is pretty dry, but he doesn't skip anything.  Ep# 455, 456, 458, and the rdiff-backup on (sorry, don't know the number).  LVM/snapshots make getting uncorrupted backups pretty easy.

You could also use file permissions to prevent modification of files, but this is a hassle and dangerous. Can't really do it on an installed OS. Plus, root will always be able to do anything. There are usually 10+ privilege escalation bugs in the wild at any time for Linux.

**By far, the best security tool that I know is versioned backups. They solve 1,001 issues.**

Oh ... don't have a backup server?  Get a raspberry pi and some USB storage for it.  It will be slow, but it will work.  A $50 Intel CPU will blow away what a R-pi can do - you can build a backup system for $120-ish using old parts - or just buy a used system (off-lease) for $75 to get the main parts, then consider swapping the CPU+MB for a current generation, fast, setup.

---

### Post by Robbyx on 2017-05-13
Thank you for that full reply. I have read it quickly and it is very useful. I now study your links.  I hope it helps others as well. 

I am unclear how the backup server accesses the main machine if you are not going through the Lan that is also connected to the internet.  Am I to assume that you have 2 network cards in the main machine, one for the backup system and the other for lan / internet.

---

### Post by TheFu on 2017-05-14
There can be more than one LAN in any location. Depending on your network gear, you can have multple LANs either physically or logically.  Physical separation is more secure, but less management hassle for professionals since we can manage the LANs remotely through switch and router controls.

If we step back and bring some common sense to our goal, what do we want?
[LIST=1]
[*]A secured, backup server
[*]That means it cannot be hacked through the network
[*]That means it cannot be on the internet-facing network
[*]Backups must be "pulled" by the backup server, never "Pushed"
[*]Clients cannot 'see' the backup storage, except read-only. It is often best to prevent all client access to the backup storage.
[*]
[/LIST]
With those requirements, how can we accomplish it?
[LIST]
[*]Since we can't use network storage from the clients to backup stuff, we need a client/server backup method. rdiff-backup has that. There are other tools which can do it too.
[*]Since the backup server can't be on the same front-door LAN, but must be networked, we need a "backup LAN/back-door LAN"
[*]The backup server shouldn't connect to the internet (except to be patched), so it isn't an end-user desktop.
[*]
[/LIST]

The total answer is 
* use LVM snapshots
* use a backup tool that supports versioned backups and can be remotely "pulled"
* a secure, encrypted, connection from the backup server to the client(s) is required. The easy answer there is ssh - rdiff-backup uses librsync - which uses ssh encryption and authentication by default. Nothing new to learn.

To clarify. The backup server **can** have NAS storage. It can use directly connected storage, but none of that storage can be available to any other machines.  People tend to put all their storage into a NAS, then make it available all over the place. This is a bad idea.  Limit NAS access through firewall protection.  Definitely never make a NAS available to a router or connect data that you don't want to share with the entire world to the WAN router.  WAN routers should never be completely trusted, especially with storage.

---

### Post by HermanAB on 2017-05-14
Mandatory Access Control is designed to do what you want.  There are two popular examples: SELinux and AppArmor.

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


A simpler way is with Access Control Lists (ACLs): 

[https://help.ubuntu.com/community/FilePermissionsACLs](https://help.ubuntu.com/community/FilePermissionsACLs)

[http://manpages.ubuntu.com/manpages/zesty/man1/setfacl.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/setfacl.1.html)

[http://manpages.ubuntu.com/manpages/zesty/man1/getfacl.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/getfacl.1.html)

---

### Post by TheFu on 2017-05-14
ACLs don't work with all file systems and can be disabled with a **mount -o remount**. Just something of which to be aware.
AppArmor is a good idea too, but if root access is gained on the system, nothing can stop a slightly non-noob attacker from disabling it. I've not heard of any attackers doing so, but ... if we can think of it, then it will happen, eventually.  The remount attack to disable ACLs **is** happening already.

Basically, client machines can't be trusted once an average end-user has control. The level of trust is something each organization must decide for themselves.

---

