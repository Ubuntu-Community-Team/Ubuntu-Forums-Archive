---
title: "Add/Remove Disappeared"
date: 2008-07-02
forum: General Help
---

### Post by rashwan on 2008-07-02
Salam Alikom "Peace On You"

Sorry for disturbing but the "Add/Remove" icon disappeared from the Applications Menu

"sudo apt-get install gnome-app-install" didnt solve anything

also the Add/Remove are Installed and i can reach it through Menu Editor
but when i try to check on it...it uncheck itself Automatically

as shown here [http://img372.imageshack.us/img372/9566/screenshotbw2.png]("http://img372.imageshack.us/img372/9566/screenshotbw2.png")
 
appreciate any help
sorry again

---

### Post by iaculallad on 2008-07-02
Drop to your terminal:

```
gksudo alacarte
```

Click on "Applications" and on the right-window pane, place a check mark on the "Add/Remove" check box.

EDIT: Disregard the post, I didn't see the attached picture.

---

### Post by aysiu on 2008-07-02
Sounds as if you might have some kind of screwy permissions. Enter this command in the terminal: ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

---

