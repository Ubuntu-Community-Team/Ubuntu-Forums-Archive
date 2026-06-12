---
title: "Playing audio files"
date: 2006-10-24
forum: General Help
---

### Post by ozmium on 2006-10-24
Hi!

I've been having a problem with playing basic audio format mp3 on my ubuntu (6.06) for awhile now. My audio files are located at my other computer (has got more disk space) and it's running on windows. So I share the files trough network. Only player that plays these files is Rhythmbox.I've tried other porgrams (such as maroK, Real Player, JuK, Beep Media Player, XMMS Music Player) and they won't work. So does anyone have any clue what this is all about? ](*,)

---

### Post by dbd on 2006-10-24
Do mp3 files play fine if they are on your hard disk and not accessed via the network?

---

### Post by ozmium on 2006-10-24
> **dbd said:**
> Do mp3 files play fine if they are on your hard disk and not accessed via the network?

Yes they do.

---

### Post by dbd on 2006-10-24
I really don't have any idea why one media player would work when the others don't, very strange.

This is really a shot in the dark, but how are you accessing the other computer? You could try mounting the shares as explained here:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
But that really is nothing other than a crazy guess, so no guarantee it will help!

---

### Post by ozmium on 2006-10-24
Actually it made the situation worse. Even the Rhythmbox would not play the files after that :(

---

### Post by IYY on 2006-10-24
Instead of just sharing the folders, you'll need to mount them. Something like 

mount -t smbfs //dc/tmp /tmp/test

(this will probably not work as I just got it from a quick google search. I remember using a similar approach earlier, though, and after some tweaking it worked).

---

### Post by ozmium on 2006-10-25
> **IYY said:**
> Instead of just sharing the folders, you'll need to mount them. Something like 

mount -t smbfs //dc/tmp /tmp/test

(this will probably not work as I just got it from a quick google search. I remember using a similar approach earlier, though, and after some tweaking it worked).
well it almost worked but you did find the solution for problem. I tried mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test and it worked well. Still wondering though how that one player could play the files even they weren't mounted..

---

### Post by skymt on 2006-10-25
I think Rhythmbox uses Gnome VFS, the system Gnome uses in applications like Nautilus and gEdit to access remote file systems without "physically" mounting them.

---

