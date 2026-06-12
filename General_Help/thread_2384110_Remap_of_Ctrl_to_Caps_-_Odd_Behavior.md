---
title: "Remap of Ctrl to Caps - Odd Behavior?"
date: 2018-02-02
forum: General Help
---

### Post by clalian on 2018-02-02
Hello, I am running the latest Xubuntu 16.04 from a recent fresh install. When Xfce starts, in the "Session and Startup" I have added the command: ```
setxkbmap  -option caps:ctrl_modifier
```  This remaps the left control key to the caps-lock key.  It is working is it should, except for one odd behavior: When I am inside phpStorm (the programming IDE by IDEA/IntelliJ), the caps-key (acting as Ctrl) does not "release".  As normal usage: If I press left Ctrl+Tab I get a list of the open files I have. I can tehn keep on pressing Tab until I get to highlight the file I want. I then release the left Ctrl+Tab combo, and I jump that that file.  Problem: If I do the same using the Caps+Tab, I get the lift of the open files. I keep on pressing tab until I highlight the file I want. Yet when I release the combo, the window stays open with the highlight file. I have to then press Enter in order to jump to the file.  Any suggestions on what to do? I tried running  ```
xinput test 10
``` And I can see echo'd the keys I press, yet I can't see echo'd when I press Ctrl (either left Ctrl, or the re-mapped Caps-ctrl).  Any suggestions?  Thank you!

---

### Post by bonzini on 2018-02-02
clalian, I too prefer the ctrl key between shift and tab but I use the ctrl:swapcaps setting, which exchanges the shift lock and the left control key.  I don't use phpStorm but I have to say that I've been using this setting for mmm 15 years? and I've never ever run into any problem with it.

---

