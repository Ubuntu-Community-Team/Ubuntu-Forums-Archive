---
title: "General question about Muon Software Center"
date: 2013-01-19
forum: General Help
---

### Post by circa on 2013-01-19
If I am using Muon Software Center, within location Get Software -> Games -> Arcade (or any other category(s)), and I decide to install an application, the progress indicator starts the install. If stay on the current page during the install, upon 100% completion, the focus goes completely back to "Get Software" selection category, rather than staying within the Game -> Arcade category.

I'm wondering if this is normal, a bug (I haven't found one reported yet), or if this is something that can be altered in a setting I can't locate. It's really annoying to continually go back and forth.

---

### Post by ibjsb4 on 2013-01-20
Try using apt-get and see if it gives any errors that will help trouble shoot this.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install **name-of-package**
```

---

### Post by circa on 2013-01-20
Thanks for the input ibjsb4.

I reported this as a wishlist bug, 
[https://bugs.kde.org/show_bug.cgi?id=313572](https://bugs.kde.org/show_bug.cgi?id=313572)
but unfortunately, it's a duplicate which was reported 11 months ago. This issue was fixed in Muon Software Center version 1.4, however, this version is only supported in Ubuntu 12.10. You have to manually add the unsupported PPA for LTS versions. Since this is merely a slight nuisance, I guess I'll just have to deal with it.

---

