---
title: "/home and a new drive"
date: 2006-11-15
forum: General Help
---

### Post by lozenge on 2006-11-15
I got an 80gb drive and want to use it as my home drive.

I've copied ALL files from /home onto the new drive and I've tried to mount the drive at mount point /home but no luck.

When I log in I get a completely default profile. No settings I've changed are the same... skins are different, wallpaper is default, etc.

How can I set the 80gb as my home dir and make it properly work?

---

### Post by taurus on 2006-11-15
You need to add an entry in /etc/fstab, pointing it to the new harddrive for your /home!

---

