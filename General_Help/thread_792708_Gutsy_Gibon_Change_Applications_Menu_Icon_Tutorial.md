---
title: "Gutsy Gibon Change Applications Menu Icon Tutorial"
date: 2008-05-13
forum: General Help
---

### Post by punxtux on 2008-05-13
[B]If this hasn't been posted like this, I gathered information on the net and with a bit of trial and error, I found the way to change your Applications Icon in Gutsy Gibon 7.10.

-Get whatever picture you want, and resize it to a 22x22 image 
-Save it to your desktop as 'start-here.png' format. (minus the qoutes) 

-Open terminal.

$cd Desktop

$sudo cp /usr/share/icons/gnome(or whatever icon theme you use)/22x22/places/start-here.png start-here-old.png

$sudo cp start-here.png /usr/share/icons/gnome(or whatever icon theme you use)/22x22/places/

$sudo gtk-update-icon-cache /usr/share/icons/gnome(or whatever icon theme you use)/

$killall gnome-panel

There ya go. I hope it goes as smooth for you as this process did for me. Just remember to change whatever theme you're replacing with the correct name where I put 'gnome'.

Enjoy!






[/B]

---

