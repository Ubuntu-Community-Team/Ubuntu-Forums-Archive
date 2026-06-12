---
title: "FF3b5 Bookmkarks location?"
date: 2008-05-01
forum: General Help
---

### Post by Sak on 2008-05-01
I know this question is strange.  I don't want to believe I'm asking it myself, but is there some mysterious new location for FF3b5 bookmarks?

I did a fresh install of 8.04 last night, because I wanted to repartition, and now I'm trying to recover my bookmarks file from my backup and FF3b5 just isn't reading them.

/home/sak/.mozilla/firefox/*.default/bookmarks.html

...is the file.  I've double and triple checked the permissions...

chmod 744 bookmarks.html

I've completely deleted the "firefox" folder and tried again.  The file is there, and it's the right file, when I open it in the browser it lists all my bookmarks, but none of them show up in the Bookmarks menu or the bookmarks bar in the browser proper, it keeps just showing the default bookmarks.

Any suggestions would be fantastic!

---

### Post by Ramses de Norre on 2008-05-01
Try File > Bookmarks > Organize Bookmarks > Import and Backup button > From File

---

### Post by chrisccoulson on 2008-05-01
FYI, Firefox 3 doesn't use a bookmarks.html file anymore. It uses a sqlite backend for storing bookmarks

---

### Post by Sak on 2008-05-01
Thanks guys, that did it.  Leave it to me to ignore the GUI and go for the old fashioned way of doing things.

---

