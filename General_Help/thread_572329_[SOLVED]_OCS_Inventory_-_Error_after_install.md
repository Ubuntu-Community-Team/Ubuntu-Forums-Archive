---
title: "[SOLVED] OCS Inventory - Error after install"
date: 2007-10-10
forum: General Help
---

### Post by jumping_snake on 2007-10-10
I have an interesting issue that I've posted on the OCS forums, but haven't heard anything back yet. Therefore, I'm asking the greater Ubuntu collective for answers!

So here's the issue:
After I get OCS installed (running Ubuntu 7.04 Desktop on a virtual server), I can get in, get access to all of the functions, change the admin password, create a new user and everything is happy. But, as soon as I log out, I can never get back in. The main reason for not being able to get back in is because I can't enter anything into the login fields/all of the text on the page is missing. A screenshot of the page is included here in an attachment. You'll understand what I'm saying when you look at that!

Anyway I have no idea what to do! I've checked the Apache2 error file and saw that an index.php is missing, which I"m assuming is the main page. If the file is missing, wouldn't it not serve up a page, but just send a 404? Either way, I tried to copy the index.php from the ocs directory and that didn't solve the issue either.

ANY ideas would be greatly appreciated!!

---

### Post by jumping_snake on 2007-10-22
WOW! So it all turns out to be a simple fix: click the Language flag for whatever language you'd like everything to be in once you reach this screen....

After I clicked the British flag (English) then everything has worked great since!

---

