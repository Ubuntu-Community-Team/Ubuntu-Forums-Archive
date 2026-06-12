---
title: "possible to remove &quot;quit&quot; button from ubuntu menu?"
date: 2006-09-13
forum: General Help
---

### Post by bionnaki on 2006-09-13
hello. I have a special setup in which I need to remove the "quit" button from the menu. I would like to only have sudo users be able to logout, shutdown, reboot. I have disabled gdm from starting up and this allows me to protect the computer from rebooting (sudo reboot in terminal is required). 

But the "quit" button is there and clicking it ends the X session. Is there anyway to get rid of it?

thanks

---

### Post by ciscosurfer on 2006-09-13
Right-click > Remove from panel

---

### Post by pravuil on 2006-09-13
You can also use Alacarte menu editor if your using gnome.

---

### Post by bionnaki on 2006-09-13
removing the menu from the panel is not what I would like to do. I would like to remove the "quit" button on the menu itself.

as for alacarte menu editor, the "quit" button is not listed, only applications.

anyone else know?

---

### Post by bionnaki on 2006-09-13
[IMG]http://img53.imageshack.us/img53/6084/quitvs8.jpg[/IMG]

---

### Post by pravuil on 2006-09-13
[http://www.gnome.org/learn/admin-guide/latest/menustructure-2.html](http://www.gnome.org/learn/admin-guide/latest/menustructure-2.html)
Don't know if this will work but it should considering it is from the official gnome site. The info is at the bottom under "Deleting an Item from a Menu"

---

### Post by DoktorSeven on 2006-09-13
Run **gconf-editor** and browse to /apps/panel/global/.

Check disable_log_out.

---

