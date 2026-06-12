---
title: "What's wrong w/this mouse cursor?"
date: 2015-05-15
forum: General Help
---

### Post by PenguinLust on 2015-05-15
In my never-ending quest to get pointers working on both my Ubuntu systems, I'm finding that my busy cursor doesn't work even though most other pointers in the theme are working. My guess about a key influence is that the busy cursor is the only animated one I've triggered so far. When the time comes to show a busy cursor, it shows one from another theme.
It could be naming. [http://www.freedesktop.org/wiki/Specifications/cursor-spec/?action=print](http://www.freedesktop.org/wiki/Specifications/cursor-spec/?action=print) says that the conventional name for the busy cursor is "wait", but /usr/share/icons/DMZ-White/cursors doesn't have a "wait", but it does have "watch". So I made a "wait" in my theme and made a sym link to it called "watch". Didn't work.
I included my wait cursor as an attachment. It might be a problem w/the way it was created. The input file for that is:
```
32 15 1 Ultima_Hi_Color_Wait_7_ankh-1.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-2.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-3.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-4.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-5.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-6.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-7.png
32 15 1 Ultima_Hi_Color_Wait_7_ankh-8.png
```
Although, I used to have "100" at the end of each line, to express the number of milliseconds it was supposed to display that image.

---

### Post by CantankRus on 2015-05-15
Isn't the busy cursor in DMZ-White named "**left_ptr_watch**"?

---

### Post by PenguinLust on 2015-05-15
The terminology is a bit confusing across the desktop world, but I think left_ptr_watch is the one that is often the basic cursor plus a miniaturization of the busy cursor.

---

### Post by CantankRus on 2015-05-15
> **PenguinLust said:**
> The terminology is a bit confusing across the desktop world, but I think left_ptr_watch is the one that is often the basic cursor plus a miniaturization of the busy cursor.
**left_ptr_watch** is the animation I see when waiting for a launched application to load.
Don't recall any situation where I see the **watch** animation.

---

### Post by PenguinLust on 2015-05-15
The watch/wait animation is most commonly an hourglass, which is supposed to mean the mouse is dead.

---

### Post by PenguinLust on 2015-05-15
... however following [your advice]("http://ubuntuforums.org/showthread.php?t=2277700&p=13285987#post13285987") in my other thread now shows the wait/watch cursor (at least, so far) in Lubuntu (I still have other problems on my desktop Ubuntu). Does it matter that I've never seen the left_ptr_watch? I don't even think I've seen it, even w/other cursor themes.

---

