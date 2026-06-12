---
title: "Music Playing Daemon trouble"
date: 2006-12-26
forum: General Help
---

### Post by Zaggy on 2006-12-26
I'm trying to get mpd to create a database out of files on an usb hdd but it keeps giving me this:

> zaggynl@AMD3200L:~$ sudo mpd --stdout --verbose --create-db
flushing warning messages
done flushing warning messages
setFsCharset: fs charset is: UTF-8
flushing warning messages
done flushing warning messages
explore: attempting to opendir:
explore:
explore: found: MUSIC (MUSIC)
failed to stat MUSIC: Permission denied
removing empty directories from DB
sorting DB
writing DB
zaggynl@AMD3200L:~$


I'm not sure on how to set the permissions, since the usb device gets mounted automatically, and it gets mounted read only because it's an NTFS volume.

---

### Post by Zaggy on 2006-12-26
To elaborate:

-mpd is running using its own user 'mpd'
-I added this user to the plugdev group.
-The configured music dir is /var/lib/mpd/music
-I made a symlink in that dir which symlinks to my NTFS usb drive

---

