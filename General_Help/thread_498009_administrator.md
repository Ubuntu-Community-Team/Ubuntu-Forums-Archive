---
title: "administrator"
date: 2007-07-10
forum: General Help
---

### Post by mr.farenheit on 2007-07-10
what all files and programs do i need to set up ubuntu as if i were an administrator? i mainly need this for the small network i have as a work in progress and i want to be able to monitor and access all content if needed.

---

### Post by fredj on 2007-07-10
When you install packages using the Administration - Synaptic Package manager to install programs you
will be doing this as an administrator. Otherwise open a terminal and type sudo -i. This makes you an
admin user while the terminal windows is open. Then for example you can type 'nautilus' to start the file
browser in admin mode. This will allow you to set file permissions for any file or directory. Typing 
'gedit filename' allows you to edit any file including system files that are not accessible when you are just
an ordinary user. 
However be careful. You can mess up your system by reckless editing or alteration of permissions.

---

