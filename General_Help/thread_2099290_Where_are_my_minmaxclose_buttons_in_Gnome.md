---
title: "Where are my min/max/close buttons in Gnome??"
date: 2012-12-29
forum: General Help
---

### Post by oxf on 2012-12-29
The title says it all!

After a fresh install of 12:10 I installed Gnome session fallback as I prefer Gnome over Unity. But I have no buttons to minimise or maximise or even close windows and have to resort to right clicking and close that way. Whats happened?

Thanks
Caitlin

---

### Post by ibjsb4 on 2012-12-29
Are you running metacity or compiz?

Could try reinstalling the gnome-panel.

---

### Post by oxf on 2012-12-29
> **ibjsb4 said:**
> Are you running metacity or compiz?

Could try reinstalling the gnome-panel.

The default which is metacity, I think??

Anyway thanks, yes reinstalling it seems to have fixed it :)

---

### Post by ibjsb4 on 2012-12-29
Good deal; want them on the right?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons)

---

### Post by oxf on 2012-12-29
> **ibjsb4 said:**
> Good deal; want them on the right?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons)

thanks... that was my next tweak.
Thanks

---

### Post by oxf on 2013-01-01
> **ibjsb4 said:**
> Good deal; want them on the right?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons)

This is really weird!
This command used to work now it doesn't. Despite me tryimg over and over the buttons remain stuck on the left! whats going on?...........................:mad:

---

### Post by stinkeye on 2013-01-01
Now in dconf.
You can use **dconf-editor**

or

Move buttons to right using Terminal...
```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

---

### Post by pierceTN on 2013-01-01
One way you can do this is by installing the gnome tweak tool.

Install by putting this in terminal and pressing enter:

sudo apt-get install gnome-tweak-tool


Open it up, then go to the "shell" tab and enable the minimize or maximize button.





-Pierce

---

### Post by oxf on 2013-01-02
> **stinkeye said:**
> Now in dconf.
You can use **dconf-editor**

or

Move buttons to right using Terminal...
```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```


Thanks that worked!  
The other command in the link used to work but maybe something changed in Quantal? Anyway its sorted ;)

@pierceTN: Yes I have tweak tools installed didn't realise you could do it from there also, thanks.

---

