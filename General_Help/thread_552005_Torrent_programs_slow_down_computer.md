---
title: "Torrent programs slow down computer"
date: 2007-09-15
forum: General Help
---

### Post by DarkDancer on 2007-09-15
**This post could be related to an Ubuntu bug filed at**: to add info... [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok, first of all let me start off by telling you what I have.

AMD Athlon 64 3800+ Orleans 2.4GHz Socket AM2 Processor
EPoX EP-MF4ULTRA-3 AM2 NVIDIA nForce4 Ultra ATX AMD Motherboard
Leadtek PX7600GS TDH GeForce 7600GS 256MB 128-bit GDDR2 PCI Express x16 SLI Supported Video Card
WINTEC AMPO 1GB (2 x 512MB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel

A couple of cd-roms (ok ones a dvd-burner, the other a cd-burner) and a few hard drives. And I am running Feisty.

Pretty much since I have started downloading torrents( a couple of years anyway), I have used Azureus. Some people complain about it saying that it is overblown, but I like it, all the info it provides. A month or so ago an update for azureus came out. I went the the rigamoral of installing it and eventually thought it caused a problem, now, I'm pretty sure it didn't but let me tell you what is happening. 

A few days after the update, my computer started slowing down. Way down, eventually to the point that it was unusable. I could kill the desktop and come back up and all would be fine, I would load azureus and then a few days later, slow down. Welkl, eventually this escalated and at the end, I couldn't bring azureus up at all. In less than a minute the computer would slow way down (to the point that if you moved the mouse, the cursor would sit there for 20 seconds or so then suddenly be on the other side of the screen). I even tried uninstalling and reinstalling azureus, to no avail. 

So I went on a torerent clilent hunt. I tried tribler, which i liked, but it also would cause a slow down (I have uninstalled azureus btw), just not nearly as quickly., I now use bittornado, which also seems like a really good client, but, after a few hours running, majow slow down, time to kill the desktop again. 

A few more details, I do have (and have had for months with no change) Beryl (not fusion, just regular old baryl) and Boinc running. I will happily kill either or both of these if you have suggestions that require that. I'll even reinstall Azureus (I have already, I have thought of some tests to try). Any suggestions?

Edited to add:

Never mind about azureus, it won't continue running. Even if I go back to metacity.

---

### Post by Sayers on 2007-09-16
You know, I think torrents can make the file system a bit unhappy, but I dont know. it's worth trying  : sudo shutdown -rF now 

that will reboot into a file system check, it's worth a try?

---

### Post by DarkDancer on 2007-09-16
I'll give it a try......

---

### Post by DarkDancer on 2007-09-16
Ok, I tried it, it went down and came back up, it didnt't really do a disk check....

---

### Post by Sayers on 2007-09-16
Oh :(  I guess I forgot how then

---

### Post by DarkDancer on 2007-09-16
Ok, a friend sent me the instructions on fsck-ing (hehe that looks dirty without the - ) the drives. I did it and it did find some um, something (sorry, it was like 14 hours ago and I no longer recall) in the /home partition. I will fire up the torrent and see what happens.

oh, and in case you are interested....

> If you really want to do a disk check, reboot into the rescue kernal and then enter these commands:

umount -a
fsck -pv /dev/{drive_name}

---

### Post by DarkDancer on 2007-09-18
Ok, it seems to have worked a bit longer since fixing the drive errors, but today it just slowed down again....anyone have any ideas?

---

