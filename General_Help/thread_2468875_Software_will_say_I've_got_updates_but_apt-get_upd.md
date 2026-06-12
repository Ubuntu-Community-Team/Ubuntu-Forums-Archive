---
title: "Software will say I've got updates but apt-get updates won't show any."
date: 2021-11-12
forum: General Help
---

### Post by josefranw on 2021-11-12
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289460&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289461&stc=1[/IMG]

---

### Post by deadflowr on 2021-11-12
Those are probably all Ubuntu's snap packages which also can be installed and updated in Software.
To see snaps in command line run
```
snap list
```
to update snaps in command lne run
```
snap refresh
```
to see more info
```
snap help
```

snap packages all completely different from the normal apt packages.

---

### Post by grahammechanical on 2021-11-12
If you update through Software Updater then Snap packaged applications will get automatically updated. But updating through the apt command does not update snap packaged applications.

Regards

---

### Post by josefranw on 2021-11-15
Thanks for the info..

---

