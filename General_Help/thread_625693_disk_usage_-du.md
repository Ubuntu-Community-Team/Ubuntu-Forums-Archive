---
title: "disk usage -du"
date: 2007-11-28
forum: General Help
---

### Post by DisruptiveTechnology on 2007-11-28
Hi

I have a problem trying to get the disk usage from a server. It does not return all the directories and their file size. It seems to skip what are the really large file directories. How can I rectify this. What command should I be using. I am using:

du -s -h *.*

Thanks

---

### Post by bingoUV on 2007-11-28
Is there a . in all your directory names? If not, try 
```

du -sh *

```

---

### Post by nick_h on 2007-11-28
This has already been answered - [here](http://ubuntuforums.org/showthread.php?t=625696).

Please don't post the same question in different forums.

---

