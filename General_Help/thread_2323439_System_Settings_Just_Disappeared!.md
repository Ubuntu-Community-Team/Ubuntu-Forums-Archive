---
title: "System Settings Just Disappeared?!"
date: 2016-05-05
forum: General Help
---

### Post by utnubu4 on 2016-05-05
My laptop was fine last night but when I powered it up today I had noticed that the system settings has disappeared from the side bar, so I clicked on the power button to try and access the system settings that way, but it dose not work. I have rebooted my laptop with no success.  Please help me if possible guys, this is very strange and I really need access to my system settings.

---

### Post by QDR06VV9 on 2016-05-05
> **utnubu4 said:**
> My laptop was fine last night but when I powered it up today I had noticed that the system settings has disappeared from the side bar, so I clicked on the power button to try and access the system settings that way, but it dose not work. I have rebooted my laptop with no success.  Please help me if possible guys, this is very strange and I really need access to my system settings.
In your thread title it shows Ubuntu...so** i am Assuming you are using unity**
You may have accidentally removed some packages (or some dependencies which caused the package to uninstall). In any case, you may try installing (or re installing) this package 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by utnubu4 on 2016-05-06
> **runrickus said:**
> In your thread title it shows Ubuntu...so** i am Assuming you are using unity**
You may have accidentally removed some packages (or some dependencies which caused the package to uninstall). In any case, you may try installing (or re installing) this package 
```
sudo apt-get install ubuntu-desktop
```

Yeas I am using Ubuntu and I must have removed some packages by accident.

Thank you very much for the help, that command worked like a charm and I have my system settings back again :)

---

### Post by QDR06VV9 on 2016-05-06
Good Job! And Glad to help.:)

---

