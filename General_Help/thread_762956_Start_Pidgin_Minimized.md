---
title: "Start Pidgin Minimized"
date: 2008-04-22
forum: General Help
---

### Post by gavinjb on 2008-04-22
Hi,

I am trying to get Pidgin to Start Minimized in the tray, but nothing seems to work, I have tried checking the option in extended preferences, but this doesn't seem to work when Pidgin is set to auto start through sessions (it used to work when running Gaim on Edgy/Feisty), but strangely if I start Pidgin manually it seems to start minimized, anyone with any ideas?


Gavin,

---

### Post by gavinjb on 2008-04-30
Can anyone help on this or is using kopette or amsn a solution

---

### Post by ryanhaigh on 2008-04-30
It is probably something to do with the panel not being loaded yet when pidgin tries to start, you could change the command you have used in sessions from just pidgin to something like
```

sleep 10 && pidgin

```
The sleep command will create a delay before proceeding, obviously you can change this time to suit your system.

---

### Post by gavinjb on 2008-04-30
Thanks, I will give that a try, strange how I never had problems on Fiesty when I was running Gaim.

---

