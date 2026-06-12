---
title: "Murrinastormcloud after gksu"
date: 2008-06-18
forum: General Help
---

### Post by bubba_169 on 2008-06-18
After switching back to Gnome from XFCE I decided to keep the default theme Xubuntu uses as I really like the colour of the titlebars. Only problem is when this theme is applied, anything run under gksu (an example being 'gksu gedit') isn't themed.

Windows appear (with lack of a better way to put it) like windows 9x...

The attached screenshot should show what I mean, on the left is normal gedt on the right is the gksu version...

Has anyone run into this before and found a workaround?

---

### Post by bubba_169 on 2008-06-19
bump

---

### Post by jjpcexpert on 2010-11-30
The last time you have to see Raleigh for until your graphics drivers fail to detect the monitor's refresh rate is:
gksu nautilus
Go to File > New Window
Open /home/<your-username>/.themes (where <your-username> is your username in UNIX) in one window
Open /usr/share/themes in another
Copy MurrinaStormCloud (and/or MurrinaStormCloudSilver, and/or any other themes you want in gksu) to /usr/share/themes
Close both windows when copy is done
Open a Gksu'd gedit or synaptic
Should work.

Tested it just now.

Now I think you should go to CCSM > Title Bar Info > Enable plugin. Just so you see when it's root.

---

