---
title: "Alacarte has stopped working"
date: 2006-12-25
forum: General Help
---

### Post by deanjm1963 on 2006-12-25
For some reason Alacarte has stopped working, it starts up and then gives up the ghost. I reinstalled it and still no luck, yet I have no problems running Alacarte as root user. Is there anything I need to edit/delete/refresh to get it up and running again? Any help would be greatly appreciated... cheers Dean.

---

### Post by kerber0s on 2006-12-27
I had this same problem a few weeks back. The problem was that I didn't have the correct permissions to access the ~/.config/menus directory. The owner of that directory was root instead of me. 
Try to change the ownership of that directory so you're the owner. That'll probably fix the issue.

sudo chown "username":"username" -R /home/"username"/.config/menus

or try this instead:

 sudo chown "username":"username" -R /home/"username"


Then try to open alacarte to see if the problem was fixed.

Replace "username" with your actual username

---

