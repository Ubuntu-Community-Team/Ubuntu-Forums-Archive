---
title: "How to Disable double click from touchpad"
date: 2008-05-13
forum: General Help
---

### Post by JustinAlf on 2008-05-13
I don't use the doublclick from the touchpad, but rather the left mouse button on my laptop.  In KDE, how do I disable the double-click funtion?

---

### Post by hermes0710 on 2008-05-14
Make sure you have an entry :```
Option      "SHMConfig" "on"
``` in your xorg.conf in the "InputDevice" Section. Then 
```
sudo apt-get install ksynaptics
``` and reboot. Run ksynaptics and see if theres is an option disabling the double click.

Check this: 

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/]("http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/")

---

### Post by JustinAlf on 2008-05-14
Thank you very much!  Worked perfectly.  I wonder why this isn't an option like it is in Gnome.

---

