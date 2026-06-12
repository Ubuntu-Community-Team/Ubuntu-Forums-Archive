---
title: "Boot into windows 1st"
date: 2007-06-27
forum: General Help
---

### Post by DrEmpire on 2007-06-27
i only have one computer and others in my household dont want to use unbuntu as its hard for thembut i love useing it now,is there a way of booting windows 1st so no one has to do n e thing to change in the menu screen where u hve a choice with os u want to boot into? i think ive asked it properly lol

---

### Post by Ragazzo on 2007-06-27
Edit /boot/grub/menu.lst with **gksudo gedit /boot/grub/menu.lst** and find something like this at the bottom of the file:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Cut that part of your file and paste it right **before** the line:
```

### BEGIN AUTOMAGIC KERNELS LIST

```

---

### Post by DrEmpire on 2007-06-27
it now says iam not the owner

how do i get permission to edit files in grub, could i have installed ubuntu wrong or badly?

---

### Post by Steve B on 2007-06-27
are you sudoing in from the terminal?

---

### Post by DrEmpire on 2007-06-27
i dont know i dont get this any more lol,ive been trying to fix 5 or 6 problems at the same time, i hate my screen size, what did you mean there sudo

---

### Post by Ragazzo on 2007-06-27
Press Alt+F2 and write **gksudo gedit /boot/grub/menu.lst**

---

### Post by DrEmpire on 2007-06-27
thank you all fixed kind sir :), ok woundering if you could help with my graphics(card)  i would like a larger ressolution 1280*1024 im useing nvidia, ive read alot on forums about this but not much i understand

---

### Post by Ragazzo on 2007-06-27
> **DrEmpire said:**
> thank you all fixed kind sir :), ok woundering if you could help with my graphics(card)  i would like a larger ressolution 1280*1024 im useing nvidia, ive read alot on forums about this but not much i understand

I can try. If the resolution isn't available in System->Preferences->Screen Resolution, open up the terminal in Applications->Accessories>Terminal and write this in it: 
```

sudo dpkg-reconfigure xserver-xorg

```

It will start asking a lot of questions. Select the default values until you come to *Video modes to be used by the X Server*. Select or unselect the resolutions that you want to enable by pressing Space. After that keep choosing the default values again until you're back in the command-line. Restart your computer or press Ctrl+Alt+Backspace to restart only the window manager (GNOME). Now you should be able to select the resolution in System->Preferences->Screen Resolution. If you're not, post a new topic.

---

### Post by DrEmpire on 2007-06-27
great its help though not the resalotion i would really like so ill post anther topic on to the forum find out some more information

---

