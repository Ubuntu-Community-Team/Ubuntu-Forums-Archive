---
title: "Trying to setup plex media server on Ubuntu 14 desktop"
date: 2014-12-21
forum: General Help
---

### Post by John_Turi on 2014-12-21
I am trying to set up plex media server on Ubuntu 14 desktop and my media library on one of the drives is not visible in plex media server.  Is there an easy way or an application that I can download to fix the ownership of the folder?
Also, is there an easy way that I can make all my folders accessible in the ubuntu desktop and windows 8.1 computers?

Thank you for all the help,

John Turi

---

### Post by TheFu on 2014-12-21
Not sure I understand.  Plex runs under its own userid. 
```

UID        PID  PPID  C STIME TTY          TIME CMD
plex      1166  1164  0 Dec18 ?        00:12:20 ./Plex Media Server
```

That means for the plex server to have read access to your media files, the files should be readable by the plex userid or the plex groupid. There are many ways to accomplish that - either make the plex userid the owner or the plex groupid the group used or allow anyone (i.e. "other") with read access.  This is needed for any sort of media you'd like plex to share - movies, TV, music, or photos.

You can use the Plex web interface to point the different media types at different locations on your system or network.

From a Windows machine, just use any DLNA client to access the Plex server - then all the media will be available.

If you want to use Windows to manage the media ... that's a more complex question and really deserves a new thread - samba is the short answer, but getting the permissions correct if you don't just allow "other" read access will be harder.

If I didn't cover all you need, ask for more details. Be specific. If you provide exact paths to where the files are stored, then we can provide exact commands that won't be confusing.

If you don't exactly understand UNIX file/directory permissions, then it is time to learn those. These are the CORE of UNIX security and important to understand to keep your system safe on the internet.

---

### Post by John_Turi on 2014-12-21
thank you

---

### Post by John_Turi on 2014-12-21
should I see Plex or a plex group ID when I go to files then click of properties.  Then, select permissions.  Then click on group.  The only choices i have there are adm, cdrom, dip, john, lpadmin, plugdev, sambashare, and sudo.  No plex group or anything like that shows up under the group permissions.  Also,  under setting and user there is no Plex user ID on my system.  Yex plex is installed and the media server is running because I can see the media center on my sidebar and I can see it on my cell phone.  So, my plex media server is running on ubuntu because that is the only place it is installed now.  So, how can I change the permissions for my movies folder to allow for plex when it is not referenced as a groupid?

---

### Post by TheFu on 2014-12-21
Sorry - I don't use/have a GUI to look at files, so don't have any idea what "properties" may or may not display.
There are many different ways for Plex to have read-access to files and directories. I attempted to explain that above.

My plex install created both a plex userid AND a plex groupid. I don't use either of these to allow Plex access to files - I just allow the "other" part of the permissions to have read-only access.  However, this is Linux and it is nothing if not flexible. You can do whatever you like.

I don't have a side-bar, so don't know what you are looking at.  I'd check the process table for anything with "plex" in the name - on my plex box, there are 5 processes, all being run by the plex userid.
```
sudo /etc/init.d/plexmediaserver start
``` - to start
```
sudo /etc/init.d/plexmediaserver stop
``` - to stop

> If you don't exactly understand UNIX file/directory permissions, then it is time to learn those. These are the CORE of UNIX security and important to understand, to keep your system safe on the internet.  This still applies. There are tutors for this.

Did you use a web browser to configure the Plex server, like where the different media files are located?
[http://istar:32400/manage/index.html](http://istar:32400/manage/index.html) is where the interface is on my machine. istar is the name the machine is known by on my network - might be easier if you use the IP address for yours.

---

### Post by John_Turi on 2014-12-22
ok thanks

---

### Post by John_Turi on 2014-12-22
yes I used google chrome to install plex and the ubuntu installer from the plex pas Linux 64 bit download site. It sounds like you are running the server version of ubuntu and I'm running the Destop version.  I may switch over to the server version because I think this is a lot of overhead I don't need.

thanks again

---

