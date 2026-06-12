---
title: "Problems with Dolphin in Kubuntu."
date: 2008-03-27
forum: General Help
---

### Post by SrEstroncio on 2008-03-27
Hello everyone I have a problem with Kubuntu ´s dolphin and I was wondering if someone could help me out.

I was installing a groupware server as part of a homework assignment and through the konsole I ran dolphin as root using:

sudo dolphin

i closed the window and then ran dolphin again from the kicker and I got this message:

Will not save configuration.
Configuration file "/home/srestroncio/.kde/share/config/kio_thumbnailrc" not writable.
Please contact your system administrator.

and when I close dolphin I get this other error:

Unable to save bookmarks in /home/srestroncio/.kde/share/apps/d3lphin/bookmarks.xmtl. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

I had this same problem a month ago before I reinstalled kubuntu and now I have it again. Any help fixing this would be greatly appreciated. Thanks in advance to everyone.

---

### Post by Ub1476 on 2008-03-27
You need to give yourself permission to those files. Remember I had the same problem on Arch with KDEmod (on D3lphin though).

```
sudo chown srestrocio /home/srestroncio/.kde/share/config/kio_thumbnail rc #I'm not sure of that space on the last line (the file which you need to have permission), you might want to check out the directory..
``` 

```
sudo chown srestrocio /home/srestroncio/.kde/share/apps/d3lphin/bookmarks.xmtl
```

In case you wonder, **chown** is the command for giving read and/or write permissions. Kinda useful if only root (sudo) somehow only has permission like in this case.

---

### Post by SrEstroncio on 2008-03-27
It worked, yay! Thank you very much kind chap. ^-^

---

