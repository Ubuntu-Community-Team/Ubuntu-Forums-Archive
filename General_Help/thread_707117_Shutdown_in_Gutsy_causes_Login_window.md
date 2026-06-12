---
title: "Shutdown in Gutsy causes Login window"
date: 2008-02-25
forum: General Help
---

### Post by Kyairan on 2008-02-25
Morning,

When I goto shutdown Gutsy, it now has the habit of reloading the 'Login Window' with the 'Happy Gnome' theme briefly before the system shuts down properly. My normal Login Window has Human as the theme. Any ideas why this has started happening?

Thanks.

---

### Post by Zeroangel on 2008-02-25
Try running the command
```
sudo dpkg-reconfigure gdm
```
And see if that does the trick for ya.

---

### Post by Kyairan on 2008-02-25
You are a gentleman and a scholar sir, I think that might have done it.

Thanks.

---

