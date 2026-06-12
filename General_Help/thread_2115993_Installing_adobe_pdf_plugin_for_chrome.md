---
title: "Installing adobe pdf plugin for chrome"
date: 2013-02-14
forum: General Help
---

### Post by jpr0 on 2013-02-14
Hi 

I'm trying to disable the default pdf plugin for chrome and to use the adobe plugin. Does anyone know how to accomplish this? 

If you go to chrome://plugins you can disable the default pdf reader there, but now I have no idea how to install adobe reader for chrome... 

Thanks a lot

---

### Post by gordintoronto on 2013-02-14
You can install the Adobe Reader from Software Centre, Synaptic, apt-get, etc. It's called acroread.

In Chrome help, it says this:
In Adobe Reader, go to Edit > Preferences.
Click Internet on the left.
[Select the "Preview PDF in browser" checkbox at the top (may also be called "Display PDF in browser"). If the checkbox is already selected, you may have to deselect it, click OK, then access Preferences again to reselect it.] ***I did not see such a checkbox.***
***It did, however, ask for the name of the browser, which is google-chrome.***
Click OK.

And it didn't work the way you wanted. If I click on a PDF in Chrome, it gets downloaded, and then I select the "open" option to view it, offline, in the Adobe Reader. I actually prefer this method.

---

### Post by jpr0 on 2013-02-14
Hi

Thanks for the reply. I already tried this, although it was with Adobe Reader 9 (I think this is basically the same as acrobat reader). 

I also tried going to the menus you suggested and putting the browser information in, but it still didn't work. 

I really need to have the ability to display embedded pdf files in chrome like the one you see here: 

[http://www.qapla.com/mods/showthread.php/31-PDF-BBCode-Embedded-PDF](http://www.qapla.com/mods/showthread.php/31-PDF-BBCode-Embedded-PDF)

The reason why I need adobe (and not just the standard pdf viewer in chrome) is because I also need to be able to "silent print" pdf files (print them without a print dialog showing up). The only way I can see of achieving this is to use adobe reader in chrome.. but I just can't get it to work :/

---

### Post by mayagrafix on 2013-02-14
Try using Firefox :o

---

### Post by jpr0 on 2013-02-15
> **mayagrafix said:**
> Try using Firefox :o

I tried this too, but pdf objects are not rendered. It tells me I need a plug in. I click "look for suitable plugin" (or whatever), and it tells me there is no suitable plugin.

---

### Post by slickymaster on 2013-02-15
Once you've disabled the default pdf plugin for chrome and installed Adobe Reader, you have to go back to **about: plugins** and enable the Adobe PDF plugin.

---

### Post by jpr0 on 2013-02-15
I uninstalled adobe, then reinstalled it using a .deb package. 
The pdf plugin for firefox works now, but I need to change a setting in acroread. But when I try loading it from the console I get a load of warnings and acroread won't start: 

```

~$ acroread

(acroread:22711): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", 
[^ ^ the above line repeated about 20 times]
(acroread:22711): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module"
`menu_proxy_module_load': /usr/bin/acroread: undefined symbol: menu_proxy_module_load

(acroread:22711): Gtk-WARNING **: Failed to load type module: (null)

```

I have the canberra-gtk-module installed. Does anyone know how to fix this? I found a post on this forum: 

[http://superuser.com/questions/337639/how-to-fix-unable-to-locate-theme-engine-in-module-path-murrine](http://superuser.com/questions/337639/how-to-fix-unable-to-locate-theme-engine-in-module-path-murrine)

detailing a similar problem. I've installed all the gtk engines but the problems persists.

---

