---
title: "Does ktorrent keep running when you close its window?"
date: 2023-01-01
forum: General Help
---

### Post by raphaell2 on 2023-01-01
Although I'm generally not a Kubuntu user (I use Ubuntu Mate myself) I recently installed ktorrent because I got frustrated with some aspects of Transmission. Shortly ago, while I was seeding, I closed the ktorrent window, and, a while later, opened ktorrent again. When I opened it again, I saw that it was apparently already uploading stuff, as if it had done that while the window was closed. *Does* it run while it has no window open? And if so, what can I do about that?

---

### Post by howefield on 2023-01-01
After closing try running

```
ps aux | grep ktorrent
```

Still running ?

Then use the file menu option to quit rather than the window close button.

---

