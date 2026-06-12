---
title: "No access to tty1, tty2 ..."
date: 2008-03-06
forum: General Help
---

### Post by didli on 2008-03-06
Hi everyone :) !
Everytime i log out my session with ctrl+alt+->, my screen goes black and i can't see any tty text (it's as if my resolution was too big or too small, can't really tell). 
It is beginning to be quite a problem ... For infos : I'm currently using the repository version of fglrx.
Any idea please :) ?

---

### Post by SpaceTeddy on 2008-03-06
mhm... i've had that problem in feisty... disableing the splash during boot fixed it for me. I don't know if that still works in gutsy tho.

to do that, run this command
```
gksu gedit /boot/grub/menu.lst
```

that should open your grub configuration... search for a line that looks like this one
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=67397eb5-badc-4989-bb6d-a94998666569 ro quiet splash
```

and remove the spash (can remove the quiet if you want, too). that should disable the splash. then reboot your system and see if you can access the consoles :)

---

### Post by didli on 2008-03-06
Wow Fast Answer and ... yes ! It worked :)
Thanks SpaceTeddy ! I delete splash from # defoptions and now I can see tty.
Next thing please, if it doesn't bother you, do you know why my splash mess up with tty ? Is there any chance to keep the splash AND the tty console ?
Thanks again anyway !

---

### Post by SpaceTeddy on 2008-03-06
i personally find the splash rather disturbing (i like to see what is happening), but my guess is that is has something to do with the framebuffer being setup wrong. 

how to fix this i have no idea - never looked into it. I wanted to splash gone anyway :)

---

