---
title: "Sandisk Sansa e200 series in Edgy"
date: 2007-04-11
forum: General Help
---

### Post by kenaparsons on 2007-04-11
Just purchased a Sandisk sansa e270R mp3 player (after returning the other small mp3 player this is based off of) and was having problems transferring mp3's to the player. It was due to permissions issues even though I was root and allowed permissions on this end to the player (and via 'chmod 777 /media/sansa' it showed up as being able to write to the player. Also, I was getting dumped while attempting so I had to remount each time after an attempted transfer. Checked fdisk for partition issues, /etc/mtab, /etc/fstab, all the suggestions I've been reading in the history of this forum and others. But no one mentioned this:

Update the firmware - [http://www.sandisk.com/Retail/Default.aspx?CatID=1449](http://www.sandisk.com/Retail/Default.aspx?CatID=1449)

Just follow the instructions for the manual update. It worked in Ubuntu Edgy for me, and now I'm able to access the Sansa as many are saying they could out-of-box....Just thought I'd share this in case anyone was banging their heads against things trying to figure it out.

---

