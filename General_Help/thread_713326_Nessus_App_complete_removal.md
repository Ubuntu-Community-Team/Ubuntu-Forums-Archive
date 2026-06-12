---
title: "Nessus App complete removal"
date: 2008-03-02
forum: General Help
---

### Post by G-Unot on 2008-03-02
Hi guys, i recently installed nessus and it would crash, so i tried removing it. then i deleted a couple of files that werent removed. then i tried installing nessus again it worked however until i ran it. i got this error msg

```
**** /var/lib/nessus/nessus-services could not be found. Install it and try again
```

is there a way to fix this? i think that completly removing it would maybe work then intalling it again. im not sure :confused:

---

### Post by Oldsoldier2003 on 2008-03-02
> **G-Unot said:**
> Hi guys, i recently installed nessus and it would crash, so i tried removing it. then i deleted a couple of files that werent removed. then i tried installing nessus again it worked however until i ran it. i got this error msg

```
**** /var/lib/nessus/nessus-services could not be found. Install it and try again
```

is there a way to fix this? i think that completly removing it would maybe work then intalling it again. im not sure :confused:
from a terminal:

```
sudo apt-get purge nessus
sudo apt-get update
sudo apt-get install nesus
```

---

### Post by G-Unot on 2008-03-02
okay now i get this when i reinstall 

```
mkdir(/var/lib/nessus/plugins/.desc) : No such file or directory
Couldn't open the directory called "/var/lib/nessus/plugins" - No such file or directory

```

---

