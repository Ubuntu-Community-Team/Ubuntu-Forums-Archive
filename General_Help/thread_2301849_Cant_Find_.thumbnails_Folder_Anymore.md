---
title: "Cant Find .thumbnails Folder Anymore"
date: 2015-11-05
forum: General Help
---

### Post by jooge on 2015-11-05
I installed a new HDD on my laptop and installed Ubuntu 14.04.3 on it. For about 2 weeks now I have not seen my old .thumbnails folder that use to be there. I do see that there are some images in ~/.cache/thumbnails.

On 12.04 there were images in both ~/.cache/thumbnails & ~/.thumbnails

Why is that folder not there any longer? Am I missing something?

Thanks in advance

---

### Post by QDR06VV9 on 2015-11-05
```
$ locate thumbnails
```

```
/home/me/.thumbnails/home/me/.cache/thumbnails
/home/me/.cache/thumbnails/normal
/home/me/.cache/thumbnails/fail
```
Me is my username
Regards

---

### Post by jooge on 2015-11-05
Thanks for the info runrickus.

---

### Post by vasa1 on 2015-11-06
Here's mine:```
10:38 AM ~ $ ls -alR | grep nail
drwx------  4 vasa1 vasa1  4096 Sep 25 07:16 .thumbnails
drwx------ 2 vasa1 vasa1 4096 Oct 23 16:06 thumbnails
./.cache/mozilla/firefox/itjrx7ly.Testing/thumbnails:
drwx------ 2 vasa1 vasa1 4096 Jul 14 16:15 thumbnails
./.cache/mozilla/firefox/yfska9ip.Main/thumbnails:
-rw------- 1 vasa1 vasa1 29029 Jul 23  2014 thumbnail.png
./.thumbnails:
./.thumbnails/large:
./.thumbnails/large/00000000000000000000000000000000.png:
./.thumbnails/normal:
./.thumbnails/normal/00000000000000000000000000000000.png:
10:38 AM ~ $ 

```

```
10:38 AM ~ $ uname -a
Linux vasa1-Inspiron-1545 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
10:39 AM ~ $ 

```

---

