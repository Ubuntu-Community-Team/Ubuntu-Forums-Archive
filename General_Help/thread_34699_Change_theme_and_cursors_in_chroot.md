---
title: "Change theme and cursors in chroot"
date: 2005-05-16
forum: General Help
---

### Post by Sam on 2005-05-16
Hello

I'm running Ubuntu 64bit, and I've created a 32bit chroot (from [32-Bit Chroot How-To](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=32bit+chroot)). It worked well, but every application I run in the chroot environement has no theme (except for the window border) and the ugly core cursors. How do I change this in the chroot ??

Attachments: [Firefox without theme](http://ubuntuforums.org/attachment.php?attachmentid=1093&stc=1), [Firefox ok](http://ubuntuforums.org/attachment.php?attachmentid=1092&stc=1)

I've tried many things, please help me I'm stuck... ](*,)

---

### Post by Sam on 2005-05-16
I tryed```
$ sudo update-alternatives --config x-cursor-theme
```but the cursors I'm using in my non-chroot environement aren't recognized by this command in the chroot (and the file /chroot/usr/share/themes/Human/cursor.theme exists).

---

### Post by Duffman2010 on 2006-04-29
```

/usr/bin/dchroot -d
sudo apt-get install gtk2-engines-industrial

```

Or any other gtk2-engines-*

---

