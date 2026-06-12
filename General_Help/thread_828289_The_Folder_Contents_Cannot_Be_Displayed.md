---
title: "The Folder Contents Cannot Be Displayed"
date: 2008-06-13
forum: General Help
---

### Post by GSZX1337 on 2008-06-13
I've been using Ubuntu 7.20 since about December (afraid to upgrade to 8.04 :P) and just recently (since about the middle of May) I keep getting this error "The Folder Contents Cannot Be Displayed." Whenever I get this error, I exit the file browser and try to open up home again. No dice, nothing comes up when I click on Home, Pictures, Music, etc. The only way I can get the problem temporarily fixed is to Ctrl-Alt-BackSpace it. The problems seems to be happening quicker and quicker. Now, I'll use the file browser for about two or three hours and I'll get the error. It used to be about a day before I get the error.

Any help is appreciated.
~GSZX1337

---

### Post by Ub1476 on 2008-06-13
Maybe it helps troubleshooting if you run Nautilus (filebrowser) via the terminal

```
nautilus
```

Then you can see if it gives you some more detailed feedback about the issue.

---

### Post by GSZX1337 on 2008-06-13
I'll try that when I get the problem again.

---

### Post by GSZX1337 on 2008-06-13
When typing the command into the terminal, it just hangs.

---

### Post by TeoBigusGeekus on 2008-06-13
Go to the folder ~/.nautilus and delete everything in there.
If that doesn't solve your problem, then the next step would be to completely uninstall nautilus and reinstall it...

---

