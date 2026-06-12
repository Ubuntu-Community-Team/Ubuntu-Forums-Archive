---
title: "Create executable links"
date: 2014-05-06
forum: General Help
---

### Post by darko4 on 2014-05-06
Hi all...

I'm kinda new to ubuntu and linux generally and I want to know how to make desktop link to some command... let's say that in terminal i run the command as "optirun firefox" without quotes.
Now, I want to make desktop link to that command a.i. when I double click the link, the command runs and dorothy goes to wonder land.

thanks,
darko

---

### Post by Impavidus on 2014-05-06
Create a .desktop file and put it on your desktop or wherever you want. There are examples in /usr/share/applications.

---

### Post by darko4 on 2014-05-06
> **Impavidus said:**
> Create a .desktop file and put it on your desktop or wherever you want. There are examples in /usr/share/applications.

aaah ^^ :)

thanks a bunch

---

### Post by papibe on 2014-05-06
Hi darko4.

[Here]("http://askubuntu.com/questions/142159/desktop-shortcut-to-create-a-new-desktop-shortcut-doesnt-do-anything")'s how to do it.

Let us know how it goes.
Regards.

---

### Post by kc1di on 2014-05-06
Here is an example of a .desktop file based on you command "optirun firefox"

```
[Desktop Entry]
Version=1.0
Name=Optirun Firefox
Exec=optirun firefox <you will need the full path here to the program is located unless the executable is located in /usr/bin>
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox <again you'll need the full path to the Icon you want to use>
Categories=GNOME;GTK;Network;WebBrowser;

```

create the file similar to the one above and save it to```
 /home/<user name>/Desktop
```  it will then be shown on the desktop.  or if you save it to ```
/usr/share/applications
``` it will be place in the menu. in the case above it would show up under internet.  

good luck

---

### Post by darko4 on 2014-05-06
> **papibe said:**
> Hi darko4.

[Here]("http://askubuntu.com/questions/142159/desktop-shortcut-to-create-a-new-desktop-shortcut-doesnt-do-anything")'s how to do it.

Let us know how it goes.
Regards.

this is very helpfull,

thanks,
darko

---

### Post by darko4 on 2014-05-06
> **kc1di said:**
> Here is an example of a .desktop file based on you command "optirun firefox"

```
[Desktop Entry]
Version=1.0
Name=Optirun Firefox
Exec=optirun firefox <you will need the full path here to the program is located unless the executable is located in /usr/bin>
Terminal=false
[COLOR=#008000]X-MultipleArgs=false[/COLOR]
Type=Application
Icon=firefox <again you'll need the full path to the Icon you want to use>
Categories=GNOME;GTK;Network;WebBrowser;

```

create the file similar to the one above and save it to```
 /home/<user name>/Desktop
```  it will then be shown on the desktop.  or if you save it to ```
/usr/share/applications
``` it will be place in the menu. in the case above it would show up under internet.  

good luck

thank you very much...
i c this text [marked green]... is it somehow connected to the output. what i mean, can I direct the link to which display to show executed link. i've notebook screen and external vga [crt] monitor, the latter being left of nb screen. now, when i execute desktop link, it's shown at vga screen, and i want it to be displayed at nb screen, which is... right.

thanks,
darko

---

