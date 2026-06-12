---
title: "How are those pop ups called and is it possible to add them on xubuntu"
date: 2014-09-18
forum: General Help
---

### Post by danbuz on 2014-09-18
Hi there,

I like xubuntu and yet I would like to know is it possible to add similar pop-up like style menus like those in gnome and cinammon for example. I mean the design when I press pannel right click for example to be like [this]("http://www.themukt.com/wp-content/uploads/2014/08/linux_mint_bottom_menu.jpg") pop up and not like ordinary rectangle list of options..?

Is that possible guys? I think It could add some freshness to the nice xfce look! 
Thanks in advance!

---

### Post by ibjsb4 on 2014-09-18
As far as I know, that is part of the panel.  So what you could do is try different panels.
Here is a partial list:
[https://wiki.archlinux.org/index.php/list_of_applications#Taskbars_.2F_panels_.2F_docks](https://wiki.archlinux.org/index.php/list_of_applications#Taskbars_.2F_panels_.2F_docks)

Using Synaptic package manager you can get a complete list of supported panels.
[ATTACH=CONFIG]256539[/ATTACH]
To install and temporary activate a panel.  Example using gnome-panel:
```
sudo apt-get install --no-install-recommends gnome-panel
```
And then to activate.
```
gnome-panel
```
To make a permanent panel change, I am not sure how that is done in Xubuntu.  Someone else will have to help you.

Also take note of the dependencies when installing different panels, you could end up with more than you want.

---

