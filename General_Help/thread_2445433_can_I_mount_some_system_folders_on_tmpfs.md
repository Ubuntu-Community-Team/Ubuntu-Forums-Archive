---
title: "can I mount some system folders on tmpfs?"
date: 2020-06-14
forum: General Help
---

### Post by peb-cak on 2020-06-14
I wonder if it is a good idea to mount /tmp on tmpfs. How about ~/.cache?

Or is it better to use something like anything-sync-daemon for ~/.cache?
[URL="https://github.com/graysky2/anything-sync-daemonI"]https://github.com/graysky2/anything-sync-daemon
[/URL]
I appreciate your comments/suggestions.

---

### Post by ActionParsnip on 2020-06-14
I've done it with subfolders of ~/.cache like the cache folder of my browser. It means when I reboot all the fluff goes away. You'll need to make script to run at boot and so on. I just used a folder then a symlink for simplicity.

Something like this
[https://www.joeyconway.com/blog/2011/09/11/ubuntu-ssd-move-chrome-cache-to-ram/](https://www.joeyconway.com/blog/2011/09/11/ubuntu-ssd-move-chrome-cache-to-ram/)

If you have oodles of RAM then shifting storage to it rather than your comparatively slow storage (Yes, even SSD) can make systems more responsive

---

### Post by CatKiller on 2020-06-14
/tmp is already tmpfs with systemd. Mine was set up like that prior to systemd, though, as well as the log file locations as tmpfs.

---

### Post by peb-cak on 2020-06-15
> **ActionParsnip said:**
> 
[https://www.joeyconway.com/blog/2011/09/11/ubuntu-ssd-move-chrome-cache-to-ram/](https://www.joeyconway.com/blog/2011/09/11/ubuntu-ssd-move-chrome-cache-to-ram/)


Thanks for the reply and the link! So do you think if I am going to put the whole ~/.cache on tmps, can I just make an entry in fstab?

> **CatKiller said:**
> /tmp is already tmpfs with systemd. Mine was set up like that prior to systemd, though, as well as the log file locations as tmpfs.

Thanks for the reply and the clarification! 

Has any one of you any experience with anything-sync-daemon that I linked to above?

---

