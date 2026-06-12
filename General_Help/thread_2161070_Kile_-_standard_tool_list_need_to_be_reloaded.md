---
title: "Kile - standard tool list need to be reloaded"
date: 2013-07-09
forum: General Help
---

### Post by dnova on 2013-07-09
I just installed Kile 2.1 on a fresh installation of Ubuntu 13.04.  While I open Kile, I get this message:
 > The standard tool list need to be reloaded because of the switch from KDE3 to KDE4. This will overwrite any changes in the tools you have made. Do you want to reload the list now (recommended)?



Whether I click Yes or No, the result is the same: Kile immediately closes.  When I restart Kile, the same message continues to appear.

Any thoughts for how I can get past this?  Thanks!

---

### Post by berlu42 on 2013-07-10
I experienced the same behaviour. The solution for me was to close the window by a click with the middle mouse button on the window (with the question) in the expose mode (Super+w). I hope this will help you as well.

---

### Post by dnova on 2013-07-10
I tried this, and it did not work.  Closing the window with the question, in the expose mode, still caused Kile to close as well.

---

### Post by dnova on 2013-07-10
I've solved it, and I post the method here in case anyone else encounters the same problem.  Somehow, I did not have the appropriate user permissions to update the tool list.  The solution is to run Kile as the superuser, and then click Yes in the offending dialogue box.  Close Kile, and run again, this time as the ordinary user.  Everything works fine, and the message about the "standard tool list" no longer appears.

---

