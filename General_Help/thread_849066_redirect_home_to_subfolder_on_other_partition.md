---
title: "redirect /home to subfolder on other partition?"
date: 2008-07-04
forum: General Help
---

### Post by ricster on 2008-07-04
A bit of googling has shown how to mount /home AS a new partition but i don't want to do that, I have a seperate ext3 partition which has various docs/mp3s etc in it and want home to sit alongside them, the full path would look something like

 /dev/hda5/home

can I mount that directly as home, or does it need to be root in the partition? i.e. will:

 /dev/hda5/home /home ext3 nodev,nosuid 0 2

work or will i need a symlink instead? (btw taring it up and shifting it over isn't a problem, and I'll probably try it tonight i just wanted to check first!)

ricster

---

### Post by justleen on 2008-07-04
a symlink would be best.. there is no /dev/sda1/home, and you cant create it.

so you have to mount /dev/sda1 to /whatever,  create a folder /whatever/home, and symlink your home to that.

---

