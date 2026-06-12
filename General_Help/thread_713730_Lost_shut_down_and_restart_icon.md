---
title: "Lost shut down and restart icon?"
date: 2008-03-03
forum: General Help
---

### Post by ravindukelum on 2008-03-03
when i'm gonna shut down or restart ubuntu i cant get those button only have suspend log out such buttons so then how to shutdown or restart ubuntu?

---

### Post by Gen2ly on 2008-03-03
"restart" and "shutdown" can be typed from the terminal.  Type "sudo" before though. :)

---

### Post by taouk on 2008-07-11
I have the same problem, and although i can reboot or shutdown through the command line, my wife and kids cant.
Is there any idea how to show these buttons again?

---

### Post by Fire_Chief on 2008-07-11
In Hardy, go to System -> Administration -> Authorizations. 
Drill down in the tree to org -> freedesktop -> hal -> power-management.
You'll see a list of power related functions. Select an option and then on the right window pane, add the explicit user accounts you want to grant the rights to. After all changes are done, the buttons will appear on the shutdown menu.

Cheers!

---

### Post by taouk on 2008-07-11
Thanks, but i just found out that when i tried to change login window i unchecked the Show Actions menu checkbox. (Administration - Login Window - Local -Show Actions menu)

I checked it again and everything is OK.

---

