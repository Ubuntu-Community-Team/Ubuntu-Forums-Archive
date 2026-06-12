---
title: "Ghost Like Application"
date: 2007-08-15
forum: General Help
---

### Post by Vince4Amy on 2007-08-15
Is there any sort of application that I could use that is like Norton ghost. Preferably open source. I'm getting a 160Gb HDD for this laptop to replace the current 40Gb one. Will I be able to create an image of this HDD & stick it on the new one without any further intervening or will I have to change some settings eg Fstab.

---

### Post by shavenlunatic on 2007-08-15
i think I posted a while back asking if something like this existed.. it would be ideal if I could just set my system up how I wanted it... and if I every screw anything up, I can just recreate from the image and be back to normal...

nothing came of my request really other than making a copy of the home folder.. hopefully something has turned up since then which will image the whole HDD..

fingers crossed :)

---

### Post by PilotJLR on 2007-08-15
G4L is great for this.

---

### Post by Ubris on 2007-08-15
I have used *partimage* happily since I stopped using evil encumbered software.

I don't think it has an X front end. The version I used was [ncurses]("http://en.wikipedia.org/wiki/Ncurses") based, so it's not too scary and also pretty intuitive, if command-line happens to worry you. I'm pretty sure it has much more flexibility than Ghost, though, and, of course, no evil proprietary lock-in format. :)

It is in the default repositories, but I recommend using it from a live CD. Yes, step away from Ubuntu. EIther [SystemRescueCd]("http://www.sysresccd.org") or the wonderfully lighweight [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") are great environments from which to launch *partimage*. (I see looking that address up that GParted has another disk imaging option). Of course, if you are simply shifting small partition(s) to a larger disk, you can probably just use GParted (on both of those LiveCDs), which is a fantastic Partition Magic clone.

Happy cloning.

---

### Post by LaRoza on 2007-08-15
CloneZilla in my sig.

---

