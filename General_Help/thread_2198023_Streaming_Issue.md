---
title: "Streaming Issue"
date: 2014-01-06
forum: General Help
---

### Post by sayre on 2014-01-06
First off, I really appreciate the help in advance, I am new to Linux and this is my first Linux build. 
   
  Hardware:   Intel i3 processor,  8GB (2x4GB) memory, 1 TB Hard Disk.  
  Router: Belkin AC750
  Raspberry PI:  Model B with OpenELEC XMBC 
  Software:   Ubuntu Server(w/ LAMP, OpenSSH, and Samba), SABnzbd, and SickBeard
   
  I am having trouble streaming what appears to be only large video files (2GB .MKV) from my Ubuntu server to my Raspberry PI running XBMC (openelec). I can stream 1GB .MKV video files no problem. It’s as if someone pauses it, then it plays for 15-30 seconds and pauses over and over. My server setup is wireless (direct view of the router) and the Pi is connected by Ethernet.  Another issue that may be related is when I access the server from OSX VIA the finder and select it from the devices menu it will say connection failed but if I deselect it and reselect it, it opens just fine. Sometimes I have to do this more than once.  If I try to open and play these large videos directly from the finder window it will take 2-3 mins to open and start playing in VLC. 
   
  Here is a screenshot of the system usage so I definitely don’t believe it’s a server resource issue;
   
   
   [ATTACH=CONFIG]249274[/ATTACH]

   
  Any ideas of where to begin on this? Where I can look and what I’m looking for?

---

### Post by Derek_Gentle on 2014-01-06
While I am far from an expert, I do have a similar setup to yours at home, the only difference is that my media is stored on a separate server from the one that run SAB, Sick, Couch&#8230; etc.
 
A couple things&#8230;
 

[LIST=1]
[*]I notice that your router is only 10/100&#8230; while this *shouldn&#8217;t *cause an issue, I would recommend a gigabit connection
[*]Are you able to connect the server to your router with an Ethernet cable?
[*]How does the Pi access the media files (ie: nfs, samba, etc?)
[/LIST]

---

### Post by sayre on 2014-01-06
Thanks for the reply;

1. I will give this a try as a last resort. 
2. That is another issue I am having, I tried to do this how even when connected with ethernet it was still using the wifi. I had found the command to shutoff the wireless connection but it would use the wired connection still.  Any ideas on how to fix that? 
3.) The Pi access it by samba, could that be the issue?

---

### Post by sayre on 2014-01-07
Does anyone know what might cause a drop in data transfer?   I watched my resources on the server while streaming looking at the tx speed and it will be at about 600K - 1500k then a few seconds before it skips it will drop to bytes before going back up to 1k and playing again. This repeats.

---

### Post by SeijiSensei on 2014-01-07
For Linux-to-Linux file sharing, [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is by far the better choice.  You can run both nfs-kernel-server and Samba together on the server if you need to make files available to Windows users.

I recommend adding "async" to the list of server options in /etc/exports:

```
/path/to/share   10.0.0.0/8(rw,async)
```

and expanding the transfer block sizes on the client in /etc/fstab:

```
server:/path/to/share /media/stuff nfs defaults,rsize=32768,wsize=32768 0 0
```

> **sayre said:**
> Does anyone know what might cause a drop in data transfer?   I watched my resources on the server while streaming looking at the tx speed and it will be at about 600K - 1500k then a few seconds before it skips it will drop to bytes before going back up to 1k and playing again. This repeats.

This is the result of buffering, probably on the client.  I use [SMPlayer]("http://smplayer.sourceforge.net/") to watch videos (over NFS), and I've set the program's cache (Options > Preferences > Performance > Cache) to 5 MB so that the player can keep ahead of the stream.  It takes a second or two for the cache to fill at the beginning of the video, then it just rolls along.

---

### Post by sayre on 2014-01-08
> **SeijiSensei said:**
> For Linux-to-Linux file sharing, [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is by far the better choice.  You can run both nfs-kernel-server and Samba together on the server if you need to make files available to Windows users.

I recommend adding "async" to the list of server options in /etc/exports:

```
/path/to/share   10.0.0.0/8(rw,async)
```

and expanding the transfer block sizes on the client in /etc/fstab:

```
server:/path/to/share /media/stuff nfs defaults,rsize=32768,wsize=32768 0 0
```



This is the result of buffering, probably on the client.  I use [SMPlayer]("http://smplayer.sourceforge.net/") to watch videos (over NFS), and I've set the program's cache (Options > Preferences > Performance > Cache) to 5 MB so that the player can keep ahead of the stream.  It takes a second or two for the cache to fill at the beginning of the video, then it just rolls along.

Thank you. So far i've switched to NFS and re setup my sources in XBMC but am still having hiccups in XBMC while watching.  

In regards to:

> and expanding the transfer block sizes on the client in /etc/fstab:

```
server:/path/to/share /media/stuff nfs defaults,rsize=32768,wsize=32768 0 0
```

I don't see the /etc/fstab folder in xbmc. Should I add it?

thanks for your help.

---

### Post by SeijiSensei on 2014-01-09
Where do you mount the NFS shares?  The /etc/fstab file contains mounting information for all the filesystems on the machine.   If you are mounting the remote shares permanently, this is the place to do so.  I've only glanced at XBMC, so maybe there's a method for mounting shares there, but I'd do it all in /etc/fstab. See the section on static mounts in [https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts](https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts).

If you take this path, be sure to add the option "no_root_squash" in the share definition in /etc/exports. 

```
/path/to/share   10.0.0.0/8(rw,async,**no_root_squash**)
```

Attempted mounts by the root user are "squashed" by default for security reasons.

---

### Post by Derek_Gentle on 2014-01-09
> **SeijiSensei said:**
> Where do you mount the NFS shares?  The /etc/fstab file contains mounting information for all the filesystems on the machine.   If you are mounting the remote shares permanently, this is the place to do so. ** I've only glanced at XBMC, so maybe there's a method for mounting shares there**, but I'd do it all in /etc/fstab. See the section on static mounts in [https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts](https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts).

If you take this path, be sure to add the option "no_root_squash" in the share definition in /etc/exports. 

```
/path/to/share   10.0.0.0/8(rw,async,**no_root_squash**)
```

Attempted mounts by the root user are "squashed" by default for security reasons.

There is a method for mounting NFS shares through the XBMC interface, it's done when setting up the media sources.  I've tried this, and have had limited success within this method.  I would also recommend adding a line in the /etc/fstab file, this way you are sure to have the files mounted correctly.

---

