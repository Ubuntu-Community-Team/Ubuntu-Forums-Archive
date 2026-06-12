---
title: "rollback deb package?"
date: 2008-01-03
forum: General Help
---

### Post by Hawk__0 on 2008-01-03
Is it possible to roll back a deb package?
I had skype 100% working with v1.4, then i installed the beta, cuz i wanted web cam, but 2.0 breaks my cam until i restart... so i want to roll back.  I have both .deb packages sitting on my desktop.  is this possible?

---

### Post by sumguy231 on 2008-01-03
Since you didn't install Skype 2.0 from the repositories, you can just uninstall the 2.0 package and then install the 1.4 package and it shouldn't bug you about it.

---

### Post by Hawk__0 on 2008-01-03
how do i uninstall the deb package? If i open it, it just gives the option of reinstalling it

---

### Post by RC Howe on 2008-01-03
```
dpkg -r *package_name*
```
I think.

---

### Post by Hawk__0 on 2008-01-03
thanks, ill remember that for next time.  This time i just went into synaptic and marked for removal, then it allowed me to install the 1.4 skype again.

anyone happen to have gotten the logitech quickcam pro 5000 working with skype 2 by any chance?

The cam works with cheese.  but not camora or whatever it is

---

