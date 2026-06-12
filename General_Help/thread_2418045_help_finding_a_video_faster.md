---
title: "help finding a video faster"
date: 2019-04-30
forum: General Help
---

### Post by COKEDUDE on 2019-04-30
Is there a way to make this search faster? It takes about 30 minutes. Its a video so I figured I could say larger than 100 MB. It contains Mark so I added name. What else could I do to make the search faster?

```
find / -type f -name "*Mark*" -size +100M 2>/dev/null
```

---

### Post by Holger_Gehrke on 2019-04-30
Unless you're in the habit of copying / moving files with 'sudo cp' / 'sudo mv' you can forget about almost all the directories in / since they are not writeable to normal users. Give multiple starting points for directories where a normal user could have put the file:
```

find /tmp /media /home -type f -name "*Mark*" -size +100M 2>/dev/null
```
If you've got some other user-writeable directories (let's say nfs or samba shares in /srv)  put them before the first option. This should shorten the search time some.

Holger

---

