---
title: "Sound"
date: 2007-05-12
forum: General Help
---

### Post by NooBeee on 2007-05-12
my sound was working fine and then I installed the realtek ac97 linux drivers and now my sound doesn't work (if it ain't broke....)
anyway, how do i undo driver installs or reinstall the default stuff?

**_stuff i forgot to add:_**
if i click on the sound icon it says something about not detecting any devices because i have the wrong gstreamer plugins or something

---

### Post by energiya on 2007-05-12
How did you installed it? If you compiled and installed the driver in the "classic" manner, try cd to the directory the source is and "sudo make uninstall". If theese drivers have modified some config files, it might need a lot of detective work.

---

### Post by NooBeee on 2007-05-14
nope, i tried 'sudo make uninstalled' and it doesn't work 
*sigh* i suppose i could just reinstall ubuntu(and upgrade to feisty at the same time

---

