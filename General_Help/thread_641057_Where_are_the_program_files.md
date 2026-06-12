---
title: "Where are the program files?"
date: 2007-12-14
forum: General Help
---

### Post by Moonfrost on 2007-12-14
Hi I wanted to check my virtual machine created with VirtualBox. VirtualBox tells me the directory is /home/<username>/.VirtualBox/Machines...turns out I checked everywhere and that directory doesn't seem to exist. Also I used my file browser's search feature which I always use and it usually works...I don't know, anybody have any ideas? most programs I download or install from repos I can't never find their directories...only thing Windows had good, I'm kinda new to Linux specially Ubuntu and Gnome so any help would be appreciated!!!!

---

### Post by dpar on 2007-12-14
The .virtualbox directory is hidden, thats what the . means before the name. In nautilus, click on veiw and check 'show hidden files'

---

### Post by taurus on 2007-12-14
You mean you get an error message when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/.VirtualBox
```

---

### Post by ectospasm on 2007-12-14
/home/<user>/.VirtualBox is a hidden directory.  Searches and views will not work unless you elect to show hidden files.

---

### Post by Moonfrost on 2007-12-15
Thanks a lot to all of you!!! I'm gonna try nautilus since I'm new to Ubuntu and haven't tried much yet because I have Ultimate Edition and it has tons of extra software...

---

