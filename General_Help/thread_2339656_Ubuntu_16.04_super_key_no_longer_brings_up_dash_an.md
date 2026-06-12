---
title: "Ubuntu 16.04 super key no longer brings up dash and managing keybindings"
date: 2016-10-11
forum: General Help
---

### Post by jbodhorn on 2016-10-11
I was trying to change the super key's keyboard binding so that it worked differently and now I can't seem to reset it back to default. In this case my windows key is my super key, 

I was trying to set super to spread all windows instead of open the dash/search so it acts more like it does in gnome. 

I installed the unity tweak tool and when trying to set spread all windows to just <super> nothing happened, I could set it to <super> + <any other key> but not to <super> alone. 

I went into system settings, keyboard, shortcuts and set <super> + "l" to search assuming this would leave <super> open and allow me to set <super> as spread all windows. Unity tweak tool still will not let me set <super> to spread all windows, now pressing super alone or holding it down does nothing

Ideally I would like super to spread all windows when tapped and show the short cuts menu when held. At this point I'd be grateful to just have ALL my keyboard shortcuts reset to default.... I'd like to reset the keyboard shortcut all back to default and then if possible set my super key to spread all windows

I seriously installed Ubuntu because I wanted something low maintenance and easier to use for daily use than Arch Linux is, I'm not off to a good start...

---

### Post by mc4man on 2016-10-11
You could try to reset compiz back to defaults, done with 2 commands - 
```
dconf reset -f /org/compiz/
```
```
setsid unity
```

May be better to just set all gsettings back to install defaults & then be more careful about what you try to change.
The super button is already set to do 2 things, (tap opens Dash, press opens shortcut overlay) & is also used as a modifier for other things. (super+l is set to go to lockscreen
The keyboard bindings in system settings are gnome bindings, compiz/unity have their own.

To reset back to default install gsettings - 
boot up, at login screen go - 
ctrl+alt+F3
login using your username & password
Execute this command
```
mv .config/dconf/user .config/dconf/user.bak
```
then - ```
sudo reboot
```

Personally I prefer compizconfig-settings-manager to set/adjust compiz settings rather than that ubuntu tweak app, more descriptive & it has a reset to defaults button for most options.
As far as the spread, it probably should be a 2 key binding unless you have a single key that does nothing atm. (forget just plain super..

---

### Post by jbodhorn on 2016-10-12
I managed to get things reset back to default. The one thing that bothers me so much about Ubuntu is how much of a PIA it is to customize, the only reason I'm using it is because I installed and it worked which is less than I can say for other *nix on this laptop, I was able to get to a DE first boot... Fedora crashes due to driver conflicts. I'm fighting with Arch trying to get the right drivers so I can boot into gnome, atm in arch I had to turn off gnome cause it just crashes

---

