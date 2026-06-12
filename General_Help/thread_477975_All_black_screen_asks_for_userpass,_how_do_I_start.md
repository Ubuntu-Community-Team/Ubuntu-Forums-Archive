---
title: "All black screen asks for user/pass, how do I start the GUI or Gnome?"
date: 2007-06-18
forum: General Help
---

### Post by RonB123123 on 2007-06-18
All black screen asks for user/pass, how do I start the GUI or Gnome?

There is a black screen when I boot into Ubuntu and it asks for a user and pass. I type it in and it says I have logged in, but then that's it. It doesn't boot up gnome or any kind of GUI. What's wrong? Do I need to run something? What do I do?

---

### Post by ago on 2007-06-18
do you see any error messages?
look in /var/log

to start the graphic interface manually the command is:

sudo /etc/init.d/gdm restart

---

