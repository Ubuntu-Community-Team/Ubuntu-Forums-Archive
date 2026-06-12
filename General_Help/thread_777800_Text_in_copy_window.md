---
title: "Text in copy window"
date: 2008-05-01
forum: General Help
---

### Post by macafyc on 2008-05-01
Hi all

After upgrading from Gutsy to Hardy when I copy or move files I can't see neither the file name nor the destination folder in system window

Any idea?

Thanks

---

### Post by retrow on 2008-05-01
Perhaps the fonts used to display the filenames are missing.
Try:
```
sudo apt-get install msttcorefonts
```
If your default fonts are 'sans' and 'monospace' then the above package should have you covered.

---

### Post by macafyc on 2008-05-01
Thank you for answering.

Yes, I have sans and monospace as default fonts and msttcorefonts installed, so that's not the problem.

---

