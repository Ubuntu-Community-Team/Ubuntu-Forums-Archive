---
title: "Can Not Retrieve Data From 32GB SD Card FAT16 File System"
date: 2015-10-30
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-10-30
Hello,

I recently purchased the following traffic cam from Amazon FAT16 file system; and Ubuntu can not mount it or read it.

[h=1]WanTech R300 2.7" 140° Dual Lens Dash Board Camera Black Box Video Recorder Car HD DVR[/h]The 32GB SD card did mount in Windows; but the only file visible was a software labled RGA-PLay. The video files were somehow hidden; I suspect encrypted. RGA-Play would indeed play the video files; so they obviously exist; but not in a form that I can access. The file format is AVI. The device also appears to have been made in Russia, based on the users manual. I tried to use GParted to recover the video files; but it reported that there were no file systems on the card other than FAT16. Does anyone know how to recover the video files. I would like to save the data and reuse the card. If there was ever a legitimate use for decryption, this is certainly it.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-11-02
I finally got this figured-out; but what a headache. I've even managed to post the video on YouTube. Here's the link, just to prove it works:

[https://www.youtube.com/watch?v=RXkIyJ4Qkjc](https://www.youtube.com/watch?v=RXkIyJ4Qkjc)

Below is a response I provided at another tech-support site; that asked about this as well:

X2Player is a legitimate media player, probably Chinese in origin. I  have a WanTech R300 Blackbox DVR DashCam that uses this player. First  the Device formats the 32GB SD card to FAT16, then adds this player to  the SD card. The device encrypts the .avi video files, so they can't be  accessed without the player. The player will however save the video to  your hard drive, by pressing the floppy disc icon, and selecting the  destination folder. Windows however won't play the files, out of the  box; but Linux will, oddly enough. The sytem is a real pain in the neck;  but it works, if you have the time to figure it out. No it's not a  virus.

---

