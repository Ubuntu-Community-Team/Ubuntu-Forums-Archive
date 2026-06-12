---
title: "[SOLVED] Help With AWN Trash"
date: 2008-05-11
forum: General Help
---

### Post by Patrick793 on 2008-05-11
I need help with the trash can on AWN. If I delete a file, it doesn't appear in the icon. The only way I can delete the files from the Trash is by opening the trash. I've tried using both Stacks Trash and Trash Applet. Neither of them work.

Could someone help me please?

---

### Post by Patrick793 on 2008-05-11
Well, I was googling about it, and I found a fix. In the terminal type

```
rmdir ~/.Trash
ln -s ~/.local/share/Trash/files ~/.Trash
```

That fixed it for me. Thing is, with Trash Applet, the window freezes at the end when removing items. This doesn't happen with Stacks Trash.

---

