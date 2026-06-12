---
title: "Bookmarks and Firefox 3b5"
date: 2008-05-08
forum: General Help
---

### Post by GRETANIKOS on 2008-05-08
Where is the bookmarks.html file in Firefox 3b5? I cannot order my bookmarks with bookmark edit, they appear in a spare way. Any help?
Anyway I updated to 8.04 with my desktop, and I did a fresh install on my laptop with no problems, the only problem seems to be firefox 3b5. It has been a bad decision to include firefox 3b5 with 8.04.
Thank you.
Nikos

---

### Post by mridkash on 2008-05-08
Its right there on my 8.04 desktop. in Terminal type this command to see the folder, there you'll see the bookmarks.html

```
nautilus $HOME/.mozilla/firefox/*.default
```

---

### Post by erfahren on 2008-05-08
I tried overwriting the bookmarks.html file in ~/.mozilla/firefox/xxxxxxxx.default with my backup (as I've always done) and they wouldn't come up for me either. I finally just imported them and had to re-organize them with the bookmark manager.

> **GRETANIKOS said:**
> It has been a bad decision to include firefox 3b5 with 8.04.
Thank you.
Nikos
To be honest, I don't like it that much either.

---

### Post by GRETANIKOS on 2008-05-08
> **mridkash said:**
> Its right there on my 8.04 desktop. in Terminal type this command to see the folder, there you'll see the bookmarks.html

```
nautilus $HOME/.mozilla/firefox/*.default
```

It is not there in my case, I added some new bookmarks and the date is the same.It must be in another place, anyway I cannot order them.

---

### Post by Seti on 2008-05-08
Firefox 3 better be better than the beta is so far, or I'll be shopping for a new browser too.

---

### Post by GRETANIKOS on 2008-05-08
I installed opera and seems fine. I will wait firefox 3 final hoping it works.

---

### Post by bollix47 on 2008-05-08
The way I have sorted the main bookmarks list:

1.  ctrl-b  to open bookmarks sidebar
2.  right click on Bookmarks Menu
3.  select 'Sort By Name'

To sort the contents of any one folder just right click on the folder name in the drop-down Bookmarks menu and select 'Sort By Name'.

Seems to work fine here.

---

### Post by GRETANIKOS on 2008-05-12
> **bollix47 said:**
> The way I have sorted the main bookmarks list:

1.  ctrl-b  to open bookmarks sidebar
2.  right click on Bookmarks Menu
3.  select 'Sort By Name'

To sort the contents of any one folder just right click on the folder name in the drop-down Bookmarks menu and select 'Sort By Name'.

Seems to work fine here.


Thank you, it works fine here too, but only for the folders, not for single bookmarks outside any folder.

---

