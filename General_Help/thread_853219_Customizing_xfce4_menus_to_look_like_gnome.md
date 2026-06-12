---
title: "Customizing xfce4 menus to look like gnome"
date: 2008-07-08
forum: General Help
---

### Post by ReiN[FiN] on 2008-07-08
My goal is to make the xfce menu look and behave like gnome's one. 


Xfce4
Applications: Places:

GNOME
Applications:  Places:  SYSTEM:


So far I've only found out that /etc/xdg is the place where magic happens and menus are generated for different languages. I need these menus to be generated, not hand made. We all like standards :) 

Editing icons at /usr/share/applications/ would also be a bad long term solution, requiring hand tuning after new software installation.


Ideas? Has someone done this already?

---

### Post by MetalheadGautham on 2008-07-31
I too want to do something similar. I think the default Xfce menu is a bit too complicated compared to the organised gnome menu. Isn't there a way to get the ubuntu gnome look onto ubuntu xfce and do some tweaks to make it even more light, to a level comparable to zenwalk ?

---

### Post by denham2010 on 2008-07-31
Hi,

The simplest solution is to just use the actual Gnome menu.

Xfce has an applet - called Xfapplet - for the panel that allows you to use Gnome applets.

Install Xfapplet:
```
sudo apt-get install xfce4-xfapplet-plugin
```

Install Gnome menu: (this will also install a lot of gnome libraries as dependencies)
```
sudo apt-get install gnome-main-menu
```

Once done, right click your Xfce panel and select "Add New Item"

Select XfApplet from the list.

Once this is added to the panel, a list of installed Gnome applets will be displayed.

Select the menu applet and you are all set.

Cheers.

---

