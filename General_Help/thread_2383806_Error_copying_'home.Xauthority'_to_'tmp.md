---
title: "Error copying '/home/*****/.Xauthority' to '/tmp/"
date: 2018-01-29
forum: General Help
---

### Post by frank72 on 2018-01-29
hello I hope someone can help.

I just installed 17.10 and its not creating an xauthority file. subsequently I'm getting the following error when running graphical applications as root.

i get errors like this...

gksudo '/home/xxxxx/Downloads/MYAPP
Error copying '/home/xxxxt/.Xauthority' to '/tmp/libgksu-eHDvmv': No such file or directory

If i run    
touch ~/.Xauthority

The file stays empty and when I run gksudo I get a password popup but my text winds up in the terminal beneath it.

Any help appreciated

---

### Post by TheFu on 2018-01-29
Wayland is the default display server on 17.10.  It is NOT X11.  Not all applications are supported by Wayland today.
You can logout, pick the "gear" and there should be an Xorg option in the menu.

---

### Post by frank72 on 2018-01-29
Thank youu so much man. Exactly the info I needed.

---

### Post by yetimon_64 on 2018-01-30
> **frank72 said:**
> Thank youu so much man. Exactly the info I needed.

Could you please mark this thread as [SOLVED]? The blue middle link in my signature has a linked guide for how to do so, if needed, thanks. Regards, yeti.

---

