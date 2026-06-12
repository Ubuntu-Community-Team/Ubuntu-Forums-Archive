---
title: "File Permission...Wine...Mp3tag"
date: 2007-07-25
forum: General Help
---

### Post by broth420 on 2007-07-25
I am trying to get MP3Tag to work under wine.  It installs no problem, and if I click run at the end of the install, it works great.  Once closed, however, it will not fire up again until I reinstall it and run at the end of the install (I get a long windows like message in German, and it says something about file access).  Well, I have attempted to do my own research and figure out what I have done wrong (WineHQ DB says it works well), but have run into sideline issues.  The one suggestion they have for getting wine to work is putting a .dll into the windows/system32 folder, but I can not copy anything into the folder.  My directory is "/home/broth/.wine" and it says it is owned by root.

My question is...How can I change permissions on this folder to copy stuff to it.
and side questions...
1. any help with wine/mp3tag, suggestions, comments, etc.  I don't like EasyTag as much.
2. winetools install??

I am trying to give up Windows, but man...

---

### Post by zanglang on 2007-07-25
Try
> sudo chown -R <your username> .wine
to change the .wine folder's ownership to you. Not sure about the other 2 though. :)

---

### Post by broth420 on 2007-07-26
Thanks for your help
As alwasy (I am learning Ubuntu the hard way I guess), my problem was self inflicted

I never ran winecfg after I installed Wine
and
I installed MP3Tag as the root user (sudo wine mp3tag....exe) which first created the folder /home/broth/.wine with root as the owner, and installed mp3tag as a root only app.  Which is why it would run if I choose "lauch mp3tag" at the end of the install, and wouldn't run after (I was still executing the program as root)

---

