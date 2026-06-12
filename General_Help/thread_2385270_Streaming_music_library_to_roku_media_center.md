---
title: "Streaming music library to roku media center"
date: 2018-02-18
forum: General Help
---

### Post by serapis5 on 2018-02-18
Ubuntu 17.10.  Has anyone had any success getting their music library to a roku stick media center located in another room?  Any help would be appreciated.  Thanks!

---

### Post by Dennis N on 2018-02-18
> **serapis5 said:**
> Ubuntu 17.10.  Has anyone had any success getting their music library to a roku stick media center located in another room?  Any help would be appreciated.  Thanks!
You can use Plex Media Server and Roku's Plex Channel. Have you tried this, or what else have you tried?
[https://www.rokuguide.com/channels/plex](https://www.rokuguide.com/channels/plex)

---

### Post by SeijiSensei on 2018-02-18
I use **minidlna** as my DLNA server.  It appears in Roku Media Player.  You can install minidlna from the repositories.

It's pretty simple to configure.  At a minimum, you only need to designate the directories to serve by editing /etc/minidlna.conf.

I just tested it again and played a song encoded with FLAC.  However it cannot play files with A** subtitles yet, only SRT.  I complained to Roku, and they actually said they'd consider adding that to the player.

---

### Post by serapis5 on 2018-02-19
Hey guys!  Just wanted to say thank you for the advice.  I tried both, but couldn't seem to get minidlna to work.  Plex is up and running but I REALLY appreciate the input.  Thank you for everything!

---

