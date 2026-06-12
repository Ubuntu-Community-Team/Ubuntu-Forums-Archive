---
title: "Ctrl+Alt+Left-click causes logout rather than rotate"
date: 2008-07-07
forum: General Help
---

### Post by ianoreo on 2008-07-07
When I hit ctrl, alt, and left-click to enable cube rotation my computer enables some sort of logout? I went to the prefs of rotate cube and saw that this was the initiate command. What should I set to get the manual rotation?

---

### Post by AmericanYellow on 2008-07-07
You most like set up the shortcuts wrong.

Check under System ---> Preferences --> Keyboard Shortcuts and make sure that the Logout shortcut is not assigned as Crtl + Alt + Left-Click (don't think its possible).

You can always reset the settings to default and start over.

To rotate the cube, you should be able to use the roller of the mouse/ scroller of the touchpad on the deskop to rotate, you can press Crtl + Alt + Left/Down/Right to turn the Left, unfold it, or turn it right.

Also by pressing the middle click on the desktop you can initiate the cube.

---

### Post by ianoreo on 2008-07-07
I don't really know if its a logout command. I just checked all the shortcuts and they are clear but I still get the same problem. What happens is I hit Ctrl+Alt then when I click the screen goes black then some weird DOS like thing then the login screen.

---

### Post by sayakb on 2008-07-07
Open CCSM (System->Preferences->Advanced desktop effects settings)
If you dont have CCSM, Install in by typing at a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Then at CCSM, press **Preferences** and click **Restore defaults**. Then enable the Cube, Rotate Cube, Cube Caps etc. and see if it works.

---

### Post by estyles on 2008-07-07
Ctrl+Alt+F1 (or F2, F3, etc...) opens up an xterm.  I think Ctrl+Alt+F7 will bring you back to Gnome if you're in an xterm (I might be wrong, can't check right now).  It sounds like there's something wrong with your shortcut to xterm and it's firing on Ctrl+Alt+Click...

---

