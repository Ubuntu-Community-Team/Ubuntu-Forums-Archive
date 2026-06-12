---
title: "how to remove wine"
date: 2007-09-27
forum: General Help
---

### Post by usif on 2007-09-27
hey i installed wine and didnt run the thing i wanted it to run, now i want to remove wine but i dont know how?
can anyone help me

---

### Post by DagMan on 2007-09-27
Go to accessories-->terminal
and type the following
```
sudo apt-get remove --purge wine
```
Just in case, thought the above probably removed it, do this too.
```
rm -rf ~/.wine
```

---

