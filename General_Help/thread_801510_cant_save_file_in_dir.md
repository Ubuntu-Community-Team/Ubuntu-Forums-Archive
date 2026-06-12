---
title: "cant save file in dir"
date: 2008-05-20
forum: General Help
---

### Post by kopiq on 2008-05-20
hi i cant save a file i download to a dir. the dir is /usr/share/rainlendar/skins. i dl a skin to that dir and it says i cannot change the folder contents. give it permission and try again. how do i do this?
thanks.

---

### Post by MaindotC on 2008-05-20
You may not have permission to save to that directory.  Save the file to the desktop, then move it with root permissions:
```

user~Desktop$ sudo mv filename /usr/share/rainlendar/skins

```

It should prompt you for the administrative password.  Check to make sure the file is in that directory by using the following "ls" command:
```

ls /usr/share/rainlendar/skins

```

---

### Post by kopiq on 2008-05-20
k i tired in terminal i got bash: user desktop$ command not found. sorry iam new to terminal

---

### Post by kopiq on 2008-05-20
hey i got it. i forgot to cd to desktop heheh. thanks alot! it worked. is there a way to change the dir so i dont have to do this everytime?

---

### Post by Kralizec on 2008-05-20
You can give yourself permission to modify that folder: in a terminal, do
```

sudo chown <your username here> /usr/share/rainlendar/skins
sudo chmod u+rw /usr/share/rainlendar/skins

```

chown **ch**anges the **own**er of the file and chmod **ch**anges the permissions (file **mod**e bits).

---

### Post by MaindotC on 2008-05-20
Glad to help - star me plz :)

---

### Post by kopiq on 2008-05-21
thanks everyone!

---

