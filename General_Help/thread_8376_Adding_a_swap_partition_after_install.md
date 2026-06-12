---
title: "Adding a swap partition after install"
date: 2004-12-16
forum: General Help
---

### Post by Cloudane on 2004-12-16
Stupidly during install, I forgot to create a swap partition.  So now I'm trying to add one.

I created a swap type partition, 1GB in cfdisk as /dev/hda3
Did mkswap /dev/hda3 and this was successful

If I type:
sudo swapon /dev/hda3

I get:
"swapon: /dev/hda3: device or resource busy"

After putting the line into /etc/fstab:
/dev/hda3  swap swap defaults 0 0

If I type:
sudo mount swap

I get:
"mount: mount point swap does not exist"

Any ideas?

---

### Post by jdong on 2004-12-16
Check **free**. Does any swap show up?

---

### Post by Cloudane on 2004-12-16
[QUOTE=jdong]Check **free**. Does any swap show up?[/QUOTE]
 Oh... er,  yes it does :P  That would explain a few things.  I guess it was ahead of me, and I didn't actually need to do anything.  Ta!

(This distro is just like OS X.  Love it.)

---

### Post by jdong on 2004-12-16
Lol, it's so automatic that sometimes it's CREEPY ;)

Like yesterday, I switched my old keyboard with an MS Internet Keybord (I got it for free.... don't blame me!), and it automatically modified XF86Config to reflect my new keyboard... I have **no idea** how Ubuntu figured that one out.... Not even kudzu and DrakX are that smart!

---

