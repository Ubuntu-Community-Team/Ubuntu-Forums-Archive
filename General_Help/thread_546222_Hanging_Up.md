---
title: "Hanging Up"
date: 2007-09-08
forum: General Help
---

### Post by dougandmegan on 2007-09-08
I have installed Wubi, but it will not boot.  It just hangs on the Ubuntu title screen.  There is nothing I can point to that would be making this happen.

---

### Post by minhmeoke on 2007-09-09
Can you try pressing Ctrl + Alt + f2 when Ubuntu starts booting in order to go into text-based boot? Post the messages that are displayed right before the computer hangs.

Also, try pressing Ctrl + Alt + f1 when the booting sequence freezes. If this brings you to a shell (command prompt), then please post the contents of the logs by entering the following commands:
```
more /tmp/zenigata.log
more /tmp/lupin.log
```

---

