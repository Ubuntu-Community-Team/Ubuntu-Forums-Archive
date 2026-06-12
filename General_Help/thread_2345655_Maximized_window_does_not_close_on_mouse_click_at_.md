---
title: "Maximized window does not close on mouse click at the top right corner"
date: 2016-12-06
forum: General Help
---

### Post by jkos2 on 2016-12-06
Hello,
although this is probably not a bug, it makes using Xubuntu less comfortable to me. Before I switched to the Xfce + Compiz combination, I had been using Xfce with Xfwm4. Back then I had been used to throw the mouse pointer to the top right corner of the screen and click 'close' button to terminate a maximized window. Now, however, when I do this with the Compiz window manager, the close button is not registered and thus the window simply stays still instead of closing. Is there any known fix or a workaround to this?

Thanks.
Best Regards,
J. K.

---

### Post by vasa1 on 2016-12-06
Previously, if you moved your mouse to the top-right corner (till you could move it no more), the mouse pointer would be over the close button (for a maximized window). Now, it's not!

There could be at least two reasons:
[LIST]
[*]the change from xfwm4 to compiz has affected the exact placement of the close button vis-a-vis the corner of your screen
[*]your theme has changed so that there's now some padding between the close button and the corner of the screen.
[/LIST]

Related reading: [Fitts's UI Law Applied to the Web]("https://msdn.microsoft.com/en-us/library/ms993291.aspx")

---

### Post by jkos2 on 2016-12-06
Well, I guess the problem lays in Compiz. I have encountered this issue while using Compiz with different DE, too. I even have had this issue in distributions, that have Compiz preinstalled.

---

