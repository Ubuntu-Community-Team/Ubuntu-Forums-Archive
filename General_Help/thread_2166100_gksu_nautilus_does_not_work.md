---
title: "gksu nautilus does not work"
date: 2013-08-07
forum: General Help
---

### Post by Dannyv2003 on 2013-08-07
Hello!

I am trying to install a new theme, but when I do gksu nautilus, it does it likes it is working. Then it does not do anything.
Right after it says "Initializing nautilus-gdu extension", it stops itself. I use Ubuntu 12.04 on a Gateway 550GR. Please Help.

---

### Post by Bashing-om on 2013-08-07
Dannyv2003; Hi ! Welcome to the forum .

Try as gksudo vice gksu.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by Dannyv2003 on 2013-08-07
That did not work. And thanks.

---

### Post by Bashing-om on 2013-08-07
Dannyv2003; Hummm...
Do you have admin privileges ? what returns from:
```

groups

```
You should see "sudo" in the listing in order to have access.

[INDENT][INDENT]safety is no accident
 [/INDENT][/INDENT]

---

### Post by Dannyv2003 on 2013-08-07
I am the admin of the system

---

### Post by Dannyv2003 on 2013-08-07
If this helps, I am using GNOME with some elements of Pantheon mixed in.

---

### Post by oldos2er on 2013-08-07
> **Dannyv2003 said:**
> That did not work. And thanks.

Can you please post the terminal output of ```
gksudo nautilus
```?

---

### Post by Dannyv2003 on 2013-08-08
Here it is:
```

(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksudo:14970): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Initializing nautilus-gdu extension


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:177:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:179:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:239:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:245:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:298:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:311:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:317:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:335:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:460:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:467:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:474:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:480:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:486:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:492:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:498:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:505:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:512:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:518:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:524:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:533:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:654:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:663:17: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:829:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:834:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:891:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:909:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:927:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:945:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1061:28: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1109:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1141:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1196:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1318:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1338:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1389:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1401:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1412:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1449:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1456:23: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1597:17: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1806:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1821:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1833:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1846:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1903:0: unknown @ rule


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1988:97: 'currentColor' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1996:32: Junk at end of value


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2008:13: 'animation' is not a valid property name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:16:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:33:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:207:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:214:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:226:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:239:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:400:18: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:431:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:447:24: Horizontal and vertical offsets are required


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:458:23: 'px' is not a valid color name


(nautilus:15008): Gtk-WARNING **: Theme parsing error: gtk-apps.css:463:23: 'px' is not a valid color name
```

---

### Post by Dannyv2003 on 2013-08-08
It also does that every time it works.

---

### Post by steeldriver on 2013-08-08
I've seen a few threads in other forums where nautilus startup issues seem to have been solved by clearing the gvfs-metadata cache

```
rm -r ~/.local/share/gvfs-metadata/
```

and then log out and back in

DISCLAIMER: I don't know enough about gvfs to understand if this has any downsides, however I have tried it on my own system and it does not appear to break anything.

---

### Post by Dannyv2003 on 2013-08-08
That did not work.

---

### Post by QDR06VV9 on 2013-08-08
> **Dannyv2003 said:**
> That did not work.

try this.
Code: gksu-properties
The program 'gksu-properties' is currently not installed. You can install it by typing:
sudo apt-get install libgksu2-0


Then retype "gksu-properties"
You should then see a box with a dropdown bar, click the bar and choose "sudo" close all should be good!
you may have to be root for the "gksu-properties" command.
and heed anns advice using the gksudo command.

---

### Post by Dannyv2003 on 2013-08-09
Still does not work, but thanks.

---

### Post by bapoumba on 2013-08-09
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/762167](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/762167)
sudo apt-get install gtk2-engines-pixbuf should fix the first error.

But : [https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1052353](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1052353) prompts me to ask what them are you using ? Could you please try with one of the standard ones even before trying the first workaround ?

---

### Post by Dannyv2003 on 2013-08-09
Installing it does not work. I am using GNOME 3 with the theme Google+ with Faience.

---

### Post by bapoumba on 2013-08-09
> **Dannyv2003 said:**
> Installing it does not work. I am using GNOME 3 with the theme Google+ with Faience.

Could you please try with one of the standard themes (radiance/ambiance) ?

---

### Post by mc4man on 2013-08-09
> **bapoumba said:**
> Could you please try with one of the standard themes (radiance/ambiance) ?

I would go with that. Whatever theme you're using seems quite poorly done. The "Unable to locate theme engine in module_path: "pixmap" warnings are not that critical but the theme parsing errors  likely are.

---

### Post by bapoumba on 2013-08-10
> **mc4man said:**
> I would go with that. Whatever theme you're using seems quite poorly done. The "Unable to locate theme engine in module_path: "pixmap" warnings are not that critical but the theme parsing errors  likely are.
+1, thanks for the input (I'm not much into these theme thingies). I did ask a couple posts back. I'm not seeing these issues with the ubuntu provided themes.

---

### Post by Dannyv2003 on 2013-08-10
I did trie that as part of my troubleshooting.

---

### Post by Dannyv2003 on 2013-08-10
It always worked well with this theme setup.

---

### Post by mc4man on 2013-08-10
> **Dannyv2003 said:**
> It always worked well with this theme setup.
You might want to see if system wide or something local to your user.
To do that create a new user with account type of Administrator
Login into that user & see if it works there (you can remove that user after testing

---

### Post by Dannyv2003 on 2013-08-11
it is system wide.

---

### Post by mc4man on 2013-08-11
Can you do anything with with gksu(do) like - 
gksudo gedit

If so then you could open a root terminal, go alt+f2, use  this command -

```
gksu /usr/bin/x-terminal-emulator
```
Then run nautilus from it

Or just open a normal terminal, run this,  ( 2 separate  commands,
```
sudo -i
nautilus
```

Edit: even though what you've presented seems to indicate having gksu set to sudo mode it won't hurt to ck.
Run this, should show sudo, not su. If it shows su then change in dropdown
```
gksu-properties
```

---

