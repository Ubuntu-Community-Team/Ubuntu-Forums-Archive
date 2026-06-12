---
title: "Recent update trashed my pc, again!! fsarchver to the rescue?"
date: 2013-03-01
forum: General Help
---

### Post by Dobly on 2013-03-01
You'd think I'd learn by now. Don't do upgrade when Ubuntu 12.10 suggests it. 

After the upgrade yesterday other day I rebooted into a desktop with no launcher, no top nav and no right click menu. Great. 

I googled and found what I thought was a solution worth trying. I don't recall what I did but it involved removing xOrg and reinstalling it or some such thing. On reboot after that I didn't even get the desktop. Just a black screen. 

Luckly for me, this time I was prepared. I had made a backup of my system drive a week ago to a 2nd hard drive on this pc. 

The question is, how do I restore it? 

I'm booted now with the Ubuntu Install disk. It does not have fsarchiver archiver. Furthermore, if I try ... 

sudo apt-get install fsarchiver 

I get a message that says it cannot be found. I'm not off to a good start with this restoration .

Seems I have 2 courses of action here. 

1. Download a rescue disk that can see all the drives and restore the image on hd 2 to the system drive. 
2. Or more simply run fsarchiver from the system drive while in this bootable  disk environment. 

Option 2 seens simple, except I don't know 

- where fsarchiver lives on the system drive, 
- IF I'll be able to run it, 
- IF it will be able to see and access both drives
- If I have any hope of restoring my PC to the state it was in just a week ago before the Ubuntu update trashed it. 

Which way should I go about this??

---

### Post by Dobly on 2013-03-03
In the end I did a clean install (again).  Seems my 'backup' wasn't. 

I just don't get what it is with these so called 'updates' that leave my pc unusable. 

What I have observed is that this seem to be something do to with the graphics driver. 

In my case I had the 13.1 Catalyst driver running. It worked great in a whole range of games. I do recall however that to get them working in version 12.10 64bit in the first place, I had to install the 32 bit driver package (or whatever this is) with this command.. 

apt-get -y install ia32-libs

I remember needing to do that in order to get the Catalyst drivers installed. 

I'm just wondering if something in this recent 'update' might have upset that setup. Would be nice to know so I can look out for it in future updates. 

This time I am giving 12.04 LTS a go.

---

