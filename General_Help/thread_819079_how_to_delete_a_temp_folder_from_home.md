---
title: "how to delete a temp folder from home?"
date: 2008-06-05
forum: General Help
---

### Post by raj83168 on 2008-06-05
I just installed a fresh heron, and i noticed my gnome-appearance-properties have been screwed up. I noticed tht a folder ".icons" is causing the problem in the home directory. If i try to delete it, it reappears automatically, and doesnt contain anything. I tried "sudo rm -r .icons", it gets deleted and when i run gnome-appearance-properties, tht folder shows up again. Any ideas to permanently delete it?

Thanks in advance. 

R

---

### Post by bingoUV on 2008-06-05
Why do you think it is a temp folder? Some part of gnome might require this to be present. Does an empty .icons also screws up your gnome-appearance-properties?

---

### Post by iaculallad on 2008-06-05
Does running **gnome-appearance-properties** (in your terminal) or navigating to System->Preferences->Appearance gives you any error? (Post any error you encounter) The .icons folder inside your /home directory would probably be in no effect with whatever error you're getting.

---

### Post by Xiong Chiamiov on 2008-06-05
If it's being recreated, then that means that gnome needs it.  A easy way to fix DE problems is to delete (or rename) the associated folder in your home directory, as it all gets regenerated on next login if needed.  If you've deleted it and you're still having a problem, then it's not with that folder, since it's being recreated fresh.

---

### Post by raj83168 on 2008-06-05
@BingoUV : Well, when I delete the .icons folder, and open gnome-appearance-properties, the folder is regenerated before the appearance window opens up. 

@iaculallad: this is the error via terminal

> (gnome-appearance-properties:10326): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

(gnome-appearance-properties:10326): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
/home/raj/.themes/Mac4Lin_MacMenu_Graphite_v0.4/gtk-2.0/gtkrc:2219: Unable to find include file: "icons/iconrc"


In addition, I also found out that gnome-appearance-properties is using up almost 50% of my cpu when opened, and instantly goes down when G-A-P is closed. Is this normal? 

Thanks again 

Raj

---

### Post by iaculallad on 2008-06-05
Seems like there is a problem with the theme you installed. Try to remove the theme (going back to Ubuntu's default theme) and test if it displays the same error.

*running gnome-appearance-properties (in your terminal) or navigating to System->Preferences->Appearance*

---

### Post by raj83168 on 2008-06-08
Finally, it seems after a lil research and updates, its a bug in hardy after the latest updates have been installed. 

The updates causes a spike in CPU usage and wallpapers cannot be changed via G-A-P. heres the info: [https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/236778]("https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/236778")

---

