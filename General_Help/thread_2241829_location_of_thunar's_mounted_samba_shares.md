---
title: "location of thunar's mounted samba shares?"
date: 2014-08-28
forum: General Help
---

### Post by fedebaka2 on 2014-08-28
I have two systems, one xubuntu trusty and one ubuntu trusty which i stripped of unity and uinstalled xubuntu-deskto. I want to ask about both, hopefully the answer is the same.

In thunar I have no problem surfing to my windows shares by using CTRL+L, smb://something/something

but when I do that, doesn't that share get mounted by thunar at some point of my filesystem? I would like a quick way to access it via filesystem without having to mount it with mount (which i wasn't able to do yet, even if i tried lots of syntaxes). I read that thunar (or i don't know what) mounts the shares on $HOME/.gvfs, but mine's always empty.

Any clues?

Thanks!

---

### Post by TheFu on 2014-08-28
gvfs is being used, but the locations where that is placed has changed between the different releases.  Plus those mounts do not show up in the /etc/mtab, so ... you'll just have to look.

Try /var and /media/
The label of the partition should be there.

---

### Post by fedebaka2 on 2014-09-01
Well I found it! It's so far fetched!

/run/user/(my uid)/gvfs/smb-share:server=(server),share=(share)/

---

