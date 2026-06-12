---
title: "Disk Utility no S.M.A.R.T Status"
date: 2016-09-29
forum: General Help
---

### Post by bookie2 on 2016-09-29
I have S.M.A.R.T activated in the Bios but Disk Utility is not giving me the option to check them?
Is there a better way from command line to get a up to date view of the state of the drives?
Disk Utility says OK to all drives but I still would like to check....

bookie32

---

### Post by westie457 on 2016-09-29
Hi
```
sudo apt-get install smartmontools
``` to install.
For usage instructions ```
man smartctl
```

---

### Post by howefield on 2016-09-29
Are you sure ?

Click on the hamburger menu in the Disks utility to start S.M.A.R.T tests or highlight the relevant disk and use the keyboard short cut Ctrl+S

---

### Post by bookie2 on 2016-09-29
No S.M.A.R.T is in the menu to choose:

---

### Post by jeremy31 on 2016-09-29
See if CTRL + s brings up the SMART tests

---

### Post by howefield on 2016-09-29
> **bookie2 said:**
> No S.M.A.R.T is in the menu to choose:

Not that menu.. the hamburger menu in the window header on the right hand side of the window (to the left of the minimise button - three horizontal lines), or as stated Ctrl+S :)

---

### Post by bookie2 on 2016-09-29
Bloody hamburger menus...;)
OK! Panic over found it....lol

Sorry, forgot to say thanks to all here!

bookie32

---

### Post by howefield on 2016-09-29
> **bookie2 said:**
> Bloody hamburger menus...;) OK! Panic over found it....lol

Get used to it, they are ever more prevalent, popping up in more and more applications :)

Anyway, glad you got there.

---

