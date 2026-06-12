---
title: "samba and authentication"
date: 2004-11-15
forum: General Help
---

### Post by wilhelm on 2004-11-15
i am having a migth troubles with browsing windows shares...
one of the window shares, is not pass protected, with read access, when i go to that share , a popup window requesting user:pass comes up, i leave everything empty and  i get in and browse the share ( winxp).

then when i want to access the office share (w2kserver), where i need me domain user:pass to access the share, it doesn't pop up the window requesting the user:pass, and i can't get into the share, it just tells me i don't have permission to access the folder. 

btw i am doing this all via GUI

any ideas ?

---

### Post by ynef on 2004-11-15
See if it works when you mount from the command line, so you know for sure if it's samba's fault or the gui's.

---

### Post by Klunk on 2004-11-15
It is probably a fault with windows. When you connect to a machine with windows you cannot reconnect with different credentials. This happens with all windows shares.

In my office if I connect to my own home drive I cannopt connect to another home drive on that server as a different user.

What happens if you specify a password with the first request ? Can you make the first share not even prompt for a userid / password

---

### Post by spirospr on 2004-11-15
It is a windows problem. Use windows wizard to set up a home network select your prefered choices and after  i believe you will not have any problem accesing the shared docs of that pc

Does anyone have any idea how to make samba be active after boot up? Because every time i restart i have to activate samba.

---

