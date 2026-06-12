---
title: "Hover Click Will Not Disable"
date: 2014-08-06
forum: General Help
---

### Post by Matt_Tarleton on 2014-08-06
Hello all,

I'm new to Linux but a Windows SysAdmin. I've got Ubuntu 14.04 running on my machine(bare metal, not a VM) and I cannot get hover click to disable. I've toggled the setting for it a dozen times, rebooted, check for updates, installed Unity Tweak Tool and CompizConfig Settings Manager and changed appropriate settings in both but I cannot get it to stop. The mouse works just fine in Windows, no random clicks there. It is a Tesoro Shrike H2L mouse. I can't for the life of me figure it out. Any of you have any ideas on how to fix? :)

---

### Post by mc4man on 2014-08-06
You've turned it off in System settings > Universal Access > Pointing & Clicking ?

---

### Post by Matt_Tarleton on 2014-08-07
Yepp I've toggled that a few times now and it simply will not go away.

---

### Post by mc4man on 2014-08-07
Well that's got to be really annoying plus, at least here, when dwell click is enabled one can't scroll in any gtk3 window with a mouse wheel..

Maybe try logging into a guest session & see if it's enabled there, if not then it's not a hardware issue.

The gsetting for this is org.gnome.desktop.a11y.mouse dwell-click-enabled so try - 
```
gsettings set org.gnome.desktop.a11y.mouse dwell-click-enabled false
```

To re-check - 
```
gsettings get org.gnome.desktop.a11y.mouse dwell-click-enabled
```

Edit: you could also try removing the app that does this - 
```
sudo apt-get purge mousetweaks
```
Then log out/in

---

### Post by Matt_Tarleton on 2014-08-08
Thank you mc4man, but unfortunately still seeing the behavior even after removing mousetweaks.

I can now confirm actually that the mouse clicks are totally random and not dependent on having just stopped movement. I got several random clicks while writing this reply and my hand wasn't even on the mouse. Sorry to have sent you barking up the wrong path. I tried a second USB mouse but saw the same behavior. Again, both work fine in Windows. The mouse is plugged directly into the PC so no hubs in the middle. 
I've also noticed that whatever window I already had open seems to stay on top and I cannot bring any other windows to the front.

---

### Post by mc4man on 2014-08-08
I guess I'd probably try a guest session or set up a new user & see if your issues occur there. **If not **then I'd try going back to the default user gsettings for your user. May be various ways but I do as such.

Set up a way to kill x, a simple *per session*  means would be to run this - 
```
echo 1 | sudo tee /proc/sys/kernel/sysrq
```

Then  - 
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak

```

Immediately after the above command, -  kill x by going Alt+Print+k  
This should kill x & bring you back to login screen. login & see..

If no go then if desired you can simply rm the new ~/.config/dconf/user file & rename the user.bak back to just user to get back your current settings

(- the reason for killing x after removing or renaming the user file is that in a normal logout/restart/shutdown  it is rewritten from memory so you'd just end up with what you had previously.

---

