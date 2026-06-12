---
title: "automatically update"
date: 2006-08-29
forum: General Help
---

### Post by maxdevis on 2006-08-29
how can i make my ubuntu server make herself update twice a week automatically.
i need to do it in the terminal.

thanks

---

### Post by mssever on 2006-08-29
Type```
sudo crontab -eu root
``` and insert the following line:
```
0       1       *       *       2,5   /usr/bin/apt-get update && /usr/bin/apt-get upgrade
``` 
Save and exit the editor.

---

