---
title: "Troubles mapping a key in Compiz"
date: 2007-12-04
forum: General Help
---

### Post by Zolty on 2007-12-04
I followed  [http://ubuntuforums.org/showthread.php?t=563736]("this") guide on the ubuntu forums and have gotten far enough to install compiz on my TC1100 tablet computer.  There is a "Q" key on the side of the tablet which guide suggests I use for screen rotation.  I was able to get this rotation functionality tied to the correct key using the Metacity bindings, but as soon as I actiivate Compiz it stops working.

I noticed in the guide that I should expect this as Compiz will take over keybindings, so I go into the ccsm and check to make sure the command is bound to command 0, it is, then I check the actions tab to be sure the key is bound properly.  The Run Command 0 has a key value of DISABLED.  I can set it to a keyboard command like ctrl+alt+D, but it will not let me bind it to 0x9f as the guide suggests (it simply goes back to "disabled" when I hit OK).  I have also tried hitting the key when prompted for "New accelerator" and nothing happens when I hit any of the proprietary keys on the TC1100.  

Based on some advice from the #compiz-fusion irc channel on freenode I tried the Xen Command to see what is being returned from those key presses:

```
KeyPress event, serial 31, synthetic NO, window 0x6800001,
   root 0xc1, subw 0x0, time 2792056699, (276,-95), root:(283,464),
   state 0x0, keycode 159 (keysym 0x0, NoSymbol), same_screen YES,
   XLookupString gives 0 bytes:
   XmbLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x6800001,
   root 0xc1, subw 0x0, time 2792056699, (276,-95), root:(283,464),
   state 0x0, keycode 159 (keysym 0x0, NoSymbol), same_screen YES,
   XLookupString gives 0 bytes:
   XFilterEvent returns: False
```

Any help is greatly appreciated.

---

### Post by kelbizzle on 2007-12-06
Have you asked anyone in their forums? [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

---

