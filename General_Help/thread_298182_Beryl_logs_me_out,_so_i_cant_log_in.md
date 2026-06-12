---
title: "Beryl logs me out, so i cant log in"
date: 2006-11-12
forum: General Help
---

### Post by Dot Communist on 2006-11-12
So i added beryl to my System>pref.>Sessions>Srartup programs list, and when bryl loads it just logs me out, i need a way to:

A:acces my account to remove that from the startup list
or
B:remove Beryl from my comp


either would do ](*,)

---

### Post by aidanr on 2006-11-12
you should add "beryl-manager" to your startup, "not beryl"

boot up in recovery mode (press escape when grub is loading and choose the second option) 
```
cd /home/YourName/.config/autostart
mv beryl.desktop beryl-manager.desktop
nano beryl-manager.desktop

```
change the line that says
```
Exec=beryl
```
to
```
Exec=beryl-manager
```
"ctrl-o" to save, "ctrl-x" to exit, and then type "reboot" to reboot

---

### Post by Dot Communist on 2006-11-12
> **aidanr said:**
> you should add "beryl-manager" to your startup, "not beryl"

boot up in recovery mode (press escape when grub is loading and choose the second option) 
```
cd /home/YourName/.config/autostart
mv beryl.desktop beryl-manager.desktop
nano beryl-manager.desktop

```
change the line that says
```
Exec=beryl
```
to
```
Exec=beryl-manager
```
"ctrl-o" to save, "ctrl-x" to exit, and then type "reboot" to reboot
thx :D

---

