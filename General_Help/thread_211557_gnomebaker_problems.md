---
title: "gnomebaker problems"
date: 2006-07-08
forum: General Help
---

### Post by mmmichael on 2006-07-08
gnomebaker worked fine until today. I tried opening from the apps menu as usual and nothing happened. trying from terminal reulted in:

michael@michael-desktop:~$ gnomebaker
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
Aborted

So I did a forum search and found a cvs at
[http://www.ubuntuforums.org/attachment.php?attachmentid=9635&d=1147878250](http://www.ubuntuforums.org/attachment.php?attachmentid=9635&d=1147878250).

I installed the new gnomebaker and it opens but when I try to burn a data cd it tells me to put a disk in my cd-rom drive, even though the cd-rw drive was selected.

Does anyone know what I can do without switching ide cables? (I'm going to try opening a kde session and using K3b, but I'm really more comfortable in gnome.)

---

### Post by RawMustard on 2006-07-08
try this [link]("http://www.ubuntuforums.org/showthread.php?t=178288"), the copy on that page worked for me.

---

### Post by mmmichael on 2006-07-08
Yeah, that's where I found the cvs package. I installed it, it opened, it showed the cd-rw drive selected. Then after it prepared the file it told me to put a disk in the cd-rom drive!

---

