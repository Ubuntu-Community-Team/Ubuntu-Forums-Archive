---
title: "Rollover mp3 icon in nautilus and play?"
date: 2007-06-10
forum: General Help
---

### Post by Geekkit on 2007-06-10
I saw from a couple of threads that you can have it in nautilus so that when you mouse over an icon of an mp3, it starts playing ... but this doesn't happen on my system. I have 7.04. I have all the appropriate CODECS and Totem and Rhythmbox work like a charm with every possible media stream I've come across (including playing my DVDs). Is there some sort of script I need to edit?

Thanks in advance.

---

### Post by Ek0nomik on 2007-06-10
Open a terminal and type:

```
sudo aptitude install mpg321
```

Log out of your session, and log in again.  Put your folder viewing as icons (not list) and then... hope.  :)

---

### Post by Geekkit on 2007-06-10
> **Ek0nomik said:**
> Open a terminal and type:

```
sudo aptitude install mpg321
```

Log out of your session, and log in again.  Put your folder viewing as icons (not list) and then... hope.  :)

Ek0nomik, thank you sah, that worked like a charm!  :p  Such a little thing but when I read someone post that you could do that I thought that was just one of those thing I really wanted to have.

:D

---

### Post by mcduck on 2007-06-10
For ogg files, get the vorbis-tools package. I'm still looking for information about which package enables flac preview..

---

