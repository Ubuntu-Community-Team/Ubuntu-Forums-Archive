---
title: "Sansa Clip+ Woes after upgrade to 13.04"
date: 2013-05-20
forum: General Help
---

### Post by strange_cathect on 2013-05-20
I upgraded to 13.04 and now my Sansa Clip+ is not working properly. It has quirky  issues with mounting, but I am able to get it to mount. However, I am unable to browse the files on it when mounted. The folders appear, but they seem empty. However, there are many .mp3 files in the folders that may be listened to. 

I am unable to add or remove songs from the device at present.

Anyone having this problem or know a fix? It was working fine under 12.10.

---

### Post by AgentZ86 on 2013-05-20
Try this from the Ubuntu Software Center:

Download and install gMTP

It's a little clunky but will transfer your files etc.

Android and mtp devices are different then normal storage space
gMtp you may still have to sometimes go to computer and right click to mount/unmount from time to time

But I found that if you run gMtp and wait like 10 seconds or so before clicking on connect device this works well

And as long as you remember REMEMBER to click disconnect and wait for it to complete it works well also
ONE last thing is once you disconnect I would still go to computer and unmount it again

A bit of a pain but should work for you.

---

### Post by BBQdave on 2013-05-20
I have my Sansa Clip+ set to **MSC** mode. No troubles accessing and transferring files through Nautilus on F18 - Gnome 3.6.3.

---

### Post by AgentZ86 on 2013-05-21
> **strange_cathect said:**
> I upgraded to 13.04 and now my Sansa Clip+ is not working properly. It has quirky  issues with mounting, but I am able to get it to mount. However, I am unable to browse the files on it when mounted. The folders appear, but they seem empty. However, there are many .mp3 files in the folders that may be listened to. 

I am unable to add or remove songs from the device at present.

Anyone having this problem or know a fix? It was working fine under 12.10.

Try right clicking it and formatting it again I had a problem with my new one I just purchased that actually showed up today.
Until I formatted it was stuck on refreshing media list etc. just FYI

I formatted to Fat but I assume linux formatting would be ok as well

---

### Post by strange_cathect on 2013-05-29
I formatted and reinstalled the firmware. Works now. Not sure what that was about.

---

### Post by AgentZ86 on 2013-05-29
yep me too
formatting probably was the key, I had to do the same thing and it's not glitchy at all works perfect in fact

---

### Post by gerryl on 2013-07-08
At least you were able to get your Sansa Clip to mount ;-)   After upgrading to 13.04 my Sansa Clip would not mount.  Got message 
Unable to access "SanDisk Sansa Clip+
Unable to open MTP device '[usb:001,012]'

gMTP will not connect either.  Help.

---

### Post by gerryl on 2013-07-08
Never mind - switching from USB to MSC mode solved the problem!

---

### Post by BBQdave on 2013-07-08
from [https://help.gnome.org/users/rhythmbox/stable/portable-audio-player.html.en](https://help.gnome.org/users/rhythmbox/stable/portable-audio-player.html.en)

[I]Rhythmbox can detect when an portable audio player is plugged to your     computer, and is able to read tracks stored on it.     Rhythmbox Music Player should be able to deal with most     portable audio players including Apple iPod, MTP players and Mass Storage     players.

[/I]
[I]When you plug in a portable audio player, an icon for the Portable Audio Player         is added to the side pane. This source works in the same way as the Library         source.
[/I]

 :!: *If Rhythmbox Music Player does not detect your device     as a portable audio player, you can create an empty file named*     **.is_audio_player** [I]at the top level hierarchy of the     filesystem of your player.
[/I]




I have my Sansa Clip+ set to **MSC** mode, and placed the **.is_audio_player** file on it - no problems syncing playlists from Rhythmbox :D

---

