---
title: "Remove username from login screen"
date: 2013-01-24
forum: General Help
---

### Post by alphaamanitin on 2013-01-24
How do I remove the user name lists from the login screens in Xubuntu 12.04?  I don't think it is the same as the way for Ubuntu, and that is all I can find.  

Gracias,

AlphaA

---

### Post by omeomi on 2013-01-24
This doesn't work?

Edit /etc/lightdm/lightdm.conf

add the following two lines to the [SeatDefaults] section:

```
greeter-hide-users=true 
allow-guest=false
```

You then need to restart lightdm: ```
sudo restart lightdm
```

---

### Post by alphaamanitin on 2013-01-24
That worked thanks.  I just wasn't sure the commands and the like would be the same and didn't want to mess anything up.

AlphaA

---

### Post by dannyboy79 on 2013-01-24
> **alphaamanitin said:**
> That worked thanks.  I just wasn't sure the commands and the like would be the same and didn't want to mess anything up.

AlphaA

use the thread tools and mark it solved so others can benefit. :p

---

### Post by alphaamanitin on 2013-01-24
Thought I had, but I think I'll mark it as unsolved.  How to remove it from the screen saver lock?  I just use the default Xubuntu AMD64 12.04 LTS fyi.

AlphaA

---

