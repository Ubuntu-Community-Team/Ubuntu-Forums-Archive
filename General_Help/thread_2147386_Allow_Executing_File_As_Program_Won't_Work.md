---
title: "Allow Executing File As Program Won't Work"
date: 2013-05-21
forum: General Help
---

### Post by elfin8er on 2013-05-21
Ok, so I'm trying to write an sh file as a program. I right clicked on the file, and ticked the box next to "Allow executing file as program", but it still opens with the text editor when I double click on it. I tried restarting my computer, and it still didn't work. Any suggestions?

---

### Post by Ubutea on 2013-05-21
Make sure in Nautilus-file preferences-behaviour-executable text files the selection is 'Ask each time'. Then open your sh file & choose run.

---

### Post by elfin8er on 2013-05-21
> **Ubutea said:**
> Make sure in Nautilus-file preferences-behaviour-executable text files the selection is 'Ask each time'. Then open your sh file & choose run.
Seemed promising, but it didn't work :/

---

### Post by elfin8er on 2013-05-22
I can run it by using bash in the terminal, but still can't double click on the file.

---

### Post by deadflowr on 2013-05-22
If the script isn't extremely long, you could post it, and those who know what means what could critique it and give pointers on what's right or wrong.

If you choose to post it, please use the code tags (#).

---

### Post by CatKiller on 2013-05-22
If you don't tell it to run in a terminal it will run but have no way to show you output. You may already have considered this, of course.

---

### Post by HiImTye on 2013-05-22
make the first line:
```
#!/bin/bash
```

---

