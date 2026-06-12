---
title: "Deleting icon themes"
date: 2015-07-31
forum: General Help
---

### Post by fdhe5m on 2015-07-31
Hi,

I have a VM that's running Lubuntu 14.04 on which I pretty much don't ever need anything but a Firefox and a Terminal. I gave it 6 GB of space on my SSD and figured that should easily be enough. Yet, usage on my root partition shot up to like 98% of its 4 GB within barely 2 months of the VM existing.
Using du, I found out /usr/src, where I cleaned up all kernel images but the latest) to be a bad guy here, and that seems to be a common problem. Almost equally bad, however, is /usr/share/icons at a quarter of a gigabyte - the gnome and high contract themes are *huge*. And I don't need any extra themes installed, I'm fine with the default one.

But: I cannot delete them in the lxappearance / "Customize look and feel" menu, it's greyed out. Okay, they are owned by root and not by my regular user who doesn't have W rights. Trying to open lxappearance with root crashed my VM though, so that is clearly not the way.

So, my question: to *properly* get rid of these excess themes, would it be fine to just rm -rf their individual folders in the /usr/share/icons/ directory? Or how should this be approached?

---

### Post by v3.xx on 2015-07-31
/usr/share/icons/
/usr/share/themes/
and maybe in your home directory
~/.themes/ (a hidden file)

Take a snapshot and delete away :) Shouldn't be a problem.  I have done this before, without issue on ubuntu installs.  There may be some extra cleanup with Lubuntu that I am not aware of.

---

### Post by fdhe5m on 2015-07-31
Looks good so far - thanks! :)

---

### Post by v3.xx on 2015-07-31
A couple of cleanup commands
```
sudo apt-get autoclean && sudo apt-get autoremove
```
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

When you feel that this thread has been answered
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

### Post by v3.xx on 2015-07-31
An afterthought

Themes/icons not always, but may be restored with a upgrade.  A metapack can cause this.

If this happens it will be necessary to dig a little deeper into the package system, but not a concern for now, if it happens at all.

---

### Post by fdhe5m on 2015-08-01
I actually did routinely do apt-get clean and, earlier after purging all those random things like xfburn, also autoremove earlier, the package cache was actually filling up my disk much faster than in just 2 months... but eventually, it was at nearly 100% with an empty cache.
But thanks for the warning - let's give it a few days and see if anything will be restored automatically now...

---

