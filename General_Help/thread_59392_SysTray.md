---
title: "SysTray"
date: 2005-08-23
forum: General Help
---

### Post by dJnEvS on 2005-08-23
I have installed mercury messenger as my MSN client..
but i want to have it in the systemtray.
only thing i need to know is the default 'java_home' directory..

could some1 tell me where i can find this?

thanks ^_^

---

### Post by arnieboy on 2005-08-23
[QUOTE=dJnEvS]I have installed mercury messenger as my MSN client..
but i want to have it in the systemtray.
only thing i need to know is the default 'java_home' directory..

could some1 tell me where i can find this?

thanks ^_^[/QUOTE]
It should be in */usr/lib/j2re1.5-sun* if u have installed java by doing:
```
sudo apt-get install sun-j2re1.5
```

---

### Post by dJnEvS on 2005-08-23
```
E: Couldn't find package sun-j2re1.5
```
i guess i need another source in sources.list..

---

### Post by arnieboy on 2005-08-23
[QUOTE=dJnEvS]```
E: Couldn't find package sun-j2re1.5
```
i guess i need another source in sources.list..[/QUOTE]
lots of people have reported probs with this package even with backports repos enabled. assuming u have backports enabled and u still cant install the java package, u can go to the java website and download and install the package from there

---

