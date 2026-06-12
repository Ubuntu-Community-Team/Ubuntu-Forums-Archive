---
title: "Which Xubuntu"
date: 2007-01-31
forum: General Help
---

### Post by farscape on 2007-01-31
I have an old 400Mhz pc with 192Mb of ram sitting on my workbench at work. It has windows 2000 on it now. I use it mainly for light internet browsing(dial-up) and as a jukebox. I stream music from a local in shop file server. It's just a machine I screw around with. I was thinking of removing windows and putting Xubuntu on it. I see that there are 2 downloads.
The Desktop CD and the Alternative CD. I'm not sure what the difference is.

---

### Post by mjm115 on 2007-01-31
Go with the Alternative CD.  It contains alternative installation methods for OEM computers and computers with less than 192MB RAM.

---

### Post by nikhilk on 2007-01-31
The desktop CD has a graphical installer and the alternate CD has a text based installer and hence requires less RAM. In your case I would suggest the alternate CD.

---

### Post by heathenx on 2007-01-31
i just installed xubuntu 6.06.1 on my old p2, 400mhz, w/128mb ram. i used the alternate cd. xubuntu is very responsive on this laptop. it's used mainly for my 4 year old daughter who likes to play with tuxpaint and potato guy. it's a rock solid distro considering my old hardware.

by the way, i chose 6.06.1 because the madwifi drivers for my wg511t netgear card come installed whereas in 6.10 they don't.

---

### Post by farscape on 2007-02-03
> **heathenx said:**
> i just installed xubuntu 6.06.1 on my old p2, 400mhz, w/128mb ram. i used the alternate cd. xubuntu is very responsive on this laptop. it's used mainly for my 4 year old daughter who likes to play with tuxpaint and potato guy. it's a rock solid distro considering my old hardware.

by the way, i chose 6.06.1 because the madwifi drivers for my wg511t netgear card come installed whereas in 6.10 they don't.

I know what you mean. My 5yr old daughter loves the linux kids games.

---

### Post by mcduck on 2007-02-03
> **mjm115 said:**
> Go with the Alternative CD.  It contains alternative installation methods for OEM computers and computers with less than 192MB RAM.

Note that normal home users never ever need the OEM install, no matter what computer you have. It's only meant for preinstalling Ubuntu on computers that will be sold to users, and doesn't provide any extra benefits in normal use, only making the install process more complex as the real user isn't created during install..

But anyway, Desktop-CD wants at least 256MB of RAM to run, so the normal install using Alternate-CD is the way to go.

---

### Post by farscape on 2007-02-17
Well I installed xbuntu on the old 400mhz machine. It went well. Only problem is that it comes with wvdial. It' won't dial out. It see's the modem. It's and older external modem. 
I configure wvdial from the command line per sudo. It doesn't seem to save the config file. It's there but the ph# user name and password are not. I can't edit the config file through a file browser because I don't own it. I don't know how to open it as root. 
Are there any other good distro's that will run on a 400mhz, 196mb ram type machine on dial-up.
If I could get the dialer issue resolved I'd use xbuntu but I easily spent 4hrs screwing around with it last night.

---

### Post by mcduck on 2007-02-17
You can open a file for editing as root with 'sudo nano /path/to/file', and when you are ready press Ctrl-X to exit, nano will ask you if you want to save the file.

---

### Post by farscape on 2007-02-18
> **mcduck said:**
> You can open a file for editing as root with 'sudo nano /path/to/file', and when you are ready press Ctrl-X to exit, nano will ask you if you want to save the file.

Thanks mcduck, that worked perfectly. xbuntu is happily connected through wvdial now. That was a learning experience.

---

