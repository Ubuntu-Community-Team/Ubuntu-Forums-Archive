---
title: "Storing FF bookmarks on a server."
date: 2007-11-02
forum: General Help
---

### Post by Mongo5000 on 2007-11-02
Okay, i'll explain a bit more since even I didn't understand my topic.

I have a networked storage server that I use as just as storage.  What I want to do is store my firefox bookmarks on my server and have all my client computers use that bookmark store automatically.  So when im on my desktop, I add a couple bookmarks but then when I go to my laptop, it pulls from the same bookmark.html file and its exactly the same.

Suggestions?

---

### Post by lolindrath on 2007-11-02
There's a great plugin called Foxmarks that I use to sync my bookmarks between my work computers and home computers, I think it would work for what you'd like to do.

---

### Post by bingoUV on 2007-11-02
There are great extensions for firefox for such things, browse the bookmarks section of firefox extensions. They mostly store your bookmarks somewhere on the internet. There is also the google toolbar which does this ([http://www.google.com/tools/firefox/toolbar/](http://www.google.com/tools/firefox/toolbar/)) and much more.

If you want to store the bookmarks.html locally for some reason, symlink it from both the laptop and the desktop to the same location. The below mentioned command are not to be run directly, but an example.

If storage server is mounted on /media/storage/, do the following in the profile directory 
```

mv  bookmarks.html /media/storage/firefoxBookmarks
ln -s /media/storage/firefoxBookmarks/bookmarks.html

```

---

### Post by Mongo5000 on 2007-11-02
good stuff, thanks guys!

---

