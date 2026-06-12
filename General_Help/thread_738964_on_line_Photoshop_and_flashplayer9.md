---
title: "on line Photoshop and flashplayer9"
date: 2008-03-29
forum: General Help
---

### Post by thered on 2008-03-29
I was going to try the online version of photoshop express but it keeps telling me I haven't got flashplayer9 installed.

[https://www.photoshop.com/express/landing.html](https://www.photoshop.com/express/landing.html) - 'test drive' link.

I'm sure I have, I can view most online graphics and videos.

I've un-installed 'flashplayer non-free' as mentioned on other threads and re-installed it as it made no difference.

I've deleted xpti.dat as recommended by the flash-installer - this has made no difference either.

Anyone else having problems with this site, or any ideas how I can resolve it?

---

### Post by justleen on 2008-03-29
try downloading the flash version from adobe, and install that one?

edit: it works fine for me, using the flash installer from adobe

---

### Post by thered on 2008-03-29
ok justleen, thanks for that, at least I know the site does work.  I have indeed tried  the gz from Adobe.  

Back to the drawing board :)

---

### Post by Rebeca on 2008-04-01
I was having this problem too. I uninstalled the flashplayer non-free, then I downloaded the tar.gz from Adobe and installed globally. I checked my about: plugins, and it showed both flashplugins installed (48 and 115), so after going to the appropriate folder,

```
cd install_flash_player_9_linux
```

I installed locally,

```
./flashplayer-installer
```

And, it worked.

---

