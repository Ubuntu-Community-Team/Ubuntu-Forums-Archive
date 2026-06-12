---
title: "Beryl - just blew up on me how do I get back up and running?"
date: 2007-03-01
forum: General Help
---

### Post by otazman on 2007-03-01
I am sitting at the terminal mode. logged in and need to edit the xorg.conf but I don't know how to edit a file in terminal mode. Gedit is obviously not working? If I have to use VI or something similiar can you include quick instructions on how to make a edit and save changes.

I will also need to edit my startup programs. What file do I need to edit to remove Beryl and Emerald from the startup options?

Thanks again, OT

---

### Post by aidanr on 2007-03-01
sudo nano /etc/X11/xorg.conf
rm ~/.config/Autostart/beryl-manager.desktop

(assuming you're logged in as a user, if you're logged in as root then theres no need for sudo and you can replace ~ with /home/username)

---

