---
title: "GrubConf.."
date: 2005-03-21
forum: General Help
---

### Post by Mase Track on 2005-03-21
Since updating from Warty to Hoary, my grub has, shall we say, quite a few options to choose when I boot up! 

I've gone into grubconf to have a closer look, and it's like they are all pointing to the same place, But Im new to Ubuntu + Linux, and want to know which to delete without ruining some aspect of my distro!

any help would be appreciated :D

---

### Post by MicroChris on 2005-03-21
If its just lots of old kernels you aren't using, go to Synaptic and remove the old kernels you dont want by right-clicking on them and checking "Mark for Removal".. After it goes through the removal, it will then rewrite your menu.lst file.

Keep in mind, if you're running a dual boot to any other OS, you will need to readd it as the menu.lst gets totally rewritten.

Best of luck,
Chris

---

