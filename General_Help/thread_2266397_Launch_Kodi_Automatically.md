---
title: "Launch Kodi Automatically"
date: 2015-02-22
forum: General Help
---

### Post by David_Gardner on 2015-02-22
Hi chaps,

Newbie to Linux here.

I have got a mysql database for kodi running on my Synology NAS drive, which also holds all of my movies/media.

In my house I have got a Windows 8 Intel NUC in the lounge, & an Ubuntu (latest release) PC in the bedroom. I have got everything setup and working perfectly together.

The problem I have is trying to launch Kodi on startup. I can get it to launch fine, but it can't access my Movies and TV shows & db. I have to launch Kodi from Terminal using Sudo command to get it to access all my media.

Is there a way round this?

Thanks in advance.

David

---

### Post by TheFu on 2015-02-22
Fix the permissions on the files it needs to access.  I have Kodi running fine - auto login to a minimal session and no sudo needed.  The how-to auto login for kodi I found was exact and just worked.  For network storage, access will depend on the network storage userid and whether the NFS userids line up correctly or not - assuming you use NFS.

---

### Post by David_Gardner on 2015-02-23
Thanks for your response @TheFu. I'll give it a go tonight. Having looked through the wiki page I'm pretty confident that you're right.

---

### Post by TheFu on 2015-02-23
Whatever useid is running kodi just needs read-access to the media directories.  

I've been running xbmc for 3+ yrs. About 2 yrs ago, switched to Plex Server for the back end, but retained XBMC for playback - just added the plexbmc plugin to access and share. Plex is an easy DLNA server for your home - easier than managing the mysql DB for Kodi, IMHO.  Might be worth a look for you.  When I switched to plex - I added the userid running xbmc (now Kodi) to the plex group.
plex userid:
```
$ id
uid=107(plex) gid=114(plex) groups=114(plex)
```

xbmc userid:
```
$ id
uid=1100(xbmc) gid=1100(xbmc) groups=1100(xbmc),24(cdrom),29(audio),30(dip),44(video),46(plugdev),100(users),groups=114(plex)
```

Plus the plex server can be anywhere on your network. No desktop/gui needed at all.

---

### Post by David_Gardner on 2015-02-24
Thanks for your help.

[FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#000000]Problem sorted. It was permissions in .kodi folder - thank you for that.[/COLOR][/FONT]

[FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#000000]Thanks for your advise about Plex too. I used to use plex but wen over the XBMC a couple of years ago. It's been pretty rock solid other than this, and this is down to my lack of Linux knowledge rather than software issue. I'll certainly take a look though if it would be a more suitable option.
[/COLOR][/FONT]

---

