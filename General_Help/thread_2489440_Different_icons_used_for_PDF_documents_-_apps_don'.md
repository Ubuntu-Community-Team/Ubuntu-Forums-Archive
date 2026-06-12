---
title: "Different icons used for PDF documents - apps don't see"
date: 2023-07-30
forum: General Help
---

### Post by strider22 on 2023-07-30
When I create PDF files some of the show the first page as the icon and other show an Adobe icon.
I'm not worried by the icon but the fact that jpdfbookmarks does not "see" those files.

Any suggestions as to how to fix the file so that jpdbookmarks sees it?

---

### Post by Impavidus on 2023-07-31
I don't know about jpdfbookmarks. Does it show the icons itself or does it use some external tool, like the GTK file open box?

Anyway, the miniature first page can only be shown after it has been generated. This takes some time. It may not work for files larger than some treshold, files stored on some network location, if the tool has no write permission to cache the miniature or if the miniature-generator doesn't support that version of pdf. Showing miniatures can also be disabled altogether.

Is jpdfbookmarks by any change a snap package? In that case, it may be unable to open files stored outside your home directory (like aforementioned network locations).

---

