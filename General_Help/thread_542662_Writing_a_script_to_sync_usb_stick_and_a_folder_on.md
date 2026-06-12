---
title: "Writing a script to sync usb stick and a folder on hd"
date: 2007-09-04
forum: General Help
---

### Post by fazza on 2007-09-04
hi all
just managed to write my first simple script (I think it's called that), and it works alright. It synchronises my school work with a folder on my desktop, then displays a window telling me it's finished syncing (using Zenity). However...
Say I have two files the same, one on usb, the other on hd. One was edited at 3:00, the other was edited at 3:19. I want to get the computer to work out which is the newest and bring them both up to date. At the moment, if I do work on the hd version and then sync them, I lose everything I did to it. But if I edit the usb version and sync it, they both contain the new data. Obviously, I could write two scripts to do the job, one for usb syncing and one for hd syncing, but I'd prefer it to be in one mouse click.
Here is the current script
```
cd /
cd /home/USERNAME/Desktop
rsync -u /media/usbdisk/School\ Work/. School\ Work
zenity --title "Coursework Sync" --window-icon "/usr/share/icons/Human/16x16/status/dialog-information.png" --info --text "Your files have been Synchronised."

```
If anyone can help, I'd be very grateful.


ps. sorry, typed some code wrong. I changed it and reposted - ended up posting twice. Go here [http://ubuntuforums.org/showthread.php?t=542664](http://ubuntuforums.org/showthread.php?t=542664) to see new post. Please reply to that one, not this one.

---

