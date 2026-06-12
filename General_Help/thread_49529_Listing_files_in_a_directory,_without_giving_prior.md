---
title: "Listing files in a directory, without giving priority to capitalization."
date: 2005-07-16
forum: General Help
---

### Post by Trickyphillips on 2005-07-16
I need to list the files in a directory, ignoring capitalization in the way that files are ordered. It doesn't look like ls has this feature, so I think I'll have to turn to a shell script, or such. 

Can anyone point me in the right direction?

Thanks.

---

### Post by evilghost on 2005-07-16
Will *ls -la|awk '{print $8}'* give you what you're looking for?

---

### Post by Trickyphillips on 2005-07-17
[QUOTE=evilghost]Will *ls -la|awk '{print $8}'* give you what you're looking for?[/QUOTE]
 *ls -la|awk '{print $9}'* printed the list of files, but still gave priority to items with capitalization. :(

---

