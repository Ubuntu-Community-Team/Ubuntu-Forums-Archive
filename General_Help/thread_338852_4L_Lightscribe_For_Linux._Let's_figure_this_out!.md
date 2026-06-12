---
title: "4L: Lightscribe For Linux. Let's figure this out!"
date: 2007-01-15
forum: General Help
---

### Post by Megatog615 on 2007-01-15
Some of you may know that LaCie has released an application to interface with the Lightscribe feature of some DVD drives. Some of you may have problems getting it to work, like me. I get the common segfault error after trying to do 4l-cli enumerate, effectively rendering 4L, and the Lightscribe feature of my DVD burner useless.
I have talked with some Ubuntu users and some say they have gotten it to work, others say they have the same problem as me. I believe it may be caused by a difference in kernel version. LaCie has said there is a problem with Ubuntu 6.10, which leads me to believe this.
Who here has 4L working? If so, what kernel are you using? What Ubuntu version are you using?
Who here can't get 4L to work? If so, what kernel/Ubuntu version?

---

### Post by artinla on 2007-01-15
I have it, but have never tried to use it.  I will try it today and post the results.

Art

---

### Post by Shay Stephens on 2007-01-15
I have it installed on a dapper box.  It works great, and I use it to print labels for wedding video DVD slideshows.  So this is in a production environment.

The Specs:
Dapper 6.06
2.6.15.-27-386

I run the program with this command
gksudo 4L-gui

I have not tried to figure out why it needs sudo or how to fix it, it works, so I do it ;-)

---

### Post by po0f on 2007-01-15
Megatog615,

If you're using Edgy, [here's a little HOWTO I wrote](http://www.ubuntuforums.org/showthread.php?t=322829).  It should work just fine on Dapper.

---

### Post by Megatog615 on 2007-01-16
Heh, that works! So it is the kernel version?

---

