---
title: "What are the BEST methods to Remote Ubuntu 12.04 into a Windows XP machine (LAN)?"
date: 2013-10-12
forum: General Help
---

### Post by Jeff_Berrian on 2013-10-12
Ubuntu noob here. I look forward to evolving into an Ubuntu and Linux guru and I thank you in advance for helping me towards that goal today.

My query...

We just setup 8 new Ubuntu 12.04 desktop workstations on our small business LAN. We have a 9th workstation from our previous LAN still running Windows XP Professional SP3 b/c it contains files and applications specific to Windows. We would like our 8 Ubuntu workstations to have the capability to connect remotely into this XP machine. I would say that no more than 3 users would be accessing this machine remotely at any given time (I am assuming Windows XP Pro has a remote user limit?).

Question: What is the best and/or most convenient way to connect to this Windows XP machine with our new Ubuntu 12.04 machines?

Security:

We only want to connect remotely across our Local Area Network and never remotely through the internet/public. What are suggestions to help secure our network when opening up our LAN to remote desktop connection? My concern is that we install and configure remote settings in both Ubuntu and Windows XP that may expose us and leave us venerable to someone connecting from outside our LAN.

Are these valid concerns when setting up remote desktop connections via Ubuntu and Windows XP within our own LAN? If so, what is the best ways to protect/secure our network?

Thank you in advance!!!

PS. I am an Ubuntu noob so any solutions with specific outlined steps to follow is VERY HELPFUL

---

### Post by richardeszes on 2013-10-13
Hi,

TeamViewer ([http://www.teamviewer.com](http://www.teamviewer.com)) is in most cases used to be good. It is usable on the most platform.

---

### Post by Jeff_Berrian on 2013-10-16
Thank you for the tip!   Does teamviewer connect from computer-to-computer or does it connect from computer-to-server-to-computer?  In other words, when you remote connect  to 2 computers within your own LAN, is the session controlled or streamed through teamviewer servers?  Thank you!

---

### Post by The Spectre on 2013-10-16
> **Jeff_Berrian said:**
> Thank you for the tip!   Does teamviewer connect from computer-to-computer or does it connect from computer-to-server-to-computer?  In other words, when you remote connect  to 2 computers within your own LAN, is the session controlled or streamed through teamviewer servers?  Thank you!

TeamViewer works within a LAN just make sure that you enable it in the TeamViewer Options...

[ATTACH=CONFIG]246992[/ATTACH]

---

### Post by mastablasta on 2013-10-16
what kind of access is needed for file and data or also applications?

---

