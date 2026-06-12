---
title: "How to start SCIM in Xubuntu XFce4 and Fluxbox?"
date: 2006-10-22
forum: General Help
---

### Post by erik-the-red on 2006-10-22
How can I modify this:

> 
got it figured out

add a new file called ".xsession" in the home directory

paste:

export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

in the file and save it

Go to "System" -> "Perferences", and select "Sessions". In "Startup Programs", add the command "scim -d".

After a reboot/new login everything should be golden

for Xubuntu?

---

### Post by erik-the-red on 2006-10-23
I guess Chinese still isn't ready for the desktop.

---

