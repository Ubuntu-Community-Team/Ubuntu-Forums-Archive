---
title: "How do I reinstall Firefox?"
date: 2007-10-25
forum: General Help
---

### Post by Exillo on 2007-10-25
I changed to a theme and it stuffed up Firefox so when I open it it looks very wrong and freezes. Unless there's a way to change the theme to something else without reinstalling how do I do it?

If I just use synaptic then I would've thought if I install it again there will still be my settings there and so the bad theme will still be selected (as well as my bookmarks which I guess I'll have to loose :( :( ). Please help. =)

---

### Post by taurus on 2007-10-25
Your bookmarks.html is in ~/.mozilla/firefox/<some random numbers and letters>.default/bookmarks.html.  Save it somewhere and delete the whole firefox (or even .mozilla) directory.

```
rm -rf ~/.mozilla/firefox
-or-
rm -rf ~/.mozilla
```
Then, restart firefox again and see what happens now.

---

### Post by Exillo on 2007-10-25
Everything's working again, thanks for the fast reply. :)

Although Firefox seems to be starting up slower than it used to which is slightly weird / frustrating.

---

