---
title: "wminput ir_pointer dual screen setup"
date: 2008-03-14
forum: General Help
---

### Post by ohzopants on 2008-03-14
I have a standard LCD (screen 0 in X) running at 1440x900 and a TV (screen 1 in X) running at 1360x768.  Everything works fine.

The TV is setup as a separate screen "to the right" of my monitor.

I've gotten wminput to work successfully with my wii remote, but I can't use the IR bar for pointing at the TV because the cursor is confined to the monitor.  I'm wondering if anyone can think of a way to either confine it to the second screen, or to just force some offset (1440, the width of my monitor) on the X coordinate it records.

I've tried adding '+ 1440' to the line in the configuration file, but then the program complains about an unexpected integer.

Any ideas?  Tilting the wiimote to move the cursor is annoying and very inaccurate.

---

### Post by davy014 on 2008-03-17
What is your xorg.conf ?

---

### Post by ohzopants on 2008-03-19
I'm at work so I don't have access to my xorg, but I know it's fine.  Are you looking for anything in particular?

I've gotten it to work properly, but only if the TV is "screen 0".  I do not want the TV to be screen 0 because the login screen always appears on that screen, and I need the login screen to appear on the LCD (since that's where my keyboard is).

Thanks for the reply though.

---

