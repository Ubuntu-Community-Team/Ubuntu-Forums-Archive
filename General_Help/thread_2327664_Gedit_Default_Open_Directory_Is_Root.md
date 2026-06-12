---
title: "Gedit Default Open Directory Is Root"
date: 2016-06-13
forum: General Help
---

### Post by jim_deadlock on 2016-06-13
Gedit has started defaulting to root directory when opening files, this has only started happening recently and it's quite annoying. I'm NOT running it as root and I've tried reinstalling. Any suggestions?

---

### Post by vasa1 on 2016-06-13
> **jim_deadlock said:**
> Gedit has started defaulting to root directory when opening files, this has only started happening recently and it's quite annoying. I'm NOT running it as root and I've tried reinstalling. Any suggestions?

So when you press Menu > File > Open (or Ctrl+O), the root folder is displayed? Is that correct?

Reinstalling may not be enough. Did you first *sudo apt-get purge gedit* and then delete *~/.config/gedit* and then reinstall, assuming there isn't any important in that folder?

Have you tried renaming ~/.local/share/recently-used.xbel?

I went through```
gsettings list-recursively | grep gedit
```but couldn't find anything helpful :(

Maybe a screenshot of what you're seeing may give someone a clue?

---

### Post by jim_deadlock on 2016-06-13
> **vasa1 said:**
> So when you press Menu > File > Open (or Ctrl+O), the root folder is displayed? Is that correct?

Yes, exactly.

> **vasa1 said:**
> Have you tried renaming ~/.local/share/recently-used.xbel?

This is what fixed it, thanks!

---

