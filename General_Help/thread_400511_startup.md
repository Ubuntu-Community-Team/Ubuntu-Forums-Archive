---
title: "startup"
date: 2007-04-03
forum: General Help
---

### Post by celticbhoy on 2007-04-03
Having a startup problem and would like to know how to disable an entry from the start up program list from a terminal window. thanx in advance

---

### Post by sisco311 on 2007-04-03
to delete:
```
rm ~/.config/autostart/prog_name.desktop
```
where prog_name.desktop is the name of the startup prog

---

### Post by celticbhoy on 2007-04-03
is the startup folder /config/autostart   ????

---

### Post by spankymasterc on 2007-04-03
U can also go to System > Preferences > Session > Startup Programs and check there if you see somthing u dont want to start u can also add things u want to start on boot up :D :: Cheers:: and good luck....

---

### Post by sisco311 on 2007-04-03
is
> /home/user_name/.config/autostart/
where user_name is your user name

---

### Post by celticbhoy on 2007-04-03
just had a look but when I look in 'username' folder no .config is this hidden and can I just cd to it, or do I need to do something else

---

### Post by spankymasterc on 2007-04-03
do what i say it display whats in your /home/user_name/.config/autostart just System > Preferences > Session > Startup Programs and edit or remove anything in there :D

---

### Post by celticbhoy on 2007-04-03
Cheers for help prob solved

---

