---
title: "open applications from other user account"
date: 2007-06-06
forum: General Help
---

### Post by vilto on 2007-06-06
how do i open application from other user accounts
ok i have two user accounts .................. now im logged in to first user ..... now i want second users gui applications to open in my first accounts
I tried THIS BUT NO USE :

su firstuser
Password

now i logged into first user account using su 
now when i tried to open firefox by typing firefox in terminal i get this error::



Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:25310): Gtk-WARNING **: cannot open display:

---

### Post by DagMan on 2007-06-06
try this.  I think it may work though I haven't used it specifically in that circumstance
```
xhost local:localhost
```

---

### Post by vilto on 2007-06-07
thanx alot woked like charm :-)

---

