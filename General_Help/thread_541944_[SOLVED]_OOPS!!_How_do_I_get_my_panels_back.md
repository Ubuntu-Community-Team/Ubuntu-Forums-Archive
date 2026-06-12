---
title: "[SOLVED] OOPS!! How do I get my panels back?"
date: 2007-09-03
forum: General Help
---

### Post by rg_stephens on 2007-09-03
I think I made a big mistake. I was frustrated because wireless networking was not working part of the time, so after reading another post, I decided to install WICD and remove the Network Monitor. Network Monitor was still showing up (and not working), so I went into Synaptic Package Manager to try to uninstall it. 

I don't remember exactly what I uninstalled, but when I rebooted my computer, all of my taskbars are missing (or are they called panels?). I only have a desktop with icons; everything else seems to work ok. How do reinstall whatever it was that I removed?? 

Please help if you can. I need my computer for school tomorrow. I'm using Feisty.

---

### Post by Happy_Man on 2007-09-03
Hmm..... Well, press alt-f2, and run the command ```
gnome-terminal
```. Then in there, runt the command ```
sudo apt-get install gnome-panel
```. Then, once that's done, close the terminal, and press alt-f2 again. Run the command ```
gnome-panel
```. If all went well, your panels should be back.

---

### Post by rg_stephens on 2007-09-03
Did you mean ctrl-alt-f2? This brought me to the login prompt.

I did this, and it says, "cannot open display"

---

### Post by Happy_Man on 2007-09-03
No, I meant alt-f2.

---

### Post by aysiu on 2007-09-03
Press Control-Alt-F7 to get back.

Then press Alt-F2 (without the Control).

---

### Post by Ptero-4 on 2007-09-03
alt-f2 won't work. The run dialog is part of the OP's missing gnome-panel app.

---

### Post by walkerk on 2007-09-03
> **rg_stephens said:**
> I think I made a big mistake. I was frustrated because wireless networking was not working part of the time, so after reading another post, I decided to install WICD and remove the Network Monitor. Network Monitor was still showing up (and not working), so I went into Synaptic Package Manager to try to uninstall it. 

I don't remember exactly what I uninstalled, but when I rebooted my computer, all of my taskbars are missing (or are they called panels?). I only have a desktop with icons; everything else seems to work ok. How do reinstall whatever it was that I removed?? 

Please help if you can. I need my computer for school tomorrow. I'm using Feisty.

yep.. just re-install gnome-panel.

installing wicd would not remove gnome-panel.. not too sure what you did here..

---

### Post by rg_stephens on 2007-09-03
now I tried opening "Create Launcher" and typing in "gnome-panels". My panels reappeared after a few errors. It looks like it is back to normal.

alt-f2 wasn't working before. Now it is.

I must have uninstalled it when I was trying to get rid of Network Monitor. I've learned my lesson.

Thanks to all of you for your quick help. This had me worried for a minute.

---

### Post by rg_stephens on 2007-09-03
I'm still getting a ton of errors like 

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
The panel encountered a problem while loading "OAFIID:GNOME_StickyNotesApplet".
 and so on......

How do I restore the applets that were missing? I tried deleting the panel and adding them again, now I can't find WICD or Network Monitor. Many of the Applets don t work now

---

### Post by aysiu on 2007-09-03
Maybe [this](http://ubuntuforums.org/showthread.php?t=25259) might help.

---

### Post by rg_stephens on 2007-09-03
> **aysiu said:**
> Maybe [this](http://ubuntuforums.org/showthread.php?t=25259) might help.

 It's working fine now. Thanks again!!

---

