---
title: "unreadable fonts in skype"
date: 2008-04-04
forum: General Help
---

### Post by mawdryn on 2008-04-04
Hi,

I just installed skype from the medibuntu respository, and I can't read a single word. I had skype installed in Gutsy and it was ok, but now in Hardy, I get this.

This problem does not occur in any other app or in Gnome.

Could anyone please shed some light on the problem, thanks.

Image attached.

---

### Post by TeoBigusGeekus on 2008-04-04
Just a suggestion:
Go to your home folder and delete the hidden .skype folder. Then open Skype and it will try to reconfigure itself. Perhaps you'll be lucky...

---

### Post by mawdryn on 2008-04-04
Hi Teo,

Thanks for the suggestion, however it did not work for me.

On closer inspection, the fonts look similar to that used by LaTex, however I don't have LaTex installed currently, although it was once. 

I inspected my .fonts folder and found quite a few bizarre fonts that didn't event look like letters, so I removed them and did "sudo fc-cache -f -v" which seems to have resolved the issue.

---

### Post by kostkon on 2008-04-04
If you would like to get an update every time there is a new version of *Skype*, you could use its official repository for *Debian* and *Ubuntu*:
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

---

