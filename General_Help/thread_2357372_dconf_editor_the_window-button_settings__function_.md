---
title: "dconf editor the window-button settings  function no useable"
date: 2017-04-01
forum: General Help
---

### Post by 243750496 on 2017-04-01
I set the key
```
org -> gnome -> desktop -> wm -> preferences -> button-layout  
```
Changing it to: 
```
close,minimize,maximize:  
```
Or use 
```
gsettings set  org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:'
```
Doesn't take  effect  
So any solutions?

---

### Post by deadflowr on 2017-04-01
What desktop environment?

---

### Post by 243750496 on 2017-04-01
> **deadflowr said:**
> What desktop environment?
Ubuntu budgie 17.04

---

### Post by deadflowr on 2017-04-01
Some digging it looks like it should be
com.solus-project.budgie-wm button-layout
so see what you get when you run
```
gsettings get com.solus-project.budgie-wm button-layout
```

---

### Post by 243750496 on 2017-04-01
> **deadflowr said:**
> Some digging it looks like it should be
com.solus-project.budgie-wm button-layout
so see what you get when you run
```
gsettings get com.solus-project.budgie-wm button-layout
```

i have changed it through dconf editor but still take no effect
```
atc@ATC:~$ gsettings get com.solus-project.budgie-wm button-layout
'minimize,maximize,close:appmenu'
```

---

### Post by deadflowr on 2017-04-01
> **243750496 said:**
> i have changed it through dconf editor but still take no effect
atc@ATC:~$ gsettings get com.solus-project.budgie-wm button-layout
'minimize,maximize,close:appmenu'

Sorry, not much more I can do.
But I have added a budgie-desktop tag to this thread, so maybe someone who runs budgie will see that tag or run across it in a search can help.
(Note in the coming weeks we will be adding a budgie prefix for thread titles)

---

### Post by vasa1 on 2017-04-02
One of the lead developers does visit Ubuntu Forums but another option is to visit [https://ubuntubudgie.org/support](https://ubuntubudgie.org/support) for further options.> We have two on-demand support routes - Gitter.im and IRC (internet relay chat)

---

### Post by davidmohammed on 2017-04-03
The additional gsetting key to change is org.gnome.settings-daemon.plugins.xsettings overrides - change the Decoration part of the key to change the layout

Suggestion would be to use dconf-editor to make this change.

---

### Post by dragonfly41 on 2017-04-03
I'm not sure but from earlier research I added here ... [https://ubuntuforums.org/showthread.php?t=2357465](https://ubuntuforums.org/showthread.php?t=2357465)

I believe that you may need to add a leading colon ... [COLOR=#ff0000]**:**[/COLOR][COLOR=#000000]*minimize,maximize,close:appmenu*[/COLOR]

Just recheck the syntax to be sure.

---

