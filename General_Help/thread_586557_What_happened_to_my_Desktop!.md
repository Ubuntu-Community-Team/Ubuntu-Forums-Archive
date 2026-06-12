---
title: "What happened to my Desktop?!"
date: 2007-10-22
forum: General Help
---

### Post by Ub1476 on 2007-10-22
Ok, I just started up my pc today and it looks like this: [Click](http://img518.imageshack.us/my.php?image=desktoppl3.png)

As you see I created some shortcuts on the desktop so I could use the terminal and firefox, because the panel doesn't respond. The below panel is supposed to be on the bottom of he screen (stretched) and the top panel is supposed to be where it is (stretched), along with some other apps on it. 

If I open the terminal and write..:

```
sudo killall gnome-panel
sudo gnome-panel
```

Both panel works again, but my GTK theme and icons looks **. 

I wonder if has something to do with [Gimmie]("http://www.beatniksoftware.com/gimmie/Main_Page")  which I installed the other day, but I've removed it now and it's still the same. 

I tried restarting X and all that.

Help fast please:(

---

### Post by UK-Wobbie on 2007-10-22
> **Ub1476 said:**
> Ok, I just started up my pc today and it looks like this: [Click](http://img518.imageshack.us/my.php?image=desktoppl3.png)

As you see I created some shortcuts on the desktop so I could use the terminal and firefox, because the panel doesn't respond. The below panel is supposed to be on the bottom of he screen (stretched) and the top panel is supposed to be where it is (stretched), along with some other apps on it. 

If I open the terminal and write..:

```
sudo killall gnome-panel
sudo gnome-panel
```

Both panel works again, but my GTK theme and icons looks **. 

I wonder if has something to do with [Gimmie]("http://www.beatniksoftware.com/gimmie/Main_Page")  which I installed the other day, but I've removed it now and it's still the same. 

I tried restarting X and all that.

Help fast please:(

Can you right click on it and go to properties? And then re put the size back?

And you can move the bar to the bottom of the screen! :)

---

### Post by Ub1476 on 2007-10-22
Nope, it is not responding.

---

### Post by Ub1476 on 2007-10-22
I guess I'll do a reinstall then..

---

### Post by loganm10 on 2007-10-22
you shouldnt use sudo to restart the panel, that would run it as root, which is why your themes would be messed up

---

