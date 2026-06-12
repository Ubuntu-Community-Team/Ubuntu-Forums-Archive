---
title: "Having problems with NVIDIA 9629 drivers want to revert back to 2625"
date: 2006-11-17
forum: General Help
---

### Post by roger99 on 2006-11-17
The other day update-manager updated my NVIDIA drivers to the latest version 9629.  Now I can't get beryl to work.  It worked when I had driver version 9625 so I want to revert back.  I have all the packages (I think) in /var/cache/apt/archives but i'm not sure how to revert back to them.  I was hoping somebody could give me some advice before I get tempted to dive into it and break my system.

---

### Post by mart01 on 2006-11-18
I am also having this problem with the nvidia drivers on a GeForce 4 and need to reinstall the old drivers, but being a relative noob do not know how to do it.  After checking I also have the packages in the apt cache.  Please help....

---

### Post by Adramelech on 2006-11-18
same here but is fixed now, the problem is a [bug]("http://www.nvnews.net/vbulletin/showthread.php?p=1056053&posted=1#post1056053")    with gforce 3 and 4 video cards, i try to get the packages from amaroth repository again but it didnt work, i guess because of the restricted modules, so i installed from Alberto Milone (Tseliot?) blog [instructions]("http://albertomilone.com/driver_edgyunstable.html")

---

