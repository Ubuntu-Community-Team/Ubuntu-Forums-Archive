---
title: "Banshee and CD recognition"
date: 2013-10-15
forum: General Help
---

### Post by djpemberton on 2013-10-15
I am trying to use Banshee on Kubuntu 13.04. Most everything seems to work fine. The main gripe I have is that Banshee doesn't recognize when I insert a CD. It will only recognize a CD that is inserted if it is already inserted when I launch the program. Also, it doesn't recognize that I have ejected a CD unless I eject it from within the program. Finally, when a CD is inserted and the KDE notification pops up, Banshee is not listed as an action for the CD. Any solutions?

---

### Post by mastablasta on 2013-10-15
the first part happens in amarok as well. as i remember the issue is that system mounts the CD at a different place than default setting. and the programmes should automaticly use that mount but instead they persist with their own mount point so they can't find anyhting there.

> my cd is under /dev/scd0 and not under dev/cdrom (no wonder it couldn't read it before).



---

### Post by djpemberton on 2013-10-15
How do you change it to where it all works smoothly?

---

### Post by Erik1984 on 2013-10-15
Not a direct solution but what I do is rip the CD with K3B and then use my music player of choice to listen to the music.

---

### Post by djpemberton on 2013-10-15
I'm not sure that is the solution I need. Banshee does recognize a CD is in the drive when it is there before I open Banshee. I also just found out that I can go to "Media" - "Open Location" and Browse to "Audio Disc" in "Places." This gets Banshee to recognize that there is a disc. Why won't it recognize it when it is inserted?

---

