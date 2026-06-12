---
title: "SMB passwords in Dolphin"
date: 2007-10-23
forum: General Help
---

### Post by smotsie on 2007-10-23
OK, here's an annoying problem since Gutsy upgrade. Both Dolphin and Konq allow me to navigate to an smb share using (for example) smb://my.domain.com%5csmotsie.user@server/share. When I use this I get a password dialog with the correct username in, and my password connects me to the share.

HOWEVER, when I click on a folder in that share, I get the password dialog again but with "my.dom...e.user" as the username (which of course does not work!)

This is driving me mad :confused: , Konq in feisty remembered the username correctly and I had got used to the fact that my employer insists on Windows for the server boxes here.

Anyone out there know how to sort this?

---

### Post by smotsie on 2007-10-26
OK, so no answers yet... I followed the financial principle of DYOR (Do Your Own Research) and came across some hints that KDE offers a way to store username and password for Samba shares. So, I went into Kcontrol, Internet & Network, and selected Local Network Browsing. There are only two settings allowed there, Default Username and Default Password. I set the Username to my.domain.com\smotsie.userand added my password and Hey Presto, all network shares now work without any prompting.8-)

This almost completely solves the problem, apart from when I want to connect to a different domain, I will have to change the settings each time, but as that is very rare, I am happy with that constraint. Now to solve my "three different networks" problem!

Smotsie

---

### Post by Dianoga on 2007-10-26
This gave me a partial fix for my problem. I would still prefer that Dolphin could remember username/password as I don't much like having to store them.  Also, I have more than one username that I use to connect to different shares, so that complicates things somewhat.

---

### Post by steve.horsley on 2007-11-07
OK, so I posted a load of rubbish. 
I need more time to figure out exactly when it works and when it doesn't.

Posted a bug report:
[https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/160833](https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/160833)

---

