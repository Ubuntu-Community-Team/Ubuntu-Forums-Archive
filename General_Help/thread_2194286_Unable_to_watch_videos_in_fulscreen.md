---
title: "Unable to watch videos in fulscreen"
date: 2013-12-17
forum: General Help
---

### Post by dorigoluca on 2013-12-17
Hi, my problem seems quite common but I can't find a way to solve it...

Web videos work fine except when I try to watch them in fulscreen,

Usualy the first time I click on the full-screen button it kind of works but then it bugs and when I try to put them in fulscreen again, the video stops and the controls disappear.

I read that I should try to disable flash hardware acceleation but I can't figure out how to do this, when I right-click a flash content the ''settings'' option is greyed out...

Any help would be welcome! Thanks!

some details:

some youtube videos seem to work fine, and I can change the settings on these. other players than youtube usually don't work in fullscreen.

I have ubuntu 13.10. my laptop is a samsung X420 with intel 256M integrated graphics.

---

### Post by andrej1741 on 2013-12-17
You can try use Google Chrome. And write output for this command
```
lspci -k|grep VGA -A2
```

---

