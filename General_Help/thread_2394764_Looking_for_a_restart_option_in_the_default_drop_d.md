---
title: "Looking for a restart option in the default drop down menu - Ubuntu 16.04 LTS"
date: 2018-06-20
forum: General Help
---

### Post by nomonitor on 2018-06-20
Good evening all,

I was wondering why there is no restart option below shutdown and suspend in the default GUI in 16.04.

Is there a way to add it there?

I have used the search function but I cannot find any posts related to this.

Thanks!

---

### Post by deadflowr on 2018-06-20
Restart option is part of the shutdown option.
As when you choose to shutdown the popup window that appears to actually initiate the shutdown will give an option to either shutdown or restart.
I think there is (or was) an option to add restart to the dropdown menu, but I'm not sure where it is or was.

But even if you add restart to the dropdown, it won't change the popup window, it should still show both options.

---

### Post by deadflowr on 2018-06-21
Ah! found it for you in dconf editor < needs to be installed.
it's in apps >> indicator-session
you can enable force-restart-menuitem which should add restart to the menu.
```
sudo apt install dconf-editor
``` 
will install dconf editor.


Also, you *can* also enable suppress-logout-restart-shutdown which *will* actually set it so that the dialog popup window never shows and instead it performs the requested actions without confirmation.

---

### Post by nomonitor on 2018-06-21
You ROCK!  This was exactly what I needed and it worked perfectly!


> **deadflowr said:**
> Ah! found it for you in dconf editor < needs to be installed.
it's in apps >> indicator-session
you can enable force-restart-menuitem which should add restart to the menu.
```
sudo apt install dconf-editor
``` 
will install dconf editor.


Also, you *can* also enable suppress-logout-restart-shutdown which *will* actually set it so that the dialog popup window never shows and instead it performs the requested actions without confirmation.

---

