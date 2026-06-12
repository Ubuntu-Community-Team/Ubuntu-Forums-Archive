---
title: "How do i view .Trash folders"
date: 2006-10-31
forum: General Help
---

### Post by L2wis on 2006-10-31
Hey all, i've been having problems with my pen drive and phone flash memory... basically:

When i delete files from them they are left on them but moved to an invisible folder called .Trash (also on the drive) However, i cannot get into this folder to delete the contents as it's totally invisible (I've tried clicking view > hidden files) but it still doesn't show them up..

I end up having to boot into windows to delete the folders which are clear as daylight as soon as i go in the directory.

---

### Post by doobit on 2006-10-31
> **L2wis said:**
> Hey all, i've been having problems with my pen drive and phone flash memory... basically:

When i delete files from them they are left on them but moved to an invisible folder called .Trash (also on the drive) However, i cannot get into this folder to delete the contents as it's totally invisible (I've tried clicking view > hidden files) but it still doesn't show them up..

I end up having to boot into windows to delete the folders which are clear as daylight as soon as i go in the directory.

I'm not sure why you can't see them with the file manager, but you can see them in a terminal with ```
ls -a 
```
The ls lists files and directories in a directory and the -a switch lists all, even the invisible ones.
then to delete them you type rm and the path to the file.

---

### Post by L2wis on 2006-10-31
hey m8, thxs for a well speedy response!!! I just got linked to a solution by a friend here for anyone else with this problem :)

[http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/]("here")

---

### Post by hotani on 2006-10-31
I [started a thread](http://ubuntuforums.org/showthread.php?t=289743) commenting on this issue earlier. There are ways around it, but they are hacks and/or involve the CLI which I believe is against the goal of Ubuntu.

Probably the best workaround is to enable the 'Delete' option in your right-click menu by going to (in a Nautilus window) Edit -> Preferences -> Behavior, then check the "Include a delete command that bypasses trash". This will solve the problem by not sending anything to the trash, but is still just a workaround.

EDIT: now that I've gone and looked at the wordpress article you posted I see it is exactly the same fix. Oh well, here it is without having to click a link. :)

---

