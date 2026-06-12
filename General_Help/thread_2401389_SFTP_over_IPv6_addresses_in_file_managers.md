---
title: "SFTP over IPv6 addresses in file managers?"
date: 2018-09-17
forum: General Help
---

### Post by The Cog on 2018-09-17
Do any Ubuntu file managers support sftp over IPv6? On command line I can use scp to copy files over IPv6, e.g. 
```
scp test.csv [fc00::1]:/home/steve/test/
```
so I know that ssh and scp are working and so does command-line interactive sftp:
```
sftp [fc00::1]
``` 
but if I try to enter address "sftp://[fc00::1]/home/steve" into thunar, I get an error popup:
```
Failed to open "steve" 
Connection failed
```

---

### Post by The Cog on 2018-09-26
Bump?

---

