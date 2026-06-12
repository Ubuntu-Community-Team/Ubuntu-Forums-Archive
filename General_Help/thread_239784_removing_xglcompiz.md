---
title: "removing xgl/compiz"
date: 2006-08-19
forum: General Help
---

### Post by TheRingmaster on 2006-08-19
lets say I wanted to get rid of xgl/compiz. would following this post remove everything that needs to be removed?  [http://ubuntuforums.org/showthread.php?t=203621&highlight=removing+xgl%2Fcompiz](http://ubuntuforums.org/showthread.php?t=203621&highlight=removing+xgl%2Fcompiz)

if there is a better way please post it here. thank you!:)

---

### Post by hopstah on 2006-08-19
it depends on how you installed it.  find the thread that you followed and undo everything that it tells you to do.  there are many, many ways to install compiz, which means that the way you found might not actually remove every change you made when you installed it.

---

### Post by TheRingmaster on 2006-08-19
I installed it from this post here. [http://ubuntuforums.org/showthread.php?t=222034&highlight=xgl%2Fcompiz](http://ubuntuforums.org/showthread.php?t=222034&highlight=xgl%2Fcompiz)

---

### Post by hopstah on 2006-08-20
ok, that's what i used as well.  if you want to just stop compiz from starting, then remove the line that you added to your sessions manager, and you will be all set.

but to completely uninstall it, you will have to remove the stuff that you appended to the end of the gdm.conf-custom file, remove the /usr/bin/startcompiz file, and the following in a terminal should remove the compiz packages so they are no longer on your computer and won't be updated further

```
sudo apt-get remove xserver-xgl compiz-gnome cgwd cgwd-themes
```

---

### Post by TheRingmaster on 2006-08-20
I can't get rid of the /usr/bin/startcompiz file. all I could do was erase it. Do I have to be root to remove anything from that directory?

---

### Post by hopstah on 2006-08-20
yes.   ```
sudo rm /usr/bin/startcompiz
``` should do it for you.

---

### Post by TheRingmaster on 2006-08-21
thanks!

---

### Post by TheRingmaster on 2006-08-21
by the way I have noticed that after removing xgl/compiz (by doing the reverse of how I got it on there in the first place) that my cpu is higher than normal. It gets real high doing just trivial tasks. Is there a way to make sure that I have everything the way it was before I installed xgl/compiz?

---

### Post by kpkeerthi on 2006-08-21
Did you undo the changes you made to xorg.conf and gdm.conf-custom file when you installed xgl/compiz? Make sure you do that too. I assume you took backup of these file when you tinkered them for compiz.

---

### Post by TheRingmaster on 2006-08-21
I did change the gdm.conf-custom file back to the original but I never had to mess with the xorg.conf

---

