---
title: "my login font is giant - how to fix?"
date: 2008-04-27
forum: General Help
---

### Post by [DS]DragonSlayerz on 2008-04-27
When I login, whatever I type is giant.

Also, at the bottom left menu, if I click on the option, the Shutdown/Restart/ and such are giant as well.




[EDIT] I found the solution, had to add -dpi 96 to window login under security

---

### Post by theducks on 2009-08-07
Thank you 
I have been beating my head on this one.

To Clarify
On the Security tab (Jaunty) of the Login Window Administrative tool,
there is a button "Configure X Server..." .
Click that. Add the **-dpi 96** to the *end* of the contents of the  Command line.

---

