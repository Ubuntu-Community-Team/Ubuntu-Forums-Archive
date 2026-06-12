---
title: "[SOLVED] OpenGEU (Geubuntu) help"
date: 2008-03-16
forum: General Help
---

### Post by absolutezero1287 on 2008-03-16
I just installed opengeu and it's working ok. But the thing is that it's not as fluid as I thought it would be. Switching to other desktops isn't fluid. VLC crashes and won't play music. Any suggestions?

---

### Post by fossiili on 2008-03-18
I installed OpenGeu wich is an Ubuntu 7.10 derivative with the Enlightment VM.

On the right side of the desktop stays a vertical **curtain-rod**. It ones appeared to the Moonlight-theme. I can not draw the curtain on or do anything for it with the mouse. It has different color than the OpenGeu moonlight theme which I like.
The rod is ugly. How to get it disappear?

An other problem:

There is one thing in Ubuntu which I do not like at all. I have three hard disks with a lot of partitions in my computer. In the Gnome desktop each one of them is represented by a **"hard disk" icon**. I think they are ugly. I ones found a method to get them off but I have forgot where. Now I will like OpenGeu very much, but besides the problem mentioned above the ugly partition icons are there again as an heritage of Ubuntu Gnome.

Someone told me to use gnome-editor, but the panel needed is empty. Is there any config-file 
I could edit to get the ugly "harddisks" fly away 	:-({|=

---

### Post by danwood76 on 2008-03-18
You can edit the /etc/fstab file to make the drives mount into the /mnt folder instead of the /media folder.
Anything mounted in the /media folder appears on your desktop.

You could also change the icon theme to give you better graphics.

---

### Post by markharding557 on 2008-03-18
you can remove the desktop drive icons by turning them off in the configuration editor
you get to the sttings through apps-nautilus-desktop.
here you can choose to have trash/computer/home/networkand volume icons visble or not and you can rename them
this is for gnome not xfce

---

### Post by absolutezero1287 on 2008-03-18
<Bump>
Isn't this lovely how the thread that I started has been hijacked?

Well, VLC is working now that I download the proper plugins. As for the effects, I'll tinker with it a bit more

---

### Post by absolutezero1287 on 2008-07-04
I got rid of opengeu because it's too buggy and am making a minimal install via debootstrap.[http://ubuntuforums.org/showthread.php?t=841685](http://ubuntuforums.org/showthread.php?t=841685)

---

