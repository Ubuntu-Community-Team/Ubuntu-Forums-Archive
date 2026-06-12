---
title: "[SOLVED] 1st attempt at dual boot (ubuntu/fedora)"
date: 2008-04-21
forum: General Help
---

### Post by mandrill on 2008-04-21
It took me forever, but I finally got what I wanted - Ubuntu as primary system, Fedora in the background. Then I noticed that I had an extra disk mounting on my fedora desktop - /media/sda1....(this is a gateway e4600 p4 1.8 80gb primary 300gb slave). everything (surprisingly was working ok, (except for fedora's wireless) but now I have the root of fedora mounting itself as an extra volume on my fedora desktop. I am not jumping ship from Ubuntu - especially after trying a lot of the other distros, this is just something to play around with, but I'm afraid I'm off to a bad start. Any help on this would be appreciated, and both are fresh installs, so.....I'm losing nothing but time.......thanks in advance for any help.

---

### Post by bingoUV on 2008-04-21
[B]but now I have the root of fedora mounting itself as an extra volume on my fedora desktop

[/B]I assume this is your problem. Could you describe it more clearly? What do you mean by the root of fedora? Fedora is in a habit of showing shortcuts to all the volumes on the desktop. Do you not like that?

To remove the links to mounted volumes in from desktop, open gconf-editor. Now uncheck  volumes_visible in /apps/nautilus/desktop.

---

### Post by mandrill on 2008-04-21
> **bingoUV said:**
> [B]but now I have the root of fedora mounting itself as an extra volume on my fedora desktop

[/B]I assume this is your problem. Could you describe it more clearly? What do you mean by the root of fedora? Fedora is in a habit of showing shortcuts to all the volumes on the desktop. Do you not like that?

To remove the links to mounted volumes in from desktop, open gconf-editor. Now uncheck  volumes_visible in /apps/nautilus/desktop.

NO. The actual fedora file system is being mounted from "media" - attached is a screenshot
of my gparted ......

---

### Post by bingoUV on 2008-04-22
It is still not clear what you mean by **the root of fedora desktop**. 

You also said **I had an extra disk mounting on my fedora desktop - /media/sda1** . The screenshot looks like you are running ubuntu, not fedora (deduced just from the background, I assume nobody will replace the beautiful default background of fedora by ubuntu's). But you have not mentioned any details pertaining to this too. Please state your problem clearly or it will be lost in the deluge of posts.

Nothing is obviously wrong with the gparted screenshot.

---

### Post by mandrill on 2008-04-22
> **bingoUV said:**
> It is still not clear what you mean by **the root of fedora desktop**. 

You also said **I had an extra disk mounting on my fedora desktop - /media/sda1** . The screenshot looks like you are running ubuntu, not fedora (deduced just from the background, I assume nobody will replace the beautiful default background of fedora by ubuntu's). But you have not mentioned any details pertaining to this too. Please state your problem clearly or it will be lost in the deluge of posts.

Nothing is obviously wrong with the gparted screenshot.

Must have been fool's luck to get it as far as I did, but what was happening was a portion of fedora (root, I think) was mounting from the /media mount point, and a placing a drive icon on my fedora desktop. If it wants to place a drive icon for the 300gb slave, no problem......

---

### Post by danwood76 on 2008-04-22
The drive mounted on your desktop is sdb1, your second drive.
Its impossible for it to mount 1 partition in 2 places, it just wont do it.

---

