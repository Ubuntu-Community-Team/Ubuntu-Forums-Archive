---
title: "synce &amp; gnomevfs"
date: 2005-05-07
forum: General Help
---

### Post by animacide on 2005-05-07
I've been trying to get the gnome-vfs plugin to work for synce, but whenever I try to enter a synce:/// type url into nautilus, it says: synce:/// is not a valid location.  I installed the gnome-vfs support by downloading the source tarball from synce's sourceforge site, and it compiled and installed properly.  I also know that synce itself is working, and I even got the gnome tray icon to work (except when I try to use it browse).  The only other problem I have is that the hotplug script doesn't work properly.  If I run the script from the command line, it works fine.  But when the hotplug daemon runs it, the script does apparently nothing.  In the /var/log/synce there is just a mention of "ipaq added", but no output from the synce-serial-start command itself.  Thanks for any help you can give me.

---

### Post by roboguy on 2005-06-12
Hi there,

You can find the answers to your questions in my post here:
[http://www.ubuntuforums.org/showthread.php?p=209736#post209736](http://www.ubuntuforums.org/showthread.php?p=209736#post209736)

Cheers,
Roboguy

---

### Post by easy_target on 2005-07-13
How did you get the hotplug script to work? I followed the instructions on the fixes page and when I run the script from the command line I get the following output:

```
synce: line 24: $REMOVER: ambiguous redirect
chmod: too few arguments
Try `chmod --help' for more information.
```

What is wrong?

---

