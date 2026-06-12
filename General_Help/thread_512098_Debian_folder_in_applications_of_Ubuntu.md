---
title: "Debian folder in applications of Ubuntu"
date: 2007-07-28
forum: General Help
---

### Post by compsariomike on 2007-07-28
Alright

So maybe i'm just not very observant, but i've just noticed that there is a Debian file under applications
Applications>>Debian

But some of the shortcuts seem to not work and don't have descriptions (the drop down ones that show up when you mouse over them) and some don't have icons.  

so should i fix this problem or delete it?  And how do I do either?  
Thanks!

---

### Post by Ripfox on 2007-07-28
This is an application called "debian menu"
You must have installed it at some point. I never thought it was all that useful...some may disagree. You can presumably uninstall it with Synaptic by searching for it then marking it for uninstallation.

---

### Post by RedSquirrel on 2007-07-28
The  package is called 'menu'.

If you want to fill in your Debian menu, running this command should do it:

```
sudo update-menus
```

---

### Post by compsariomike on 2007-07-30
I tried that but nothing happened?  Do I need to reboot before the update takes effect?  Or is there something else I can do?  

Thanks

---

### Post by RedSquirrel on 2007-07-30
Make sure the menu package is installed.

```
sudo apt-get install menu
```then try

```
sudo update-menus
```If that doesn't help, you could try:

```
sudo dpkg-reconfigure menu
```You might have to log out and log back in again, but I doubt it. I'm pretty sure the update is done immediately and should be shown in your menu. I haven't used GNOME in a while but I believe 'sudo update-menus' should work as long as the menu package is installed.

---

