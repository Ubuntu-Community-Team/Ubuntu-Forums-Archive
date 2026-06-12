---
title: "/dev/hda1 has been mounted....what does it mean?"
date: 2007-02-10
forum: General Help
---

### Post by zazen666 on 2007-02-10
Hi,
I have a question. evey so often when I start up my computer i get the follow message:

/dev/hda1 has been mounted 30 times withou being checked. check forced


does anyone know what this means or how to stop it?
thanks

-marshal

---

### Post by dwasifar on 2007-02-10
Every time you boot, Linux "mounts" the disk partitions, which is just a way of saying that it makes them available for use.  Default behavior for Ubuntu is to check the partition for problems every 30th mount.

Don't sweat it.  It's a good thing, and it's there to help you prevent problems.  If it finds anything it will give you options for fixing it.

---

### Post by zazen666 on 2007-02-10
cool-thank for that. its a bit clearer now.

one more question. I did not split my hard drive when I installed linux. I erased winodws complety . should I still see this message

---

### Post by mystman on 2007-02-10
Yes.  It's like disk checker in windows.

---

### Post by Skidpad on 2007-02-10
Here's a nice little app to manage the forced disk check at boot.  Hats off to AgenT for this  :)

[http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager]("http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager")

---

