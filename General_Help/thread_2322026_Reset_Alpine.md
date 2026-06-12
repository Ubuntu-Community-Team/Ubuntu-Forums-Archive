---
title: "Reset Alpine"
date: 2016-04-25
forum: General Help
---

### Post by Charlotte18 on 2016-04-25
I set up alpine for e-mail, but I don't like the way I set it up and want to start over. How do I delete my alpine preferences and mailboxes, or how do I reset alpine so that it's as if I never used it in the first place?

---

### Post by howefield on 2016-04-26
Delete or rename (if you want to keep for possible future reference and use) the file .pinerc which you should find in your home folder, eg

```
mv ~/.pinerc ~/Documents
```

to move it to your Documents folder and pine will start afresh.

Or I guess you could simply edit the file to your liking :)

---

