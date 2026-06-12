---
title: "connect my iRiver to Kubuntu on PS3"
date: 2007-12-16
forum: General Help
---

### Post by anders_ps3 on 2007-12-16
I would like to plug my iRiver ifp 799 player, using USB, to my ps3 running Kubuntu in order to put/get mp3 files. Ideas, anyone?

It doesn't work by connecting it using the software that the ifp799 was delivered with: the Kubuntu/ps3 doesn't react, and I don't find any traces of the player by examining files on my Kubuntu, either. This is expected, since iRiver ships their mp3 players with proprietary formats, or so I heard.

iriver.com offers upgrades so that the ifp799 would appear as a USB memory. Fine, but that appears to be the case when plugging into Windows. I fear that this might be a problem on a Kubuntu/ps3, or would it work?

---

### Post by brianborchers on 2007-12-16
By default, the 795 uses music transfer protocol (MTP) to transfer files to the player.  There's a package called ifp-line that talks MTP.  See 
 
  [http://ifp-driver.sourceforge.net/](http://ifp-driver.sourceforge.net/)
 
I've had good luck with this software.  
 
The other alternative is to flash your player with USB Mass Storage (UMS) firmware.  Once you've done that, the player appears to be a flash drive to your computer and no special software is required to access it.  I'm told that this isn't possible with the players sold to the US market, but that it does work with models sold in other parts of the world.   Since I've been using ifp-line, I haven't bothered to upgrade the firmware on my ifp-795.

---

### Post by anders_ps3 on 2007-12-16
Thanks!

This ifp-line, is it a script kind of thing, runnable on any hardware? My ps3/Kubuntu doesn´t understand Intel binaries.

Flashing up the ifp: I can't read memory cards, written from Windows, on my ps3/Kubuntu. And vice versa. In view of this, do you still think it would work?

---

