---
title: "Emacs opening files"
date: 2007-01-13
forum: General Help
---

### Post by marcantonio on 2007-01-13
Hey all,

I'm having a weird issue.  I just install emacs-snapshot-gtk on edgy and it won't open any files from the command line, e.g.:

```
marc@ces01:~$ emacs /etc/passwd
```

is the same as just:

```
marc@ces01:~$ emacs
```

Really strange.  I can open files with C-x C-f though.

Any thoughts?

Thanks,
Marc

---

### Post by marcantonio on 2007-01-15
I just realized that emacs is actually opening the file, it's just not displaying that buffer.  It's displaying the intro/scratch buffer by default, but I can C-x b to the buffer containing the file I specified on the command line.

Anyone seen this before?

Thanks,
Marc

---

### Post by spwhitty on 2007-02-06
I have the same problem. I setup emacs-snapshot with anti-aliasing support via GTK/XFT. I found that when I remove any customizations in the ~/.Xresources file, Emacs behaves normally. As soon as I add the single line Emacs*Font: blah, I get this issue. Removing it and restarting X gets rid of it. Unfortunately, removing this line removes my font setting and emacs goes back to a blurry, not very readable font.

Not sure what the real solution is.

---

### Post by Scratty on 2007-03-03
I have the same issue too.

---

