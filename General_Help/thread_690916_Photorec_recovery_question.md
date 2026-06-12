---
title: "Photorec recovery question"
date: 2008-02-07
forum: General Help
---

### Post by Jugney on 2008-02-07
Hi all,

This may be a really basic question (and hopefully the fix is basic). I used PhotoRec to recover a whole bunch of documents that were lost in a partition reformatting foible. 

The problem is none of them open. Nautilus shows attributes for the documents, with sizes that vary up to 2MB, indicating there should be data there. But no text editor can decode the file. Even when using nano in the terminal, the file shows up blank. 

Here's something that may be the key - for every file, there is at least one duplicate with "_1" at the end of the filename. Some have more, up to "_8" and beyond. This is true even when I only had one version of the file on my system. But none of them open in a text editor.

Any ideas?

---

### Post by pointone on 2008-02-07
Try opening with Vim; it's pretty good at handling all sorts of data types.

---

### Post by Jugney on 2008-02-08
Thanks for the tip. Does anyone have any other insight into being able to open the documents in their original format? Does anyone know why PhotoRec creates several versions of a file with the "_#" at the end of the filename?

Jugney

---

