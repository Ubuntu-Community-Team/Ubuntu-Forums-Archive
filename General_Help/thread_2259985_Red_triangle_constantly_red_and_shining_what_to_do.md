---
title: "Red triangle constantly red and shining what to do?"
date: 2015-01-08
forum: General Help
---

### Post by petermartin2 on 2015-01-08
When I check for updates through the triangle I get the message that the system is fully updated but when I run 

sudo apt-get update

I get some error messages:

```
W: Failed to fetch http://download.videolan.org/pub/debian/stable/en_US  Bad header line       

W: Failed to fetch http://download.videolan.org/pub/debian/stable/en  Bad header line

W: Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I've run sudo apt-get update and sudo apt-get upgrade several times but still getting them, what could be wrong?

---

### Post by deadflowr on 2015-01-08
Open Software and Updates, go to Other Software and disable(uncheck) the entries for videolan and unity-tweak-tool.
(I do not know the status of videolan, but the unity-tweak-tool has no ppa for utopic.)
Then close the window and reload the software updater, if it doesn't when you close software and updates.

---

### Post by petermartin2 on 2015-01-08
> **deadflowr said:**
> Open Software and Updates, go to Other Software and disable(uncheck) the entries for videolan and unity-tweak-tool.
(I do not know the status of videolan, but the unity-tweak-tool has no ppa for utopic.)
Then close the window and reload the software updater, if it doesn't when you close software and updates.

I've done what you asked, now it looks like this:
```
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

But triangle is gone! Thanks for the help!

---

