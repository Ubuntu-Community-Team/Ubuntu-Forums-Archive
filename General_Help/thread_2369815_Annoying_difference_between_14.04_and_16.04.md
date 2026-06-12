---
title: "Annoying difference between 14.04 and 16.04"
date: 2017-08-27
forum: General Help
---

### Post by lesliek2 on 2017-08-27
I'm using two laptops, one with 14.04 and one with 16.04. On each, I use the Gnome desktop.

On the 14.04, if I open, say, my home folder, there's a cog wheel at the top right and when I click on it, one of my options is preferences. Using that option, I've enabled single left click to open folders and files.

On the 16.04, if I open my home folder and click on the equivalent cog wheel, there's no preferences option and I haven't been able to find any other way to enable single left click to open files and folders.

How do I enable single left click to open files and folders on the laptop with 16.04?

Thanks,

Leslie

---

### Post by lesliek2 on 2017-08-27
I found the answer. Run:

gsettings set org.gnome.nautilus.preferences click-policy 'single'

---

