---
title: "KUBUNTU 7.10 Running very slow on one computer"
date: 2008-03-30
forum: General Help
---

### Post by The_Hellhound on 2008-03-30
For some reason one of my three computers using Kubuntu 7.10 is running very very slow.  The computer boots normally and at first it runs normally (when i type in konsole my commands appear immediatly, when I click on a menu it opens almost immediately and when I move my mouse it moves)  however after about a minute or two it slows to a crawl (mouse movement is delayed by up to 30 seconds, typing in konsole there is a delay of about 10 seconds before a typed command displays and clicking on a menu takes up to 2-4 minutes).  Below are my computer specs, xorg, and ps aux output.  Can someone please help?

Computer:
Used only as a Samba File Server (no compiz or other unnecessary programs are installed)
Motherboard= Intel Server Board SHG2
Processor= Intel Xeon 2Ghz 512kb cache (I only have one processor as I do not think its usage demands dual processors)
Video Card= Built into motherboard ATI Rage XL
Ram= 1 GB (and Swap size=1 GB)
Harddrives= Three SATA Maxtor Digital WD3200JD 300GB 
RAID Controller= LSI Logic MegaRaid SATA 150-4

/etc/X11/xorg.conf:
[http://paste.ubuntu-nl.org/61569]("http://paste.ubuntu-nl.org/61569")

ps aux:
[http://paste.ubuntu-nl.org/61564]("http://paste.ubuntu-nl.org/61564")

/etc/samba/smb.conf (in case it helps):
[http://paste.ubuntu-nl.org/61570]("http://paste.ubuntu-nl.org/61570")

---

### Post by The_Hellhound on 2008-04-04
Does anyone have any suggestions?  The slowness is driving me nuts.

---

### Post by eriqjaffe on 2008-04-04
You could always try running a lighter-weight DE or WM instead of KDE.  Something like Openbox, Fluxbox, IceWM, etc.

Or not run a GUI at all, especially if it's just a file server.

---

### Post by The_Hellhound on 2008-04-09
I would like to keep my same distribution of linux.  Does anyone have any other suggestions?  I am still having this same issue.

---

### Post by danwood76 on 2008-04-09
When it starts running slow check which programs are eating your CPU time.

you can use the top command in the terminal, or what ever KDE uses as a system monitor.

Post your top when it goes slow:
```

top

```

KDE is a very resource hungry desktop environment and its quite buggy.
As already said switching to a smaller footprint desktop environment will help you no end.

---

### Post by The_Hellhound on 2008-04-13
The link I gave on my original post with ps aux results is about the same as my top results.  I am sorry but because top refreshes every so seconds and the computer is running so slow I am not able to select and copy the top results fast enough.    Please keep in mind that this system ran Suse 10.2 running KDE just fine.  I changed to Kubuntu because I liked it better.  It should also be noted that  with Kubuntu this system is almost always running slow, but after about 10 minutes of working on it it will run normally for about 10 - 30 seconds.  It is the speed that I notice in these 10 - 30 seconds that I would like to see the majority of the time and was the same speed I had with Suse.

---

