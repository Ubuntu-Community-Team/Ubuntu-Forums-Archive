---
title: "How to make an iRiver T30 mp3 player work w Linux"
date: 2007-09-26
forum: General Help
---

### Post by m9ke on 2007-09-26
Discovered that my iRiver T30 mp3 player is not recognized as a USB device in Ubuntu.  This is because the US version of this player is limited to use Windows Media Player (WMP) and Media Transfer Protocol (MTP) to move files on to the player.

Turns out iRiver uses MTP (M$'s  Media Transfer Protocol) as part of the DRM for this unit.   On the other hand, European/Australian players use UMS (USB Mass Storage).  This means they can be written to and from like any USB  device. 

You can upgrade your  firmware to switch  US MTP devices to become UMS devices.  This means they can be accessed by Linux (and Windows) without WMP and MTP.   Your device will behave like any other USB device.  This upgrade is from iRiver, and is straightforward.  I completed it with no problems, but as always YMMV.

You will need access to a Windows box to do this.  Also take all your files off the player before starting as the firmware upgrade will delete data on the player.

A tip of the hat to Phillip Stevens, who posted the article I learned this stuff from.

Check out his directions for this upgrade:
[http://l2ll.wordpress.com/2007/08/13/using-the-iriver-t30-medial-player-with-linux/](http://l2ll.wordpress.com/2007/08/13/using-the-iriver-t30-medial-player-with-linux/)

---

### Post by pay on 2007-09-26
My creative mp3 player used mtp and it was a simple case of installing mtp and gnomad, cant the iriver's use mtp in linux?

---

### Post by m9ke on 2007-09-27
Well, I don't know if the iRiver can use MTP.  If someone wanted to use it there might very well be a way.

What I saw when I plugged in the USB cable, was that the player was not recognized like every other USB  device I use with Linux.  Trying to figure out why, I read the iRiver manual, where they say you have to use Windows Explorer to manage files on the player.  Also found it relies on MTP, not USB, as well.

At that point I lost interest in anything not related to making the player a standard USB device.  iRiver has a fully supported option in the firmware upgrade (not a hack) to switch from MTP to USB.

Could the iRiver work with MTP?  Maybe.  Is it more to my liking as a USB device?  Sure.

---

