---
title: "Left clicking not working with Mouse Keys in Keyboard Accessibility"
date: 2007-11-29
forum: General Help
---

### Post by Lr5 on 2007-11-29
//Ubuntu 7.10 standard desktop computer version, normal live cd install

I was using mouse keys in keyboard accessibility preferences (System - Preferences - Universal access - Keyboard accessibility), and that worked fine until I changed some keyboard shortcuts (volume up and down) in System - Preferences - Keyboard shortcuts. Now, instead of left clicking, when I press 5 on numpad, it right clicks.

Anyone got any idea how to fix this? I already tried changing mouse settings to left handed, no success. Deleting the keyboard shortcuts I set didn't help either. Perhaps a configuration file somewhere went wrong or something like that?

---

### Post by Lr5 on 2007-12-01
Tried if lsof-ing told anything about where the settings are stored, but didn't help.

---

### Post by erginemr on 2007-12-01
Hello,

I am also using this wonderful feature of Linux from time to time. To make sure that you are aware of all the shortcuts, I will take the opportunity to list them here:

To begin with, you control the mouse with the several buttons of your numeric pad section of your keyboard. Then, you control it with the following commands:

Shift+NumLock: Enables / Disables Keyboard Mouse Control
Button 5: Used for left / right / middle clicking depending on the modifiers below
Button /: Enables left-clicking, click with 5
Button *: Enables middle-clicking, click with 5
Button /: Enables right-clicking, click with 5
Button 0: Starts selecting text, end the action with 5
Arrow Keys: Mouse movement

The killer fact here is that, the system remembers the last modifier pressed, so left/right/middle clicking persists between successive Shift+NumLocks.

---

### Post by Lr5 on 2007-12-01
Thanks, that solved the problem. Didn't know about those other buttons.

---

### Post by erginemr on 2007-12-02
You are welcome.

Can you also please mark your thread as solved from the Thread Tools menu at the top of this page?

Cheers!

P.S. FYI, I have learned a lot (including the mouse control above) from the following tutorial site: [http://www.tuxfiles.org/](http://www.tuxfiles.org/) 
The articles therein are basic and are full to the brim with funny jokes and remarks. You may also benefit from it. Take Care.

---

