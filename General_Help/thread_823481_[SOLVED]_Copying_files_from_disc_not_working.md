---
title: "[SOLVED] Copying files from disc not working"
date: 2008-06-09
forum: General Help
---

### Post by bardic on 2008-06-09
Hey all. Have a rather annoying issue here. Had this working on gusty and then did a clean installation of hardy and now I can't install NWN.

The problem arises when I try to copy files from the cd. It throws me errors like :

```

bardic@ubuntu:~/Games/nwn$ unzip /media/cdrom_/Data_linux.zip
Archive: /media/cdrom_/Data_linux.zip
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
note: /media/cdrom_/Data_linux.zip may be a plain executable, not an archive
unzip: cannot find zipfile directory in one of /media/cdrom_/Data_linux.zip or
/media/cdrom_/Data_linux.zip.zip, and cannot find /media/cdrom_/Data_linux.zip.ZIP, period.

```

or

```

bardic@ubuntu:~/Games/nwn$ unzip -o /media/cdrom_/data/XP1.zip
Archive: /media/cdrom_/data/XP1.zip
file #1: bad zipfile offset (lseek): 0
file #2: bad zipfile offset (local header sig): 38
inflating: ambient/al_mg_x0rui2.wav error: zipfile read error

```

Any idea's why this is happening? I'd love to play NWN again.

---

### Post by bardic on 2008-06-09
Ok, after some googling I read that it may be caused by the cp command, but I have no idea how to copy files from a cdrom any other way. 

Any help would be wonderful...

---

### Post by Stunts on 2008-06-20
Did you try to copy the file to your HD with nautilus and then unzip it?
```
bardic@ubuntu:~/Games/nwn$ [COLOR="Red"]cp[/COLOR] /media/cdrom_/Data_linux.zip
```

NWN rules.
=-)

---

### Post by bardic on 2008-06-20
Hey,
I figured out what the problem was. My DVD rom was on the fritz. Just made an iso on the roomies pc and it was all good ;)

---

### Post by Stunts on 2008-06-20
Glad it's all settled!

You should mark the thread solved or something!

---

