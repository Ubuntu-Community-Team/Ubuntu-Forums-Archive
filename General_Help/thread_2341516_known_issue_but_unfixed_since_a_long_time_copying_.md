---
title: "known issue but unfixed since a long time copying files from linux to usb stick"
date: 2016-10-28
forum: General Help
---

### Post by harlock593 on 2016-10-28
Hello,

i have a recurring issue when i try to copy from my linux filesystem huge amounts of data (more than 500 gigs) the copy seems to work correctly and then the window of the copy closes, then i try to eject the key from thunar by clicking on the eject sign but then a notification appears telling me that the copy is still in progress or that there are pending operations on the usb key, although the copy window did close itself since a lapse of time.

i don't know how to fix this issue and i have this since quite a long time with different versions of xubuntu (i think that it's the same with ubuntu).

then i can't unmount or remount the key and all i can do is reformat it from windows.

---

### Post by speartip on 2016-10-29
What filesystem are you copying to? (ext4, ntfs, fat32)
Also with that amount of data, I would suggest using a program like rsync, rather than the copy command.
In Xubuntu 16.04, I have a similar issue, when ejecting usb sticks, but after a few seconds the notification goes away, allowing me to remove the media.

---

### Post by oldrocker99 on 2016-10-29
+1 for rsync. Grsync provides a graphical interface, and works like a charm for me. It's my go-to for backing up /home.

BTW, I'd love to get a 512 GB thumb drive...:D

---

### Post by alexjpowell on 2016-10-29
I've come to the conclusion that the write shows as being completed prematurely

---

