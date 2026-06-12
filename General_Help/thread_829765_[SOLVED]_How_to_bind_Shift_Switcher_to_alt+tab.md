---
title: "[SOLVED] How to bind Shift Switcher to alt+tab"
date: 2008-06-15
forum: General Help
---

### Post by WonderStivi on 2008-06-15
I found a thread about this yesterday, however it didn't make any sense to me. Couldn't find it again, so asking here: How can I map the shift switcher in compiz to use alt+tab, instead of super+tab?

I'm on Hardy 8.04.

In advance, thanks.

Edit: Sorry, I found it myself. For those who might wonder, the GUI-way to solve it is: System -> Preferences -> Advanced Desktop Effects Settings -> Advanced Search -> Find Shift Switcher. There you can change bindings.

---

### Post by Rhubarb on 2008-06-15
First, install ccsm (compiz config settings manager)
```
sudo aptitude install compizconfig-settings-manager
```

Then go System --> Preferences --> CompizConfig Settings Manager
Scroll down to the bottom, uncheck Application Switcher.
Click on the Shift Switcher, click on the key bindings tab.
Then change Next Window to be bound to Shift + Tab rather than Super + Tab.

Edit:  Seems you figured it out anyway :)

---

