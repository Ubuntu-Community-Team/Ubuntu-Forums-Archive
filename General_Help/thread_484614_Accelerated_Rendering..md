---
title: "Accelerated Rendering."
date: 2007-06-26
forum: General Help
---

### Post by phizikal on 2007-06-26
Ok, all my screensavers and games are very laggy. I have a nvidia-glx-legacy graphic card. But can anyone guide me to setting up accelerated rendering. I really would like to have better quality and frame rate. Please and Thank yous.

---

### Post by phizikal on 2007-06-26
No one can help?

---

### Post by phizikal on 2007-06-26
Ok, can someone please help. I am really need to get this done.

---

### Post by kekojeep on 2007-06-27
Is your X using "nvidia" driver in /etc/X11/xorg.conf?

[ ]'s

---

### Post by franck3d on 2007-06-27
have  you turned on the restricted driver for your nvidia card?
you said that you have a legacy card, how old is it(what model)?
I'm running a  440mx at home and screensavers work fine for me.

---

### Post by phizikal on 2007-06-28
Ok, I installed my correct drivers. But, it's not letting me save the xorg.conf file. I tried all doing it under permissions but it wont let me. I know now I need to do it under shell, but I don't know the command. =/

---

### Post by franck3d on 2007-06-29
first, it's a good idea to backup your xorg.conf so do this in a terminal:

sudo cp /etc/X11/xorg.conf xorg.conf.bu

then you can:

sudo gedit /etc/X11/xorg.conf

that will give you permission to edit the file with a backup in case there is a problem.
if X fails on you and you end up with a command line system:o

sudo cp /etc/X11/xorg.conf.bu xorg.conf 

will restore the original file so you are back where you started!

---

### Post by The_3cHeLoN on 2007-06-29
You might try to use 'envy', you can download it from [here]("http://www.albertomilone.com/nvidia_scripts1.html"). Envy will install the proprietary nvidia drivers for you. Be sure to uninstall the 'nvidia-glx-legacy' package.

---

### Post by sochbat on 2007-07-18
I have the same problem.  Weird thing is, everything is fine and dandy, but certain games won't work.

I can play Nexius, and Temulous fine, but no visuals when i try Regnum and Savage.

Any clues on troubleshooting?

---

