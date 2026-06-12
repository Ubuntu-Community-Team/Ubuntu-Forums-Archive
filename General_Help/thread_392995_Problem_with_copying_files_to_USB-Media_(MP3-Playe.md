---
title: "Problem with copying files to USB-Media (MP3-Player, USB-Stick)"
date: 2007-03-25
forum: General Help
---

### Post by LilaQ on 2007-03-25
Hey folks,

I have a little problem with copying files to my MP3-Player or my USB Stick. There is no actual copy-bar that shows the status of the copy process. It often happened that I copied stuff on my USB-stick, unplugged it, plugged it to another computer and the data was not there. I read that you should first unmount the USB-stick to make the copy process complete. But still when I did that it happened that mp3s that I copied to my Portable Media Player or to the MP3-Player of my friend where totally messed up. The first dew seconds they play fine, then a song pops in that actually was deleted, than the 'original' song again and so on and on. This happened twice now, once from my desktop PC to my PMP, the second time from my laptop to the MP3-Player of my friend. So it's two times the same error, totally independent from each other.

Does anyone here have an elegant solution for this problem? Or can anyone tell me why there is no actual direct copy process + progress bar for copying to USB-media?

Btw, both my desktop PC and my laptop are running on Kubuntu 6.10

Thanks in advance,

LilaQ

---

### Post by jakev383 on 2007-03-25
> **LilaQ said:**
> Hey folks,

I have a little problem with copying files to my MP3-Player or my USB Stick. There is no actual copy-bar that shows the status of the copy process. It often happened that I copied stuff on my USB-stick, unplugged it, plugged it to another computer and the data was not there. I read that you should first unmount the USB-stick to make the copy process complete. But still when I did that it happened that mp3s that I copied to my Portable Media Player or to the MP3-Player of my friend where totally messed up. The first dew seconds they play fine, then a song pops in that actually was deleted, than the 'original' song again and so on and on. This happened twice now, once from my desktop PC to my PMP, the second time from my laptop to the MP3-Player of my friend. So it's two times the same error, totally independent from each other.

Does anyone here have an elegant solution for this problem? Or can anyone tell me why there is no actual direct copy process + progress bar for copying to USB-media?

Btw, both my desktop PC and my laptop are running on Kubuntu 6.10


Not using Kubuntu, but in regular Ubuntu when I plug in a memory stick it appears on my desktop. I then drag files to it and drop them. When I'm done, I right click the device and select "Eject" to be able to remove it. If there's a bunch of files copied to the USB stick then I will get a progress bar and I wait until that's done.
Very similar if you're using the command line. You'd umount the device.
Or you can dig into the automounter and try and change the options for mounting USB devices. You'd specifically be looking for the "sync" and "nosync" options for the filesystem.
Hopefully that will at least point you in the right direction.

---

