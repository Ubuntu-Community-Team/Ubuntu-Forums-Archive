---
title: "Setting up home server... Help"
date: 2008-02-14
forum: General Help
---

### Post by Sanctus Messor on 2008-02-14
I wanted to know the best way for going about this and a detailed how. I've never set up a server before :confused: 

I want to set up a server that all 3 desktops and 2 laptops will be able to connect to. I need a recommendation. First off with Xbox 360 and 4 computers, I'm one port short on the router. So what should I look into? I need a solution that will accommodate the possibility of a few more computers being added but definitely not more than 8 or 10 in total. 

Ok, so now the reason this is getting posted. I need to know how I would set up a Ubuntu server to be a centralized back up of my homework files and be a music server so I can dump all my CD's there and listen to them from any computer in the house. Its mainly going to be for music and picture files as I have many textures and reference photos for animation and having a hub for my fiance and room mate to be able to grab them without my help would be nice.

Additionally, I like having the interface of the desktop version. I read a few other related topics and they didnt quite answer what I was looking for. 

:?: So what would I need to get with the desktop version to make it mock (or become) a server? What settings should be set with the router (Linksys WRT54g)?


One last and completely unrelated question. I was browsing sourceforge one day and found a program that monitored a webcam feed and only recorded when there was a significant change in pixels on the feed. I need the name of that program or something similar for surveillance :biggrin:

---

### Post by danwood76 on 2008-02-14
You could setup a simple SAMBA file server to host all your files.
Its quite simple to do and there are loads of guides out there explaining this.
You can then setup backup programs on your machines to backup to a point on your network drives.

To add ports to the router simply buy a switch/hub and plug it in, it should work fine and you can increase the number of ports by as many as you like.
So if you bought an 8 port switch you would end up with 12 possible PCs connected to your network all with internet.

With the router set in DHCP mode (default with most routers) you should have no problems setting up and evtra PCs on your network.

---

### Post by notwen on 2008-02-14
What OSes will this 5+ computer network be running, if it's goign to strictly be Linux, I highly recommend NFS, I use this to stream mp3s/videos to my wireless laptops and other wired network PCs.  Otherwise you're somewhat limited to SAMBA.

---

### Post by Sanctus Messor on 2008-02-14
Windows XP (3) Ubuntu Gusty Gibbon (1, mine, dual boot XP), those are the numbers for now anyway.

---

### Post by graphius on 2008-02-15
I have been running two [SME]("http://wiki.contribs.org/Main_Page") servers for a number of years now. They are pretty bullet proof and very simple to run and administer. They run RAID by default so a dead hard drive is no issue.
SME is samba based so no problem with MS, or Linux.
When I started I was a complete noob. Their forums are almost as helpful as ubuntu ;)

---

