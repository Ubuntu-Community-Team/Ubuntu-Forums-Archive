---
title: "Strange problem -- restart and shutdown options gone!"
date: 2008-05-18
forum: General Help
---

### Post by adana on 2008-05-18
This is in 8.04

When invoking the System -> quit , the bottom line only offers hibernate. Restart and Shutdown are gone!

Similarly, at the login screens, there is no longer an option to shut down!

Very strange, any ideas??

---

### Post by adamthompson on 2008-09-06
I have this problem too. Does anyone have any ideas? Thank you.

---

### Post by showcaser on 2008-09-08
I had the same problem.

Have you tried this out:

[http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown](http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown)

If you can't get to the login window and you are in gnome it's probably cause you don't have GDM running (the gnome login window). This was my problem as I had intsalled KDE4 along side Gnome. 

You can do that by running:

```
sudo dpkg-reconfigure gdm
```

and selecting "GDM".

Then reboot and hopefully all is working

Hope that helps.

---

### Post by adamthompson on 2008-09-08
> **showcaser said:**
> I had the same problem.

Have you tried this out:

[http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown](http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown)



That fixed the problem. Thanks.

---

