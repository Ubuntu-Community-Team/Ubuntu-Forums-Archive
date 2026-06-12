---
title: "enabled desktop effects, installed nvidia-glx - now i cannot boot!"
date: 2007-04-24
forum: General Help
---

### Post by jtms1200 on 2007-04-24
Started with a perfectly functioning install of Feisty. On enabling desktop effects I was prompted to download and install the nvidia-glx drivers. I did and rebooted... 

Now I cannot boot at all - I get nothing but a screen full of multi colored lines when X tries to start.

I don't really need desktop effects on this box, can someone tell me how i can revert back to the original drivers and configuration? I can just wipe and reinstall, but I would rather not have to go through all the configuration again.

Thanks!

---

### Post by energiya on 2007-04-25
Alt+Ctrl+F1 and login. Open /etc/X11/xorg.conf and scroll to the "Device" section and modify "Driver" from "nvidia" to "nv" and save.
> 
sudo vim /etc/X11/xorg.conf

or use nano as an editor.
Hit Alt+Ctrl+Back Space and you will have X. You just need to uninstall the nVidia binary drivers.

---

### Post by filam on 2007-04-27
How does one save the edit to the file? I can reach the listing for the driver and replace it with "nv", but how do I save that edit?

---

### Post by energiya on 2007-04-28
If you use nano, press Ctrl+X (I think - don't have it installed anymore) or if you used vim to edit xorg.conf, press Esc key to exit insert mode and
> 
:wq

to exit vim and save modifications. To enter insert mode, press "i".
To exit without saving modifications type
> 
:q!

after exiting insert mode.

I'm used to vim but it's a bit complicated so you would be better with nano
> 
sudo nano /etc/X11/xorg.conf

modify and see in the lower left corner the keys you have to press to save. I think it was Ctrl+X.

Hope this helps.

---

