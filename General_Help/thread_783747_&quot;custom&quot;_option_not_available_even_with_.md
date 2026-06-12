---
title: "&quot;custom&quot; option not available even with manager"
date: 2008-05-06
forum: General Help
---

### Post by kylefiechter on 2008-05-06
So I can now enable "extra" visual effects on my ancient Latitude C610, but I cannot enable "custom" effects because it is not an option under appearance preferences. I tried the ol' sudo apt-get install compizconfig-settings-manager, but it told me that I already have the latest version. Any help would be much appreciated.

---

### Post by tommyhakinen on 2008-05-06
if that's the case. go to System > preferences > Advanced Desktop Effects Settings. That's where you configure your Compiz-Fusion.

To enable it, press Alt + F2, then type

> compiz --replace

---

### Post by mtbsoft on 2008-05-06
I have the same issue but found that there is a ccsm entry in the main menu which let me access all the settings.  After configuring the custom settings through this, the Custom button is still missing but all three radio buttons are off and the customs settings work just fine.

Hope that works for you too.

---

### Post by gcbzzzz on 2008-05-06
this completely sucks because I can't keep swtiching from off, and custom.

I need to do that to use games. compiz does not work with enemy territory.

will have to start saving the custom settings and doing a 7 step process every time i stop playing...


...will never understand why features always get removed.

---

### Post by mtbsoft on 2008-05-06
> **gcbzzzz said:**
> ...will never understand why features always get removed.
My suspicion is that the feature hasn't been removed, just broken.  

I expect that the code tests for a suitable driver/whatever to determine if there is any point displaying the "Custom" option for a card which cannot use it - if it cannot find such a card it doesn't display the option;  certainly that's one way I would code it, rather than just display it disabled.  If this detection code is broken then it would explain being able to configure via CCSM while having to use an alternative route to run it.

I would expect to see the detection code fixed in the none too distant future.  I know it's a pain for you to have to switch off one way and switch on another, perhaps you could write a script to toggle it.

---

### Post by tommyhakinen on 2008-05-06
try installing fusion icon then. I can switch easily between Compiz and Metacity using Fusion Icon.

> sudo apt-get install fusion-icon

You will find it under System Tools after installation.

---

### Post by RAOF on 2008-05-06
> **mtbsoft said:**
> My suspicion is that the feature hasn't been removed, just broken.  
...

Or not even broken; just changed :).  You need to have the 'simple-ccsm' package installed before the "Custom" button will show up.  Previously it would only display if ccsm was installed, but since that's a huge pile of by-design craziness...

---

