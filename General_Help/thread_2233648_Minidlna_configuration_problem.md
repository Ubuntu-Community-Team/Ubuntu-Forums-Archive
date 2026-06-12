---
title: "Minidlna configuration problem"
date: 2014-07-09
forum: General Help
---

### Post by frank72 on 2014-07-09
Hello all. I hope someone can help me.
I'm trying to share files from my secondary hard drive. My config looks like this.


port=8200
media_dir=A,/home/****/Music
media_dir=A,/media/4ext/Music2
media_dir=P,/home/****/Pictures
media_dir=V,/home/****/Videos
friendly_name=Bobbys DLNA Server
inotify=yes
enable_tivo=no
strict_dlna=no
notify_interval=900
serial=12345678
model_number=1

/media/4ext/music2 is the hard drive.
It dosn't show on any app.
Can anyone tell me whats wrong?
Thanx in advance

---

### Post by AnotherKevin on 2014-07-12
I just installed minidlna today, myself.  I had (and am still having) problems.  I got rid of a few of them by setting ***[COLOR=#000000]inotify=no[/COLOR]*****[COLOR=#000000][/COLOR]**[COLOR=#000000] and ***#***[/COLOR]***[COLOR=#000000]notify_interval=900 [/COLOR]**[COLOR=#000000](comment out). [/COLOR]*[COLOR=#000000]

Not sure if that will help you, but in searching for help for myself, I came to see that a lot of others have ended up doing this to get rid of problems.   There's not a lot of help out there for minidlna, and what IS there is pretty deep, if you're not really up on network stuff.

Good luck!   [/COLOR]:p[COLOR=#000000]

Kevin[/COLOR][COLOR=#000000][/COLOR]

---

