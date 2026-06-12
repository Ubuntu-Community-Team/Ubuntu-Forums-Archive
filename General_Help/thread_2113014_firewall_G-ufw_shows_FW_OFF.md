---
title: "firewall G-ufw shows FW OFF?"
date: 2013-02-06
forum: General Help
---

### Post by Locus Kiesselbachi on 2013-02-06
Hello!

Can anyone help solving this following riddle with my (L)ubuntuOS?
Installed graphical interface of ufw, but it shows that firewall is "off". :S

command:
sudo ufw enable
gives:
Firewall is active and enabled on system startup

...so is it OFF or ON?


Lubuntu11.10
AMD Athlon18001,5GHz
ASRock mainboard K7S41GX
Nvidia Geforce 5200FX, using DVI

...I dont know if this matters anything, but OS acts kind of strange: spalsh screen on startup is glitchy - its white stripes and some symbols )))::::;;;;. Also monitor wont startup at first, I have to "reset" my computer almost every time (double startup).

command:
gufu
gives:
(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:102:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:117:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:134:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:153:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:165:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:175:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:186:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:198:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:208:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:218:16: Themeing engine 'adwaita' not found

(gufw.py:1844): Gtk-WARNING **: Theme parsing error: gtk-bars.css:223:16: Themeing engine 'adwaita' not found

---

### Post by ankspo71 on 2013-02-07
That is because Gufw's interface is locked for security reasons. Gufw will show you the true firewall status after clicking on the yellow padlock in the bottom right corner and entering your password.

---

### Post by Locus Kiesselbachi on 2013-02-09
> **ankspo71 said:**
> That is because Gufw's interface is locked for security reasons. Gufw will show you the true firewall status after clicking on the yellow padlock in the bottom right corner and entering your password.

Hey, thank you! :D

---

