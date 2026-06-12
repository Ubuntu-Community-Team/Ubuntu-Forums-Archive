---
title: "Where are the firefox bookmarks stored on the LiveCD?"
date: 2006-09-10
forum: General Help
---

### Post by mhancoc7 on 2006-09-10
Does anyone know where the bookmarks are stored on the LiveCD.? Also where is the default homepage for firefox stored on the LiveCD?

Thanks, Jereme

---

### Post by aysiu on 2006-09-10
I did a ```
sudo updatedb
locate bookmarks.html
``` and they appear to be in /rofs/etc/firefox/profile/bookmarks.html

---

### Post by mhancoc7 on 2006-09-10
Thanks!

I opened the bookmarks.html file in gedit and I found this.

> <!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->

Now, if I want to replace the bookmarks.html file with my own custom one when building a LiveCD will it simply be overwritten? If so how can I get the LiveCD to generate my custom bookmarks.html?

Thanks in advance, Jereme

---

### Post by orb9220 on 2006-09-10
Yes if you build custom iso you can add your own defaults like bookmarks.
But you need special software to edit iso's and create your own. You just can't get the liveCD as it is to somehow someway include your bookmarks.

---

### Post by mhancoc7 on 2006-09-10
> **orb9220 said:**
> Yes if you build custom iso you can add your own defaults like bookmarks.
But you need special software to edit iso's and create your own. You just can't get the liveCD as it is to somehow someway include your bookmarks.

Yes, I know. I am already working with [UCK]("http://uck.sourceforge.net/") to build [Ubuntu CE]("http://www.christianubuntu.com"). I just am trying to figure out where the default bookmarks and homepage for firefox are stored so I can customize them.
Thanks, Jereme

---

