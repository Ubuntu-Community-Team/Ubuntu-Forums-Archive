---
title: "default enqueue in XMMS"
date: 2005-04-14
forum: General Help
---

### Post by Cyclonis on 2005-04-14
Does anyone know how I can get XMMS to enqueue mp3's by default whenever I click on a mp3?  Right now each time I click on a mp3, my entire list gets cleared and only the selected file will be played.

---

### Post by misterlizard on 2005-04-14
The command for enqueuing is:

    xmms --enqueue <filename>
or
    xmms -e <filename>

If you can set the action under whatever file manager you're using to include the '-e' switch it ought to queue it up instead of replacing the entire list. Are you using Gnome or KDE?

---

### Post by louisgag on 2007-04-13
how would I enqueue a file that I clicked in firefox?

---

