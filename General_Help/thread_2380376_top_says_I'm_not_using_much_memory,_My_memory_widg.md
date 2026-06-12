---
title: "top says I'm not using much memory, My memory widget says otherwise."
date: 2017-12-16
forum: General Help
---

### Post by nnnnnn2 on 2017-12-16
I made two screens of my results, Top claims to only use 0.16 GB but my ram widget claims I'm utilizing 6 GB of memory, So what's going on? More importantly, what's sucking all this memory???? I'm only running 1 or 2 programs (Which usually only gobbles 2 or 3 GB)...

As I can't seem to find a spoiler tag on this forum I'll simply post the [IMGUR link]("https://imgur.com/a/9KFZy") to both pictures (Big ones)

---

### Post by oldfred on 2017-12-16
You can shrink photos and attach to posts.
Easy to do with paperclip icon in Forum's advanced Editor.

 Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649)

---

### Post by nnnnnn2 on 2017-12-16
Hmm.. Thanks for the picture tip and the links. Ok so if my ram widget doesn't account for caching, is there a way to configure it to do so?

---

### Post by oldfred on 2017-12-16
No idea.

You can install htop which has a bit more info.
But top or htop would be more correct.

free also shows use:

```
fred@Asusz97:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7916        1205        3032          58        3678        6316
Swap:          4005           0        4005

```

---

