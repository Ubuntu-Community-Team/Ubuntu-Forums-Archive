---
title: "Can't sort Nautilus bookmarks"
date: 2016-04-28
forum: General Help
---

### Post by DavidS on 2016-04-28
I've just installed Ubuntu 16.04 after using 12.04 for 4 years.

Previously bookmarks in Nautilus were sorted under headings "Devices", "Bookmarks", "Computer" and "Network".

Now those heading are gone, and all the items that used to be in "Computer" appear first.  Several of these I never ever use (Videos, Music, Pictures) but they can't be deleted.

This means that my own bookmarks are way down the list and can't even be seen without scrolling unless I use a very large window.

Is there any way of getting some useful behaviour from this bookmarks list?  E.g. deleting standard items that I don't want and/or moving my own bookmarks to the top of the list.

David

---

### Post by bandjc on 2016-06-11
Annoys the heck out of me too: solutions, anybody?

---

### Post by yetimon_64 on 2016-06-12
> **bandjc said:**
> Annoys the heck out of me too: solutions, anybody?
Firstly I am on Unity 16.04 but what I have done to remove some of my bookmarks should also work with gnome. For items you don't want (Videos, Music, Pictures) go the file ~/.config/user-dirs.dirs and comment out any you don't want, save the file and you will note they have moved to the lower section of the bookmarks pane. That is because they are also listed in ~/.config/gtk-3.0/bookmarks. Delete any entries you want totally gone in the file ~/.config/gtk-3.0/bookmarks. 

One thing you should note are the comments at the top of the file ~/.config/user-dirs.dirs
> This file is written by xdg-user-dirs-update

Which means your changes are only temporary until the next log in or reboot. To make them permanent run the next code box in terminal ...
```
<snipped>
``` **Edit:** [U][I]See next post by CantankRus, that is the proper way to stop the process and it works here (after a restart) now without the "rough hack" aspect.
[/I][/U]
Doing this will stop the xdg-user-dirs-update process from undoing your changes even after the next log in/reboot.

To revert back to a standard install if needed ...
```
<snipped>
```
I can add or rename bookmarks normally with only the desktop bookmark still unchanged (despite also being manually removed from the 2 files and with xdg-user-dirs-update rendered unusable). 
This works on Unity 16.04 it should also work on Gnome but I have never tested it on such an install. [s]If ever the xdg-user-dirs-update application is updated I'll probably have to do the same proceedure of removing its executable bit with the above code box again, so this could be regarded as a rough "hack" to remove the bookmarks.[/s] **Edit:**changed method as per next post now. See attached screenshot (this is taken after a reboot)...

---

### Post by CantankRus on 2016-06-12
Another method would be to edit **/etc/xdg/user-dirs.conf** rather than changing permissions.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12453357&postcount=12").

You may want to look at using Nemo as your file manager which in my opinion 
is better because of the features removed from Nautilus.

---

### Post by yetimon_64 on 2016-06-12
> **CantankRus said:**
> Another method would be to edit **/etc/xdg/user-dirs.conf** rather than changing permissions.
See [**_[COLOR=#B22222]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12453357&postcount=12").

Thanks CantankRus, that is a much better idea. I'll change to that myself. Cheers, yeti.

---

