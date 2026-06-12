---
title: "unable to execute sudo add-apt-repository ppa:noobslab/themes"
date: 2013-07-31
forum: General Help
---

### Post by saurabh2 on 2013-07-31
Actually first i gave the command in terminal window..
sudo add-apt-repository ppa:noobslab/themes
then it asked me my password
after that it is not showing anything got stuck...
so i m unable to change ubuntu to mac theme:mad:

---

### Post by gifford on 2013-07-31
After adding the repository did you enter: sudo apt-get update in the terminal?

---

### Post by Frogs Hair on 2013-07-31
It may be a case of just trying again . Try the following. ```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo add-apt-repository ppa:noobslab/themes
``` If prompted to continue adding the repository enter yes/y.  ```
sudo apt-get update
``` Then use the theme installation command.

---

