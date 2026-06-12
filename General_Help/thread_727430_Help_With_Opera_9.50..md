---
title: "Help With Opera 9.50."
date: 2008-03-17
forum: General Help
---

### Post by rickrob on 2008-03-17
Everytime i start opera i get this:attached screen shot.What?Deos anybody know what i could do to correct this?Mind you this browser is still in the beta stage.

---

### Post by scragar on 2008-03-17
when I had this problem using opera 9.25 I just killed all opera processes```
killall opera && sleep 10s && killall -9 opera
```then re opened opera before making sure to close it off fully using file > quit (or ctrl+q if your lazy :P), next time I booted it the error was gone.

if that doesn't work you could always try deleting it and repasting it back into itself, see if it was just an error with the file:
```
cat ~/.opera/lock > ~/tmp && mv ~/tmp ~/.opera/lock
```

---

### Post by rickrob on 2008-03-17
Thanks,first command and restart did the trick.

---

