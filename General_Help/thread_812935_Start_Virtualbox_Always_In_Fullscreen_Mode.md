---
title: "Start Virtualbox Always In Fullscreen Mode?"
date: 2008-05-30
forum: General Help
---

### Post by Josh08 on 2008-05-30
Hello,

I know that it is possible to make your VirtualBox full screen by pressing Host + F or Host + G to fit the resolution but is it possible to keep it fullscreen without having to press these controls everytime i start the vm. Is there a way to save it in fullscreen? so i don't have to keep pressing the controls to manually set it like Virtual PC.

Thanks, josh.

---

### Post by george9233 on 2008-05-30
Go to the ".VirtualBox" folder in you home directory. Go into "machines", and then into the folder named by the virtual machine that you want it to start in fullscreen. Then open the XML file using your favourate text editor. Go to line 9 which determines if the VM would start in fullscreen mode, and change "off" to "on". Then it will start in fullscreen mode. 

However, after the splash screen of Sun xVM VirtualBox, it returns to window mode. I currently cannot find the way to turn the splash off, sorry.

By the way, are you using the old version VirtualBox OSE 1.5 or the newer one Sun xVM VirtualBox 1.6? I did the tests on the newer one. If you're using the old version there might not be a splash screen 'cause I don't remember there was one when using it before.

---

### Post by perspectoff on 2012-06-02
> **george9233 said:**
> Go to the ".VirtualBox" folder in you home directory. Go into "machines", and then into the folder named by the virtual machine that you want it to start in fullscreen. Then open the XML file using your favourate text editor. Go to line 9 which determines if the VM would start in fullscreen mode, and change "off" to "on". Then it will start in fullscreen mode. 

However, after the splash screen of Sun xVM VirtualBox, it returns to window mode. I currently cannot find the way to turn the splash off, sorry.

By the way, are you using the old version VirtualBox OSE 1.5 or the newer one Sun xVM VirtualBox 1.6? I did the tests on the newer one. If you're using the old version there might not be a splash screen 'cause I don't remember there was one when using it before.

If the Virtual Machine is name "Myvirtualmachine1" then you can start VirtualBox in fullscreen mode using the command (as a menu item, for example):

 VirtualBox -fullscreen -startvm "Myvirtualmachine1"

---

