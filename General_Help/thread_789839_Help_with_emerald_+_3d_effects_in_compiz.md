---
title: "Help with emerald + 3d effects in compiz"
date: 2008-05-10
forum: General Help
---

### Post by EpiLife on 2008-05-10
I´m new to linux (been using it for about 2hours) so please regard me as a novice. I´ve managed to get my video drivers (restricted) to work for my ati x200m, enabled xgl, installed compiz and emerald on my fresh installation of Hardy.

However none of the 3d effects in compiz work and no themes in emerald can be ¨enabled¨. All I get is the default red windows with transparency and things such as wobbly windows and fade animations. No Cube or other 3d effects. (activating cube leads to leaving me with only 1 work space)

---

### Post by Exsecrabilus on 2008-05-10
For emerald window borders, you need to import .emerald files manually from the Emerald Theme Manager.

---

### Post by EpiLife on 2008-05-10
I have downloaded a few themes and imported them in theme manager, they show up with screenshots, however they do not apply on my GUI. matter of fact i dont rly see an apply button anywhere. And for compiz changes i do in System>Preferences>Advanced Desktop Settings lead to the function in question to completely stop working usually, and not only for 3d effect. Only default effects are working.

---

### Post by Exsecrabilus on 2008-05-10
You just click on it.

Run this command:
```
sudo apt-get install fusion-icon
```

Now go **Applications** >> **System Tools** >> **Fusion-Icon** or press Alt+F2 and type in *fusion-icon*.

A new applet will appear in your panel. Right-click on it and **Select Window Decorator** >> **Emerald**.

See if that works.

---

### Post by eheyl on 2008-05-10
I'm having the same issue. The themes are imported into emerald, but don't activate. I'm using Nvidia Geforce 5200 FX with the restricted drivers. It worked in 7.04. Not a really big deal as everything works, but the option to change skin would be nice. Any thoughts??

---

### Post by EpiLife on 2008-05-10
i had already done that, it wasnt the problem...however just did <ctrl><alt><backspace> and it automaticaly switched to the selected theme. Going through the theme manager i cant change it unless i restart my session every time. But now im happy with the current theme so time to focus on compiz as the problem still persists there.

---

### Post by Chudilo on 2008-05-10
[LIST=1]
[*]Open CompizConfig Setting Manager or Advanced Desktop Effects Settings
[*]Scroll Down to Effects
[*]Click on Window Decoration (On the actual Icon, not the checkbox)
[*]under "Command" replace whatever is in there with: emerald --replace
[/LIST]

That's it!

---

### Post by eheyl on 2008-05-11
It worked! thanks!

---

### Post by EpiLife on 2008-05-11
Works thx

---

