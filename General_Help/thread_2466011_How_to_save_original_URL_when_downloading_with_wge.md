---
title: "How to save original URL when downloading with wget?"
date: 2021-08-17
forum: General Help
---

### Post by sofasurfer on 2021-08-17
I'm using wget to download pdf pages ```
 $ wget -r <source url> 
```. How can I get wget to also save the original URL for future reference?

---

### Post by TheFu on 2021-08-17
```
#!/bin/bash
URL="https://some.place.net/deep/place/for/url"
wget -r "$URL"
touch "URL"
```

The manpage for wget has more options like -x or --protocol-directories or use -alog.   The wget manpage is quite impressive.

---

### Post by dragonfly41 on 2021-08-17
Another option is to install [Zotero]("https://www.zotero.org/") as a manager (standalone app plus browser extension).
This downloads PDF documents, and saves data including url's, notes, etc.
Used by librarians.

---

