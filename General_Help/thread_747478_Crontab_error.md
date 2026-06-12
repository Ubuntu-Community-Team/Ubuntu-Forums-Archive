---
title: "Crontab error"
date: 2008-04-06
forum: General Help
---

### Post by max69 on 2008-04-06
Hello,
I use disspam to delete spam from my mail server and usually use a crontab. I just installed xubuntu 8.04 and try to do the same as on my 7.04 install and made exctly the same crontab
```
MAILTO=blabla@blabla.fr
0,9,18,27,36,45,54 * * * * /home/max/disspam-0.14/disspam.pl /home/max/disspam-0.14/sample.conf
```
which was working fine on my old install. But on Hardy it gives me a "bad minute error". I am a bit lost there. Anyone got any clues?
Thanks in advance.

EDIT: oops sorry just realised it was not the right thread to be posting in. Please feel free to move it to the Hardy thread.

---

### Post by max69 on 2008-05-06
Hello,
just to tell you problem solved.you should always maximize the Terminal window when using crontab or these kind of things happen.

---

