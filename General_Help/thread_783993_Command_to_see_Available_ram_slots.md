---
title: "Command to see Available ram slots"
date: 2008-05-06
forum: General Help
---

### Post by nikolas22t on 2008-05-06
Is there any command to see if there are any available ram slots on my server that runs ubuntu and also see the current ram slots and what ram are installed in each slot? ( I don;t have physical access at this time )

---

### Post by cdenley on 2008-05-06
```
sudo lshw
```

Towards the top, under "*-memory", it shows "*-bank:0", "*-bank:1"...

---

### Post by nikolas22t on 2008-05-06
dmidecode -q | less



Thats a nice command. Use it. Need root access.

---

