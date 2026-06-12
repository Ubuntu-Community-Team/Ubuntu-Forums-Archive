---
title: "MP3 Music Interruption"
date: 2008-05-09
forum: General Help
---

### Post by vba_djs on 2008-05-09
I'm not sure whether this post should be in this forum or the networking forum.

**Background**
Our home lan is wired, 100 mbps.
All of our music is stored on an Ubuntu server that we access from our Windows (XP and Vista) desktops via Samba.
The server has a 2.8 GHz CPU with 4 GB of ram.
My wife uses Windows Media Player while I use several audio programs.

Since I was installing a larger hard drive on the server, I did a fresh install of 7.10 server, versus the 6.06 server that existed on the old drive.

**Issue**
With 6.06 we didn't have any problems.  Since I put on 7.10, the music streams are dropping at a consistent elapsed time, regardless of the desktop OS or the player being used.
Every 5 minutes the music 'pauses', for approximately 25-30 seconds, and then continues for another 5 minutes, 'pauses', etc.

It appears to me that some process is running on the server.

I commented all of the lines in crontab so nothing in there should be running.

I looked at the user logs and syslog without any success.

**Question**
Does anyone have an idea what other logs and/or config files I should check?  {When I installed the 7.10 I chose Print Server/Samba/OpenSSH/PostgreSQL.  ClamAv is also installed.}

---

