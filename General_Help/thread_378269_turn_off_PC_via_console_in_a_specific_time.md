---
title: "turn off PC via console in a specific time?"
date: 2007-03-07
forum: General Help
---

### Post by jfca283 on 2007-03-07
what do i write in the console to turn off my PC in a hour that i specify?
e.g. 1935 hrs?
or when amarok or totem end of playing their playlists?
must i write it like root or user?
thanksfor your responses

---

### Post by 23meg on 2007-03-07
Use *shutdown*.

```
sudo shutdown -h number_of_minutes 
```

or

```
sudo shutdown -h HH:MM 
```

---

### Post by jfca283 on 2007-03-07
there is no intention to make a program like kshutdown for gnome?
i'm testing the command
tomorrow i'll say if it works...

---

### Post by gradedcheese on 2007-03-07
> 
i'm testing the command
tomorrow i'll say if it works...


This command is old, very very old.  Like... probably more than 10 years old.  I'll wager that it works well ;)

---

### Post by jfca283 on 2007-03-07
it works fine
thanks

---

