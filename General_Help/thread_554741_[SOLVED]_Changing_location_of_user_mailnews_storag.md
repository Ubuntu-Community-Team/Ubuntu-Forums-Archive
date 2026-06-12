---
title: "[SOLVED] Changing location of user mail/news storage folders in Evolution, Pan"
date: 2007-09-19
forum: General Help
---

### Post by StewartM on 2007-09-19
Hi,

I'm now trying out Evolution (for mail) and Pan (for usenet).

One of the things that I'd like to do is to replicate what I had on my old Windows box, where all private usage data got stored by default on an encrypted volume. With Firefox, it was trivial to create user profiles and to direct them to an encrypted container mount point on my new Feisty box. Problem there easily solved. :)

On my defunct Windows box, I was using Pegasus Mail, and Xnews, for email and usenet. It was trivial to have these likewise to direct all user data to a specified directory. I could continue to run these under WINE (I tried Xnews and it runs reasonably well, though it's a little buggy; Pegasus Mail is listed on WINE's site as being tested and runnable too) and do what I want. But if possible I'd like to start using the GNU/Linux equivalents. To do that with Ubuntu's defaults, I need to be able to change where the Evolution and Pan store user data.

If Evolution and Pan does not allow user choice on where to store downloaded mail and news, is there another GNU/Linux mail or news app that any of you would care to suggest that does?

Stewart

---

### Post by dcstar on 2007-09-20
> **StewartM said:**
> Hi,

I'm now trying out Evolution (for mail) and Pan (for usenet).

One of the things that I'd like to do is to replicate what I had on my old Windows box, where all private usage data got stored by default on an encrypted volume. With Firefox, it was trivial to create user profiles and to direct them to an encrypted container mount point on my new Feisty box. Problem there easily solved. :)

On my defunct Windows box, I was using Pegasus Mail, and Xnews, for email and usenet. It was trivial to have these likewise to direct all user data to a specified directory. I could continue to run these under WINE (I tried Xnews and it runs reasonably well, though it's a little buggy; Pegasus Mail is listed on WINE's site as being tested and runnable too) and do what I want. But if possible I'd like to start using the GNU/Linux equivalents. To do that with Ubuntu's defaults, I need to be able to change where the Evolution and Pan store user data.

If Evolution and Pan does not allow user choice on where to store downloaded mail and news, is there another GNU/Linux mail or news app that any of you would care to suggest that does?

Stewart

Simply replace the current .evolution and .pan directories with links to wherever you want (and copy their contents to the new locations before you do it!)

---

### Post by StewartM on 2007-09-20
> **dcstar said:**
> Simply replace the current .evolution and .pan directories with links to wherever you want (and copy their contents to the new locations before you do it!)

Duh! Thanks! I'll try that and let you know how it goes. A solution that will work not only for Pan and Evolution, but for any other GNU/Linux app. Much appreciated.

Mind you, I'm careful to open my encrypted volumes the very first thing after I log on (it's a habit for me) so I know not to start Pan or Evolution until the links work.

Stewart

---

### Post by StewartM on 2007-09-20
> **dcstar said:**
> Simply replace the current .evolution and .pan directories with links to wherever you want (and copy their contents to the new locations before you do it!)

BTW, before I try it, does the file format of the encrypted container matter? It didn't matter with Firefox, it used a vfat container.

The reason why is that if I directly copy the .evolution and .pan directories to a vfat container, would it fail to understand the differences in "/" (linux) and "\" (vfat), as well as the use of a "." (for hidden) folders? I could change the folder names, but of course the Evolution and Pan will be looking for a folder.

It's not a problem, I could just create a special encrypted volume using ext3 for such work. But it would be nice to have confirmation beforehand.

Stewart

---

### Post by dcstar on 2007-09-20
> **StewartM said:**
> BTW, before I try it, does the file format of the encrypted container matter? It didn't matter with Firefox, it used a vfat container.

The reason why is that if I directly copy the .evolution and .pan directories to a vfat container, would it fail to understand the differences in "/" (linux) and "\" (vfat), as well as the use of a "." (for hidden) folders? I could change the folder names, but of course the Evolution and Pan will be looking for a folder.

It's not a problem, I could just create a special encrypted volume using ext3 for such work. But it would be nice to have confirmation beforehand.

Stewart

VFAT will not preserve permissions, so there may well be issues, the "." shouldn't be an issue as that is used by Linux in your link (the destination name can be any valid filename), and "/" "\" are also used by the operating system, not the filesystem.

---

### Post by StewartM on 2007-09-24
> **dcstar said:**
> VFAT will not preserve permissions, so there may well be issues, the "." shouldn't be an issue as that is used by Linux in your link (the destination name can be any valid filename), and "/" "\" are also used by the operating system, not the filesystem.

Well, I found out that after I copied the Evolution and Pan folders to a vfat container, when I tried to "make link" GNOME returned an error message and wouldn't allow it.

Then I created an ext3 container, and "make link" worked just dandy. I copied not only my Evolution and Pan folders to it, but also several others. It almost allows one to create something close to an encrypted home folder (albeit I know the .gnome and other directories can't be put into it). These links break when I close the containers, so I know it's working properly.

I'll mark this query as "closed". Once again, Linux provides a very simple solution for one of my needs. :popcorn:

Stewart

---

