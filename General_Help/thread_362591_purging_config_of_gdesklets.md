---
title: "purging config of gdesklets"
date: 2007-02-15
forum: General Help
---

### Post by xolot1 on 2007-02-15
i installed gdesklets and got them working nice, etc. i added an extra unstable desklet that has been causing problems, and one is that i cant right click on it to "remove" it. i also cant figure out any way to remove an individual desklet w/o that mouse click. is there any other way to do this?

i had resorted to just synaptic - > completely remove gdesklets, but when i reinstall, all the config is the same, ie the desklet is still stuck on my screen. how can i remove these configs?

thanks!

---

### Post by dcstar on 2007-02-15
> **xolot1 said:**
> i installed gdesklets and got them working nice, etc. i added an extra unstable desklet that has been causing problems, and one is that i cant right click on it to "remove" it. i also cant figure out any way to remove an individual desklet w/o that mouse click. is there any other way to do this?

i had resorted to just synaptic - > completely remove gdesklets, but when i reinstall, all the config is the same, ie the desklet is still stuck on my screen. how can i remove these configs?

thanks!

Delete the hidden .gdesklets folder in your home directory.

---

### Post by maxamillion on 2007-02-15
```
sudo aptitude purge <package name>
```

should in theory also solve this issue

---

### Post by xolot1 on 2007-02-15
> **dcstar said:**
> Delete the hidden .gdesklets folder in your home directory.


perfect!
thanks!

---

### Post by tanman on 2007-02-15
I have also downloaded desklets, but can not get any of the Rhythmlet one to work. They all say Rhythmbox not playing. I can right click on the applet, but none of the buttons seem to be responding.
Which is your favorite Desklet?

---

