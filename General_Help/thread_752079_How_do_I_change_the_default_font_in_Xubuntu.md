---
title: "How do I change the default font in Xubuntu?"
date: 2008-04-11
forum: General Help
---

### Post by atomkarinca on 2008-04-11
I tried a few things with no luck. First of all, I'm trying to get a truetype font to work. I copied it to
 
/usr/share/fonts/truetype
~/.fonts
/usr/X11R6/fonts

and then

```
sudo fc-cache -f -v
```

but I still can't see the font in Settings Manager > User Interface. I can select that font using text editors by the way. How can I set it as the default font of interface?

---

### Post by w0ng on 2008-04-11
Can you list examples of the ttf you're trying to use?

Anyway, try:
```
sudo dpkg-reconfigure fontconfig-config
```
Font tuning method: Autohinter
Subpixel rendering: Automatic
Enable bitmapped fonts: No

then:
```
sudo dpkg-reconfigure fontconfig
```

---

### Post by atomkarinca on 2008-04-11
> **w0ng said:**
> Can you list examples of the ttf you're trying to use?

Anyway, try:
```
sudo dpkg-reconfigure fontconfig-config
```Font tuning method: Autohinter
Subpixel rendering: Automatic
Enable bitmapped fonts: No

then:
```
sudo dpkg-reconfigure fontconfig
```


Thanks but it didn't work. Isn't it weird that I can see the font listed in the text editors but not in the user interface dialog?

---

### Post by PJSingh5000 on 2008-05-12
Be sure that all the directories and files under /usr/share/fonts/ have appropriate permissions: Owner: Can Read & Write, Group: Can Read, Others: Can Read.

If you need to change these permissions...
$ cd /usr/share/fonts
$ sudo chmod -R u+rw,g+r,o+r *

Also, I was successful in getting anti-aliasing to work globably using...
$ sudo dpkg-reconfigure fontconfig-config --force
Select:
	Font tuning method for screen: Autohinter
	Enable subpixel rendering for screen: Automatic
	Enable bitmapped fonts by default? No

Delete .fonts.conf from your home directory:
$ rm ~/.fonts.conf

Whenever there is a .fonts.conf file in your home directory, the global settings are overridden.  This file is recreated whenever you access the font/appearance configuration utility (K | System Settings | Appearance), so you may have to delete it after using the utility.

(If anyone knows how to prevent .fonts.conf from being created, please post the solution).

Tip: Use Liberation Sans font...
$ sudo apt-get install ttf-liberation

---

