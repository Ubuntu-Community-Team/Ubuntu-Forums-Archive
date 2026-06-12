---
title: "Vlc opening on double clicking mp4"
date: 2016-07-17
forum: General Help
---

### Post by 4kh3RAm on 2016-07-17
Vlc used to open when I double clicked on a mp4 file.

It does so no longer.

It may be a coincidence, but this behavior started when I added the ability for Vlc to play DVDs.

If I open Vlc and then open the file, it does play.

How can I fix that ?

---

### Post by howefield on 2016-07-17
Try right clicking the mp4 file and select Properties, then from the "Open with" tab select VLC and set as default.

---

### Post by 4kh3RAm on 2016-07-17
Thanks, that works with Caja.

Thunar is my preferred file manager.

However, I can not associate mp4s with VLC.

Can that be fixed ?

---

### Post by &amp;KyT$0P# on 2016-07-17
Check my posts in [https://ubuntuforums.org/showthread.php?t=2329806]("https://ubuntuforums.org/showthread.php?t=2329806"), that method works for me under Thunar / Xubuntu 16.04

---

### Post by 4kh3RAm on 2016-07-17
I have this but it is not working.

> [Added Associations]
application/mp4=vlc.desktop;

[Default Applications]
application/mp4=vlc.desktop


---

### Post by vasa1 on 2016-07-17
Shouldn't [https://ubuntuforums.org/showthread.php?t=2330990&p=13518518#post13518518](https://ubuntuforums.org/showthread.php?t=2330990&p=13518518#post13518518) be independent of the file manager?

---

### Post by &amp;KyT$0P# on 2016-07-17
Hmm, I found also a similarly formatted mimeapps.list file in ~/.config that I'm certain I didn't create.  What if you put in that mimeapps.list file instead?

EDIT And it seems to have an entry for VLC media player for mp4 videos under Added Associations:
```
video/mp4=vlc.desktop;
```

---

### Post by 4kh3RAm on 2016-07-17
I have that same file with those added associations.

When I use Thunar without root permission, the file association works.

I will just use it, though I prefer Super Thunar.

I have no other problems with other file associations with Super Thunar.

Makes me wonder if it is related to VLC ??

---

### Post by &amp;KyT$0P# on 2016-07-17
> **4kh3RAm said:**
> When I use Thunar without root permission, the file association works.
And that's likely why it doesn't work.  Try editing **/root/.config/mimeapps.list** (obviously, must use sudo or gksu)

For everyone else reading this thread, it is NOT SMART to run file manager as root unless absolutely necessary :o so just don't use Thunar as root for all the time.  Problem solved. ;)

---

### Post by 4kh3RAm on 2016-07-17
mimeapps.lst already has the right file association.

I _**only**_ use Thunar as root when I have to edit protected files.

---

### Post by howefield on 2016-07-18
Threads merged.

---

