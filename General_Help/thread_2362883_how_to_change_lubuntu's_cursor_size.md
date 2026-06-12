---
title: "how to change lubuntu's cursor size"
date: 2017-06-03
forum: General Help
---

### Post by ardouronerous on 2017-06-03
I've found this:
[https://www.gnome-look.org/content/show.php/Large+Mouse+Cursors?content=140787](https://www.gnome-look.org/content/show.php/Large+Mouse+Cursors?content=140787)

I installed this on */home/username/.icons*, however, the cursors are too big, and it doesn't work globally.

I've already tried this solution:
[http://bbs.archbang.org/viewtopic.php?pid=23727](http://bbs.archbang.org/viewtopic.php?pid=23727)

It works, I can choose the size, but it doesn't work globally.

---

### Post by vasa1 on 2017-06-03
See if Dennis N's post helps you: [https://ubuntuforums.org/showthread.php?t=2234783&p=13075327#post13075327](https://ubuntuforums.org/showthread.php?t=2234783&p=13075327#post13075327)

---

### Post by ardouronerous on 2017-06-03
Actually, what I want to use is already installed here: /usr/share/icons/DMZ-White

I just want to make the cursor bigger, but the solution I've tried doesn't work globally though.

---

### Post by vasa1 on 2017-06-03
> **ardouronerous said:**
> ... but the solution I've tried doesn't work globally though.
Then please explain "doesn't work globally".

And read through [https://ubuntuforums.org/showthread.php?t=1974227](https://ubuntuforums.org/showthread.php?t=1974227)

---

### Post by ardouronerous on 2017-06-03
> **vasa1 said:**
> Then please explain "doesn't work globally".

And read through [https://ubuntuforums.org/showthread.php?t=1974227](https://ubuntuforums.org/showthread.php?t=1974227)

The cursor resize only works in Firefox, when you go onto the desktop, it reverts back to it's default size, which is 18.

It looks like a reboot did the trick, the size of the cursor is now my desired size.

For those who want to know how I did this, here's the instructions:

To change the size of your mouse cursor, go to:

```
/home/USERNAME/.config/lxsession/Lubuntu/desktop.conf
```

Find this line:

```
iGtk/CursorThemeSize=18
```

and change the value, in my case, my desired size is 36.

Then save and then do a reboot.

---

