---
title: "installing QuickTime with Wine has bugs"
date: 2008-03-15
forum: General Help
---

### Post by FastMady123 on 2008-03-15
I try to install QuickTime with wine but it causes the screen to be blank. I think it a bug in wine. What should I do?

---

### Post by por100pre1 on 2008-03-15
If you haven't done so yet, you can use this method in order to use the latest version of wine:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Maybe QuickTime won't work anyway read this:

[http://appdb.winehq.org/appview.php?appId=1029](http://appdb.winehq.org/appview.php?appId=1029)

If you need QuickTime for watching mov movies, you can use Mplayer Plugin for Mozilla. Copy, paste and ENTER each one of these commands, one by one, in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install mozilla-mplayer
```

```
sudo apt-get remove totem-mozilla
```

---

