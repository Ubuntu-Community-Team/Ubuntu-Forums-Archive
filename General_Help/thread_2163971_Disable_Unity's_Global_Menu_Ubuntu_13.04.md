---
title: "Disable Unity's Global Menu Ubuntu 13.04"
date: 2013-07-20
forum: General Help
---

### Post by nmu on 2013-07-20
Hi:

I modified the tip I took from [http://lifehacker.com/5887462/how-to-disable-ubuntus-annoying-global-menu-bar](http://lifehacker.com/5887462/how-to-disable-ubuntus-annoying-global-menu-bar) and used the command

```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt5
```

to remove Unity's global menu under 13.04.

I wish there would be an option to set which application the global  menu would apply to. E.g. IDEs like Lazarus are hard to use with the global menu.

HTH,

NM

---

### Post by ktbos on 2013-08-02
This trick didn't work for Firefox.  The global menus were still active. 

Found an answer in [http://askubuntu.com/questions/312965/how-can-i-disable-the-global-menu-in-firefox](http://askubuntu.com/questions/312965/how-can-i-disable-the-global-menu-in-firefox)

First, I upgraded Firefox in Synaptic.  Interestingly, when upgrading from Firefox 20 to 22, Synaptic told me it was also going to update package "firefox-globalmenu".  

After starting the new version of Firefox, you go to "about:config" and say yes to "void warranty"!  Search for "unity" and right click on the result to choose toggle (or just double click).  Then restart Firefox.

---

### Post by dutchhome on 2013-09-01
There is another step that is missing.  Once you remove all the appmenu extensions (BTW, you missed appmenu-qt in your list), you need to change the setting in Firefox as mentioned above.  You also need to add the nautilus menus back to the cog menu.  This link has the details:

[http://www.webupd8.org/2013/02/how-to-disable-gnome-shell-appmenu.html]("http://www.webupd8.org/2013/02/how-to-disable-gnome-shell-appmenu.html")

---

### Post by LudoTW on 2013-10-30
When you do this, don't you have a bunch of warning message when running gedit (didn't try yet other applications)?

```
`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load
(gedit:5762): Gtk-WARNING **: Failed to load type module: (null)
`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load
```

---

