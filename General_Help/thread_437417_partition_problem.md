---
title: "partition problem"
date: 2007-05-08
forum: General Help
---

### Post by themerchant on 2007-05-08
Ok, so I already have ubuntu installed on my machine,, and I have extra room (Ubuntu is my only OS), so I used a live cd to split that drive up into a smaller piece so I can try out another distribution, but there is some error, any suggestions or precautions, anything I should do to the hardrive before splitting it up again?

I'm guessing the hardrive had information all over the place.

[[IMG]http://img186.imageshack.us/img186/1599/screenshot1sr9.png[/IMG]](http://imageshack.us)

---

### Post by Sef on 2007-05-08
You cannot partition a mounted partition.  I would download [GParted]("http://gparted.sourceforge.net") itself and run it.   That should take care of your problem.

---

### Post by Scheater5 on 2007-05-08
Boot into the hard disk and verify that it is not corrupted.  If all is well then the "error" was merely an abortion of the process without doing anything (which I think is what happened from viewing the error messages).  
The only thing you did wrong is trying to partition a mounted drive.  You must first unmount a drive before editing the partition table.

---

