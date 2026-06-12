---
title: "3ddesk launch key issue"
date: 2005-07-30
forum: General Help
---

### Post by umdzig on 2005-07-30
Ok i have installed 3ddesk and it looks good. However i can not get it to launch via a key on my keyboard. I followed a how to in the forum:

```
Run "gconf-editor". Drill down to apps --> metacity --> global_keybindings. Find "run_command_1" and change it to your key such as "F12" or "<Control><Alt>S". Then in apps --> metacity --> keybinding_commands find "command_1" and set it to "/usr/bin/3ddesk".

```
When i press F12 nothing happens. Any ideas? Maybe my keyboard isnt setup correctly? I like this app and would like to have easy access to it to change my desktop.

---

### Post by vladuz976 on 2005-07-31
is it a mac keyboard? i had the same problem with a mac usb keyboard trying to configure F13 for 3ddesk. didn't work, but F12 did. 
maybe your F12 is already used by something else.

---

### Post by GilGalad on 2005-07-31
Another posibility is to use xbindkeys (and xbindkeys-conf for configuration). I am using it with 3ddesk as well and works fine.

---

### Post by umdzig on 2005-08-01
[QUOTE=GilGalad]Another posibility is to use xbindkeys (and xbindkeys-conf for configuration). I am using it with 3ddesk as well and works fine.[/QUOTE]

Can you post a how to so i can use xbindkeys as well?

---

### Post by GilGalad on 2005-08-01
[QUOTE=umdzig]Can you post a how to so i can use xbindkeys as well?[/QUOTE]
 You just need to run:

sudo apt-get install xbindkeys xbindkeys-config

The run

xbindkeys-config

and define there the keyboard shortcuts and actions: click 'New' in the bottom bar, then in the edit frameset intriduce a name, click on get key, hit a key on the white window that pops up and then type and action in the Action box. When clicking on Save it will save the shortcut to ~/.xbindkeysrc. Then run xbindkeys as user and voila.

Today I have discovered this application:
[http://www.gnomefiles.org/app.php?soft_id=1020](http://www.gnomefiles.org/app.php?soft_id=1020)
but haven't tried it yet.

---

### Post by umdzig on 2005-08-01
Thanks it worked, how do i get it so it xbindkeys starts automatically when i reboot my machine?

---

### Post by GilGalad on 2005-08-01
[QUOTE=umdzig]Thanks it worked, how do i get it so it xbindkeys starts automatically when i reboot my machine?[/QUOTE]
 System->Preferences->Sessions

In the new window click on "Startup Programs", then "Add" and type xbindkeys as the "Startup command"

---

