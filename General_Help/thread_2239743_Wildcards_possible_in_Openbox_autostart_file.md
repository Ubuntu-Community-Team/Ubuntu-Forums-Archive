---
title: "Wildcards possible in Openbox autostart file?"
date: 2014-08-15
forum: General Help
---

### Post by vasa1 on 2014-08-15
I suspect it isn't possible but ...

Here's the autostart file I use for starting an Openbox session:```
xsetroot -solid "#000005"
(conky -p 5) &
(sleep 2s && tint2) &
(sleep 5s && lxpanel --profile Lubuntu) &
#(sleep 3s && nm-applet) & 
(sleep 30s && /home/vasa1/bin/cpu-usage-alert) &
(sleep 10s && /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-2.10.27/dropbox) &
(sleep 3s && /home/vasa1/bin/xclip) &
(sleep 5s && udisksctl mount -b /dev/sdb1) &
```
Of late, I've started getting automatic, silent updates of Dropbox stable. Each time that happens, Dropbox doesn't autostart because the path is now different. The variable part is the version number. For example, previously I had```
(sleep 10s && /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-**2.10.3**/dropbox) &
```which I had to change to```
(sleep 10s && /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-**2.10.27**/dropbox) &
```

---

### Post by vasa1 on 2014-08-15
Well, I found a workaround. It seems I could just use **/home/vasa1/.dropbox-dist/dropboxd**. No version numbers there!

And **/home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-2.10.*/dropbox** works from the command line. Later, I'll see if it works in the autostart file though I'll stay with **/home/vasa1/.dropbox-dist/dropboxd**.

---

