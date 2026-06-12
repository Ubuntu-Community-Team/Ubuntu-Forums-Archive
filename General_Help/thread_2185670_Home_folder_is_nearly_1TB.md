---
title: "Home folder is nearly 1TB"
date: 2013-11-03
forum: General Help
---

### Post by mark.michelotti on 2013-11-03
My disk space was running out, so I looked at my home folder and du shows most files taking up normal amounts of space ... except oddly the '.' or current folder specifier showed 891200744 bytes, nearly 1TB!  What's happening?

---

### Post by drmrgd on 2013-11-03
That's a bit strange.  What do you get if you run this from your home directory:

```

du -hsx * | sort -rh | head -10

```

That should show you the 10 largest files in your home directory, which might help you detect if you overlooked something previously.

---

### Post by XBNCPRk on 2013-11-03
Do you have any symbolic links to a media folder inside your home folder? Unless Im mistaken, linux and win both will count the size of the linked file as well, even if it doesnt actually reside there. 

Possibility 2) backups from dejadup or some other?

---

