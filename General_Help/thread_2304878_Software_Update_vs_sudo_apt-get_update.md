---
title: "Software Update vs sudo apt-get update"
date: 2015-11-30
forum: General Help
---

### Post by Ted_Reinke on 2015-11-30
After using sudo apt-get update in the terminal I used the GUI software updater.  The software updater found ~65 megs of packages mainly related to the linux image that sudo apt-get update did not install.
Is there another terminal command that needs to run after sudo apt-get update?

---

### Post by oldos2er on 2015-11-30
```
sudo apt-get dist-upgrade
``` ```
sudo apt-get update
``` just refreshes the package lists from the repositories; it doesn't actually upgrade anything on your system.

---

### Post by grahammechanical on 2015-11-30
Or, 

```
sudo apt-get upgrade
```

Software Updater shows us the result of running the apt-get update/upgrade commands.

Regards.

---

### Post by Ted_Reinke on 2015-11-30
Thanks for the clarification.  I will try both commands next time.

---

