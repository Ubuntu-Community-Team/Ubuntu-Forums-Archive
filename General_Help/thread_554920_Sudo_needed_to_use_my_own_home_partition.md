---
title: "Sudo needed to use my own home partition?"
date: 2007-09-19
forum: General Help
---

### Post by hoboken on 2007-09-19
I recently did a fresh install of Ubuntu, with the usual partition system - the filesystem and the home partitions seperately. I tried copying something into my home partition and it tells me that I don't have permission to write to it... A quick check of the properties informed me that the permissions for that partition are SUDO.

I don't want to have to sudo nautilus into a terminal every time I need to use my home partition. Any solutions?

---

### Post by mocoloco on 2007-09-19
Love the avatar!  I spent some much time playing Commander Keen back in the day....

When you say permissions to your home partition, I assume you mean to the /home folder?  Your user should only have full permissions to your folder inside /home.  When you re-installed, if you set up the same username that you had before the installer should have automatically given you all the permissions (works that way for me).  If that didn't happen, or if you used a different username, you can just set the permissions yourself.
In a terminal open /home and do ls -l.  If your user's folder doesn't have your name by it twice you need to set yourself as the owner and group for your folder.
```
sudo chown -R <youruser> <youruser>
```

Hope that makes sense.

---

### Post by mysticmatrix on 2007-09-19
> **hoboken said:**
> I recently did a fresh install of Ubuntu, with the usual partition system - the filesystem and the home partitions seperately. I tried copying something into my home partition and it tells me that I don't have permission to write to it... A quick check of the properties informed me that the permissions for that partition are SUDO.

I don't want to have to sudo nautilus into a terminal every time I need to use my home partition. Any solutions?

Well /home would still be under root. You can use /home/<username> to store all your data. It is good idea to keep /hpme under root, as it might be used to store folders for other users too.

If you are hell bent over actually using /home, do
```

gksudo nautilus
```

Select /home directory, right click it and change owner from root to your username

---

### Post by hoboken on 2007-09-19
Hmm, no, something different is going on. In nautilus, on the left side where all my partitions should be appearing I only see one: Filesystem. Yet, on my desktop, I have two icons, sda2 (windows) and sda3 (where I want to store my junk). The problem is I have no idea how to navigate to these places using nautilus or the command line. It's not under root (the partition named "filesystem") even though filesystem has its own /home/myname folder - it's a seperate partition I'm talking about here.

Thanks for the replies. Mocoloco, I wish I could get a hold of the keen games now... There were always ads hanging around for this über-cool sequel (baby-sitter from mars? something like that) which I never got to play, heh.

---

### Post by mocoloco on 2007-09-19
OK, now I get it.  Your home partition won't show up on the left.  It's a separate partition, but it's mounted under the file system.  Actually so are you other drives, they're mounted under /media.  It's just that nautilus shows you all mounted media, including those not "integrated" as part of the main file system like those two windows partitions, and any USB drives, etc.
If you can access your own home folder you're good to go.  One place you can see your file system and mount points is the system monitor (System -> Administration -> System Monitor).  Last tab.

---

### Post by hoboken on 2007-09-21
OK, that's cool, but it doesn't solve my problem. I can explore the contents of the empty partition from the icon on the desktop, too, but what I'm interested in is first of all, being able to access it through the nautilus file explorer thing, and secondly, knowing the command line path to it so that I can give myself sudo permissions and write my files in there.

edit: sorry for not looking hard enough. It's under /media/sda3. Thanks!

---

