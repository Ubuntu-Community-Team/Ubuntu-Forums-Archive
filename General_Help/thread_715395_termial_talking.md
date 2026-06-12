---
title: "termial talking"
date: 2008-03-04
forum: General Help
---

### Post by phlipp on 2008-03-04
Hope someone can help
I was installing a musc conversion tool on the through terminal but decided to abort. Now when I start the computer when I get to the main screen ther is a terminal window there and it starts to audible list languages. How do I get rid of it?:confused:

---

### Post by Rocket2DMn on 2008-03-05
Try running
```
sudo dpkg --configure -a
sudo apt-get autoremove
sudo apt-get remove *package_name_of_program_you_were_installing*
sudo apt-get update
sudo apt-get upgrade
```
Finally, if you have no GUI, start X
```
startx
```

---

