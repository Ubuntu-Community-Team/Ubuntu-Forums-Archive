---
title: "Sound problems in Firefix"
date: 2006-07-07
forum: General Help
---

### Post by fhslacrosse13 on 2006-07-07
I have just recently installed Ubuntu onto my Acer laptop.  I have problems with getting sound from webpages while using Firefox.  Places like [www.purevolume.com](www.purevolume.com) and [www.myspace.com](www.myspace.com) wont play music when i try to listen to it.  When I play something from my harddrive (i.e. mp3 files) it works just fine.  What do i need to do to fix this?

Also, I noticed that youtube.com doesnt work.  Video is fine but no sound.

---

### Post by torfinn on 2006-07-07
What do you get when you hear sound and does:
$ lsof | grep -e /dev/snd

Compared to when not hearing sound. You may also try
searching for your program *name* as follows:

$ lsof | grep -e *name*

Torfinn

---

### Post by vem0m on 2006-07-07
also are you sure you have the required plugins for firefox installed? such as Java, Flash, ETC....?

---

### Post by Rui Pais on 2006-07-07
Hi,
mind to try my suggestion on [this thread]("http://ubuntuforums.org/showthread.php?p=1153742#post1153742")? 
If it still fails give a look at the solution/workaround pointed in this [bug report]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760") (see [comment 12]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12") of Daniel Carrera)

hope that helps

---

