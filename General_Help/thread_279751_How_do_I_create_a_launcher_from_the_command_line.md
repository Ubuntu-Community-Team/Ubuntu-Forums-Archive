---
title: "How do I create a launcher from the command line?"
date: 2006-10-18
forum: General Help
---

### Post by Count Noobulus on 2006-10-18
I'm ready to put the finishing touches on my livecd/add-on cd setup and I'd like to make some desktop launchers for the extra stuff I'm installing. Having a hard time finding info on this, can anybody help? 

Oh, and I know how to do this manually, I just want some automagic for this. ;)

---

### Post by rejser on 2006-10-18
Manually = right click create launcher or creating one from command?
Why not just create a bash script that asks for your variables and writes a .desktop file.
Basicly you need to name the file, add a value to exec and name to make it runable. You could make it use a default icon

---

### Post by CatKiller on 2006-10-18
I don't know how much you know already, but if you've made your .desktop files already you can put them in the /etc/skel/Desktop directory to have them created for each user.

---

### Post by Count Noobulus on 2006-10-18
> **rejser said:**
> Manually = right click create launcher or creating one from command?
Why not just create a bash script that asks for your variables and writes a .desktop file.
Basicly you need to name the file, add a value to exec and name to make it runable. You could make it use a default icon

Manually = right click create launcher. Yeah, that I know how to do. A bash script is what I'm ultimately after, but what do I put in the command line for this to work? I can't really follow your suggestion above as is. I'm too **noob**untu.

---

