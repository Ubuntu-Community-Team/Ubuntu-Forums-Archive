---
title: "Photo management software for Ubuntu?"
date: 2005-04-10
forum: General Help
---

### Post by mmcmonster on 2005-04-10
Hi.
  I'm looking for some sort of photo management software for Linux in general and Ubuntu specifically.  Something with capabilities similar to Jasc Photo Shop Photo Album.  This isn't for me, but to make it possible for my dad to take the plunge into linux.
  Does anything like this exist?
  I noticed LPhoto, and found the [link](http://de.kde-apps.org/content/show.php?content=19947&forummode=2&forumpage=1&forumexplevel=3) to it.  I'm kind of nervous to try it, since it's not a .deb package and I'm pretty new with the whole linux thing.
  Any ideas / other applications?
Thanks,
Maimon

---

### Post by humanity_to_others on 2005-04-10
gphotocoll
[http://gpc.sourceforge.net/screenshots.php3](http://gpc.sourceforge.net/screenshots.php3)

---

### Post by Reb on 2005-04-11
digikam - [http://digikam.sourceforge.net/Digikam-SPIP/](http://digikam.sourceforge.net/Digikam-SPIP/)

---

### Post by Bob D. on 2005-04-11
[gThumb](http://gthumb.sourceforge.net/) , which is included in the Ubuntu base install, is one option. 

Another choice would be [F-Spot](http://www.gnome.org/projects/f-spot/). This app is most likely the future replacement for gThumb (my guess). While still in early development, it is quite functional right now. You can install F-Spot using Synaptic by activating the Universe repository.

Bob

---

### Post by paretooptimum on 2005-04-12
I would like to recommend the poorly named but very useful pornview.  Its in the universe repository. I don't know if your dad will get over the name?

---

### Post by mathjazz on 2005-04-12
[QUOTE=paretooptimum]I don't know if your dad will get over the name?[/QUOTE]
ROTFL

---

### Post by mathjazz on 2005-04-12
[QUOTE=mmcmonster]Hi.
  I'm looking for some sort of photo management software for Linux in general and Ubuntu specifically.  Something with capabilities similar to Jasc Photo Shop Photo Album.  This isn't for me, but to make it possible for my dad to take the plunge into linux.
  Does anything like this exist?
  I noticed LPhoto, and found the [link](http://de.kde-apps.org/content/show.php?content=19947&forummode=2&forumpage=1&forumexplevel=3) to it.  I'm kind of nervous to try it, since it's not a .deb package and I'm pretty new with the whole linux thing.
  Any ideas / other applications?
Thanks,
Maimon[/QUOTE]
 gThumb is good, except it does not have an option to resize multiple images at once. You can rename, rotate and convert formats, but you cannot scale them.

And it's a little bit slow.

---

### Post by MaX on 2005-04-12
[QUOTE=mmcmonster]Hi.
  I'm looking for some sort of photo management software for Linux in general and Ubuntu specifically.  Something with capabilities similar to Jasc Photo Shop Photo Album.  This isn't for me, but to make it possible for my dad to take the plunge into linux.
  Does anything like this exist?
  I noticed LPhoto, and found the [link](http://de.kde-apps.org/content/show.php?content=19947&forummode=2&forumpage=1&forumexplevel=3) to it.  I'm kind of nervous to try it, since it's not a .deb package and I'm pretty new with the whole linux thing.
  Any ideas / other applications?
Thanks,
Maimon[/QUOTE]
 f-spot is good for photo management

---

### Post by paretooptimum on 2005-04-13
Look, I'm all out on a limb here on pornview, can I get an amen? someone? You people are all like "F-Spot." "F-Spot." Its kinda buggy and in development and it gives you mono. Pornview is simple, stable and clean. You can admit to us you use pornview all the time, we're your friends. 

mmcmonster: Maybe you could change the icon and name, call it picview or photoview or familysnap or something. Can someone write a HOWTO on renaming pornview for your dad?

---

### Post by lao_V on 2005-04-13
I would like to know what the author was thinking when naming this app? Is it an accronym for something? Picture O R N view??

---

### Post by pip on 2005-04-13
I know what he was thinking when he designed the app.  ;-)

---

### Post by dninja on 2005-06-14
Has anyone else had the problem that pornview locks up when you try to close it? I've tried monitoring it with strace and the last couple of lines are:

futex(0xb5c81bf8, FUTEX_WAIT, 7135, NULL) = 0
write(12, "\215\r\4\0=\0\0\0J\0\0\0\1\0\0\0\215\r\4\0=\0\0\0L\0\0"..., 132) = 132
futex(0x87ee0d8, FUTEX_WAIT, 0, NULL

This happens even if I just open it then close it again without actually doing anything with it.

---

### Post by angkor on 2005-06-14
[QUOTE=dninja]Has anyone else had the problem that pornview locks up when you try to close it? [/QUOTE]


Maybe you try to close it too soon... ;-)

---

