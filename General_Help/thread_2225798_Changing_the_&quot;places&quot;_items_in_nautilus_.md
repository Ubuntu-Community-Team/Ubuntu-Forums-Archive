---
title: "Changing the &quot;places&quot; items in nautilus for Ubuntu 14.04"
date: 2014-05-23
forum: General Help
---

### Post by hojjat on 2014-05-23
The Places menu in Ubuntu 14.04 is very long by default (contains 9 items by deafult), and after that comes Devices, and then Bookmarks. This kind of refutes the purpose of bookmarks (you want them to be handy, not burried below lots of other things).

Is there any way to (a) remove some of the items from the "Places" menu, or (b) move Bookmarks to the top or at least above Devices?

---

### Post by mikeyinid on 2014-05-26
> **hojjat said:**
> The Places menu in Ubuntu 14.04 is very long by default (contains 9 items by deafult), and after that comes Devices, and then Bookmarks. This kind of refutes the purpose of bookmarks (you want them to be handy, not burried below lots of other things).

Is there any way to (a) remove some of the items from the "Places" menu, or (b) move Bookmarks to the top or at least above Devices?

This is what worked for me~~~> [http://choorucode.com/2010/07/25/how-to-add-or-remove-places-entries-in-nautilus/](http://choorucode.com/2010/07/25/how-to-add-or-remove-places-entries-in-nautilus/)

---

### Post by hojjat on 2014-05-27
Thanks. I added *enabled=False* to the begining of ~/.config/user-dirs.dirs and commented out the items I didn't want to see, and I also commented them out in /etc/xdg/user-dirs.defaults

Then ran *nautilus -q* and it was all set!

---

