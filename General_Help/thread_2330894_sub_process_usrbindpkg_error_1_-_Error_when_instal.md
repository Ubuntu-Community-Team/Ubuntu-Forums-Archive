---
title: "sub process /usr/bin/dpkg error 1 - Error when installing Splashtop"
date: 2016-07-16
forum: General Help
---

### Post by Pandee on 2016-07-16
I'm trying to install Splashtop and i get the following error - sub process /usr/bin/dpkg error 1

The picture i provided is of the full error. 

[https://dl.dropboxusercontent.com/u/74122999/ubunutu.png](https://dl.dropboxusercontent.com/u/74122999/ubunutu.png)

What can i do? Or what did i do wrong?

---

### Post by T.J. on 2016-07-16
What has happened here is that the package installer for "i-nex" has failed in some way, and the package manager is giving you a warning.

You probably did nothing wrong, since "i-nex" has been known to be buggy. I have to ask: "Are you using any PPAs?"  If you don't know what those are, then probably not and you don't need to worry about the question.  If you are using a PPA (personal package archive), you can cause installers to fail.  Personal packages are not checked for bugs.  If you are using any unofficial packages, they should be removed before you proceed.


What you can try to do is correct it, is to first make sure the installer cleanly finishes any packages that are still pending.  (sudo apt-get install -f). After that I see you have updates pending.  Best to upgrade first (sudo apt-get upgrade), and then finally to try reinstalling whatever you started doing when this appeared.

If you need more information or anything at all, please ask.

---

### Post by wildmanne39 on 2016-07-16
Please use thumbnails or url's when posting!
Thanks

---

### Post by Pandee on 2016-07-17
> **Wild Man said:**
> Please use thumbnails or url's when posting!
Thanks

Ah sorry!

@T.J.

Thanks I think its working now!

---

