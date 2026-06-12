---
title: "How to reset lubuntu to how it was when it was orignally installed"
date: 2013-08-08
forum: General Help
---

### Post by physman2 on 2013-08-08
Okay so I am using lubuntu (xfce) and ever since I got it installed, I installed all these 'apps' and repositories and made changes and customized it and what not. How do I 'wipe' lubuntu to make it like how it was when it was first originally installed, without all the changes and installed stuff?

---

### Post by TheFu on 2013-08-08
Lubuntu runs LXDE, not xfce.  That doesn't matter to answer your question. For either Xubuntu (XFCE) or Lubuntu (LXDE), the answer is the same.

The way you reset things to how they were at initial installation is to reinstall.  Backup your settings and data first, so you can put it back if required after the fresh install.

If you put your HOME on a different partition than the OS and apps, reinstalling is really easy.  Highly recommended to do this if you haven't already.

---

### Post by vasa1 on 2013-08-08
> **TheFu said:**
> ...
The way you reset things to how they were at initial installation is to reinstall.  Backup your settings and data first, so you can put it back if required after the fresh install.

If you put your HOME on a different partition than the OS and apps, reinstalling is really easy.  Highly recommended to do this if you haven't already.
+1 to backing up the data.

While there's no harm in backing up settings, it maybe better not to use the old settings unless one is sure they aren't going to be problematic in the re-install.

My preference is to back up the settings but to customize everything afresh (and keep the old settings as hints).

Re. making a separate /home ... I've seen several recommendations to do so but I found it technically difficult to understand and not really necessary. But I guess that varies from user to user.

Even if /home isn't on a different partition, if I remember correctly, the *buntu installer offers to leave /home untouched and so the installation on systems without a separate /home isn't really more complicated.

---

### Post by physman2 on 2013-08-09
> **TheFu said:**
> Lubuntu runs LXDE, not xfce.  That doesn't matter to answer your question. For either Xubuntu (XFCE) or Lubuntu (LXDE), the answer is the same.

The way you reset things to how they were at initial installation is to reinstall.  Backup your settings and data first, so you can put it back if required after the fresh install.

If you put your HOME on a different partition than the OS and apps, reinstalling is really easy.  Highly recommended to do this if you haven't already.

Hm, okay, so the way I first installed Lubuntu was booting it from a USB, so I just do the same thing? Boot the lubuntu iso file from a CD and then that will overwrite my old OS?

---

### Post by l3dx on 2013-08-09
Like any other OS-reinstall :)

---

### Post by Netstatus on 2013-08-09
> **physman2 said:**
> Hm, okay, so the way I first installed Lubuntu was booting it from a USB, so I just do the same thing? Boot the lubuntu iso file from a CD and then that will overwrite my old OS?

You can boot it from a USB just as well as from a CD. The important thing is that within the setup you choose for the option which replaces the current os with the one you're installing.

---

### Post by TheFu on 2013-08-09
> **Netstatus said:**
> You can boot it from a USB just as well as from a CD. The important thing is that within the setup you choose for the option which replaces the current os with the one you're installing.

Before you write a new OS to any HDD, be certain you have a great backup that you know how to restore. Bad things sometimes happen. We all make mistakes and accidentally wipe partitions. If you tell the installer to reformat a partition (which might be the default), it will.  All your data will be gone. There are a few other "gotcha" type things in the installer too. 

a) Best to put your /home into a dedicated partition
b) Best to backup all files/data you don't wish to loose BEFORE you begin.

I've been installing Linux for 20 yrs - I've accidentally wiped my /home/ more times that I care to admit. Please, please, learn from my mistakes **before** it happens to you.

---

### Post by Netstatus on 2013-08-09
The suggestion of backing up important information has already been made, but it's only good to make sure it's understood.

---

