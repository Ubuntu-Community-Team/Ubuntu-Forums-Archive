---
title: "change default program for opening files? UbuntuGnome 14.04"
date: 2015-03-06
forum: General Help
---

### Post by Halpm on 2015-03-06
Somehow, I've "tweaked myself into a corner" and don't know how to get out. When I put a usb drive in, then I get the option to either open the media or eject - but it only gives me the option to open with disc usage analyser!! The same thing happens when I try to open a folder that I've searched for in the shell - it opens the folder with disc usage analyser. Is there any way to change the default programme back to nautilus?

---

### Post by mc4man on 2015-03-06
Don't use ubuntu gnome so of little possible help. You may want to check a few things though - 
Is nautilus running? - run this in a terminal, should return nautilus -n 
```
ps axu |grep nautilus |grep -v grep
```

Does nautilus launch via it's .desktop? (2 possible .desktops
```
gtk-launch nautilus
```
```
gtk-launch nautilus-folder-handler
```

And while any entry(s) should make no difference if nautilus is running what, if anything,  is returned?
```
cat ~/.local/share/applications/mimeapps.list |grep inode/directory
```

---

### Post by Halpm on 2015-03-06
Cheers, here are the outputs:

hal@hal-W150HRM:~$ ps axu |grep nautilus |grep -v grep
hal       2388  0.1  0.4 1111136 34768 ?       Sl   18:27   0:10 /usr/bin/nautilus --no-default-window

hal@hal-W150HRM:~$ gtk-launch nautilus

opens nautilus fine.

hal@hal-W150HRM:~$ gtk-launch nautilus-folder-handler

(gtk-launch:5719): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1443:2: Missing name of pseudo-class
gtk-launch: no such application nautilus-folder-handler

And no output from the final code line.

---

### Post by Halpm on 2015-03-12
Does the above mean anything to anyone? :D

---

### Post by CantankRus on 2015-03-12
If this....
```
xdg-mime query default inode/directory
```
doesn't return **nautilus.desktop** try running ...
```
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
```

---

### Post by Halpm on 2015-03-12
That nailed it - thanks!

---

