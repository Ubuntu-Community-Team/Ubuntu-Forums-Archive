---
title: "What is the command for uninstallling software?"
date: 2007-06-18
forum: General Help
---

### Post by swoll1980 on 2007-06-18
Let me know please.

---

### Post by Medieval_Creations on 2007-06-18
Well if you know the name of the package it would just be apt-get remove... 
Example: 
   sudo apt-get remove gnucash

You can always go under System -> Admin -> Synaptic as well.  That's a GUI front end for apt you can just uncheck what you don't need.

---

### Post by CautionaryX on 2007-06-18
To uninstall a package that you downloaded from the repositories type

```
sudo apt-get remove <package-name>
```

or you could just run Synaptic and uncheck the packages you no longer need.

---

### Post by swoll1980 on 2007-06-18
how would you un install it im trying to do away with my gui all together

---

### Post by swoll1980 on 2007-06-18
Thanks

---

### Post by Medieval_Creations on 2007-06-18
sudo apt-get install <package-name>   ## Installs App
sudo apt-get remove <package-name>   ## Removes App
apt-cache seartch <text>   ## Will search the repositores for packages matching the text

Those are the 3 most common commands I use for apt.

---

### Post by H.E. Pennypacker on 2007-06-18
> **swoll1980 said:**
> how would you un install it im trying to do away with my gui all together

Use the server edition if you do not want GUI.

---

