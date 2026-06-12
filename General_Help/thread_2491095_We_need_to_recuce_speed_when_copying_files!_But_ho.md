---
title: "We need to recuce speed when copying files! But how!?"
date: 2023-09-26
forum: General Help
---

### Post by civilpolisen on 2023-09-26
We are going to copy a great deal of data from the clients live server. While doing so, using cp -R command, the server slow down quite a bit.
Wither we copy these files after 5 PM, after office hours, or we copy during the day at a lower speed, so that people may use the server without anoying delays...!

So! The question is! How do we slow down the file copy command?

---

### Post by ActionParsnip on 2023-09-26
Use the rsync command. You can set the speed it should copy at
[https://www.cyberciti.biz/faq/how-to-set-keep-rsync-from-using-all-your-bandwidth-on-linux-unix/](https://www.cyberciti.biz/faq/how-to-set-keep-rsync-from-using-all-your-bandwidth-on-linux-unix/)

---

