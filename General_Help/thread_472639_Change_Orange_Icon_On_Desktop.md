---
title: "Change Orange Icon On Desktop"
date: 2007-06-13
forum: General Help
---

### Post by TheVault on 2007-06-13
Hello guys,
Iv tried everything and this sucker wont change at all. I'm wanting to change that orange icon in the upper left(my desktop has not been moved or altered in anyway). The icon of where you click, you get menus inside it, that icon. I'm wanting to replace it with this apple.png image, its a blue image of a apple much like the one on Mac OS X.

I did do what some tutorials where saying and go into the /usr/share/icons/hicolor/48x48/apps/ and replace the distributor-icon.png with the image your wanting and then restart panel. I did all that stuff.

Im using this tutorial here: [http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php) and I also found out that her location for where you put the logo was kinda wrong anyway.

Iv tried everything to my ability and iv looked at some tutorials and nothing is working. Is there an application or something that could automatically change it to something that I want? I really need some help, trying my very best to make Ubuntu look like Mac OS X, if not, then i'll change it to Vista look, but overall, I need to get that icon changed somehow. Thanks.

---

### Post by rax_m on 2007-06-13
Got this off gnome-look.org. You shouldn't have to rename any of your existing icons or the like. Just copy your new icon to some where in your home folder like /home/me/.icons/apple_icon.png

1. run gconf-editor
2. navigate to /app/panel/objects

find a object_x with the "object_type=menu-object".

(my main menu is "object_8")

4. tick up "use_custom_icon"
5. change "custom_icon" value to the image path.

Rax

---

### Post by rax_m on 2007-06-13
BTW This is assuming you're using Ubuntu / Gnome desktop.

---

### Post by TheVault on 2007-06-13
I tried that but there is no objects part. I removed the bottom panel and kept the top. I donno but nothing is working

---

