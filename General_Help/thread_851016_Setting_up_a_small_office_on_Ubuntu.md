---
title: "Setting up a small office on Ubuntu"
date: 2008-07-06
forum: General Help
---

### Post by dvfreelancer on 2008-07-06
All those years I spent working in a Windows shop, ragging at them about how much better Ubuntu was and how I used it at home...blah, blah, blah (usual Ubuntu fanboy na-na).  Well, looks like karma has come home to roost.  I've got a chance to put my money where my mouth is.  

I've taken over technical management of a small start up and have an opportunity to build a Ubuntu-based office from the ground up.  The company has gotten their start relying on outsource providers for most of their applications, so I have some time to put together an office network and development platform.  I'm trying to make the office network client OS agnostic, staff already are using a mix of Mac and Windows.  

It suddenly dawned on me I'm out of my depth, I'm a developer more than a network admin.  But lack of ability never stopped me before and I'd still like to at least try to put our network and office framework together on a Ubuntu based core system.  That doesn't mean there won't be a steeking Windows box on there at some point, but I've been saying since last year you could run an office or enterprise on Ubuntu.  Now I have a chance to prove it.  

I've got a small equipment budget to get started.  I built all my home PC's from parts and some of these boxes have never seen anything but Ubuntu, so I'm confident of being able to build my own workstation.  But I'm wondering about setting up a small office server.  Just basic network services at first, but one of my first big projects will be the company portal (I'm looking at SSL-Explorer: Enterprise Edition). Any suggestions would be greatly appreciated.  

I'm wondering if I can use the server as a workstation for a while and then convert it to the office server and build another workstation, or if it's better not to mix them?  Just get the parts and build a small headless server and run it through the web admin?  

Am I missing any turn-key small office servers that are Ubuntu-based?  

Any guides for setting up a small office on Ubuntu?  

Advice?  Questions?  Suggestions?  Mockery?

---

### Post by txcrackers on 2008-07-06
Complex questions are never easy to answer, but at least you've got the right idea - approach cautiously.

First thing: you don't *necessarily* need to buy the SSL explorer software, if you feel comfortable with managing and configuring packages. The services like firewall, VPN, etc. can all be provided with F/OSS equivalents. If you want professional support, then by all means spend the money.

Secondly: just sit down and make a list of what exactly you want/need to furnish on the network. Each and every single item. Then prioritize them (start with the most non-critical first, like print serving). Then start "googling" for those functionalities. Example:
```
linux windows print server
```

As for headless vs. GUI - if the box isn't going to be over-burdened trying to do both, then there's no reason why you couldn't. Most "servers" are setup without a GUI because there's no reason for it, it does save a bit of memory space, and it doesn't use quite as much CPU cycles. I'll almost bet that your server needs are small enough that having the UI installed and running won't even be noticeable to your users. (In fact, you can start with a workstation installation and just add server programs/remove UI programs until you've got a mix that you like). **Avoid eye-candy!** Compiz is pretty but provides no real functionality on a server - and the graphics cards to run accelerated video cost more.

---

### Post by dvfreelancer on 2008-07-06
Thanks, Ed.  The development side I can manage.  Been there, done that.  But the networking and admin side...not as much experience.  

The rough priorities:

[LIST]
[*]File and print sharing
[*]Firewall
[*]VPN
[*]Company portal (single sign on)
[*]Company wiki
[*]Instant Messaging
[*]Automatic backups to a network appliance and off-site mirror
[/LIST]

Email and shared calendars I'm happy to leave to Gmail for the meantime, likely indefinitely.  

So, yes, given the load right now I should be able to run this all on a single box, at least until the end of summer.  But the more I look at it...two boxes.  My budget isn't that small.  I'm already stretching the $$$ keeping software costs under control (na-na MS).  :)

---

### Post by cariboo on 2008-07-06
It might be an idea to start a new thread in the server forum, as there are some really helpful people that only post in the server forum.

Jim

---

### Post by barratt_sab on 2008-08-05
I’m not sure if you’re still working on the project, but I thought I’d share some of my experiences doing something similar.

Over the last 5 years I’ve managed a system for a small company on a tight budget with similar priorities.  Our storage requirements are relatively light (office documents, rather than music, graphics, video or CAD etc).  I’m not a network admin (or anything similar) but we needed a system and I volunteered… so please take all this in the spirit it’s intended!

**Clients**:	mixed Windows XP, Vista, Linux (Ubuntu, Suse)
 	        and Mac

**Hardware**:	HP LH4 with four processors and 4G of RAM
                Secondhand from ebay

**Drives**:         2 x 9G SCSI in Raid mirror for operating system
                5 x 18G SCSI in Raid 5 array for data
                2 x 9G and 2 x 18G hotswap spares
                Secondhand from ebay

**O/S**:	        OpenSuse 10.0
                (I’d rather have used Ubuntu but it didn’t
                 support the HP raid card out of the box, and I
                 didn’t (don’t) have the skill or time to get it
                 to work)

**File Sharing**:	[Samba]("http://us6.samba.org/samba/"), fairly standard install

**Printing**:	[Samba]("http://us6.samba.org/samba/"), including a [URL="http://www.planetpdf.com/mainpage.asp?webpageid=1736"]pdf-maker
[/URL]
**Firewall**:	left to a hardware device (Netgear [FVS318]("http://www.netgear.com/Products/VPNandSSL/WiredVPNFirewallRouters/FVS318.aspx"))

**VPN**:	        5 sites linked full-time,
                left to hardware devices
                (Netgear FVS318 and SafeCom [SWAMRU-54108]("http://safecom.cn/code/sub/category.asp?prdid=24&subcatid=1") – the
                  Safecom boxes are really cheap but work very
                  well)

**Portal**:	        used to be [foldershare]("https://www.foldershare.com") running on one of the
                Windows clients, but Microsoft “improved” it
                after they purchased the company, so now it
                won’t share network mounts.  Currently looking
                at [SSL-Explorer]("http://en.wikipedia.org/wiki/SSL-Explorer:_Community_Edition") as an alternative

**Wiki**:	        Not yet!

**Instant Messaging**:  [Skype]("http://skype.com/intl/en-gb/") – really easy to set up, reliable,
                multiple clients, free and secure

**Network Appliance**:  a redundant 266Mhz Pentium box, with two
                320G SATA drives on a new network controller
                card, running [FreeNAS]("http://www.freenas.org/") off a CD,
                exporting a software Raid mirror of the SATA
                drives as NFS

**Backups**:	a cron script on the LH4 mounts the FreeNAS NFS
                export every hour and performs an incremental
                snapshot backup using [Mike Rubel]("http://www.mikerubel.org/")’s spectacular
                [script]("http://www.mikerubel.org/computers/rsync_snapshots/"); we keep 4 x hourly, 5 x daily and
                8 x weekly snapshots

**Offsite Service**:  [rsync.net]("http://www.rsync.net/") – a great organization

**Offsite Backups**:  a cron script on the LH4 [fusermounts]("http://www.rsync.net/resources/howto/linux_sshfs.html") the
                Rsync.net account every night and uses [duplicity]("http://duplicity.nongnu.org/")
                (as [recommended]("http://rsync.net/products/encrypted.html") by rsync.net)
                to perform an incremental backup; once a week a
                completely clean duplicity backup set is made.

So - not the fastest, cleanest, tidiest, newest, shiniest or most elegant setup in the world, but we can't have spent more than USD 1,500 on all the networking put together!

---

