---
title: "update-manager through terminal, is it safe?"
date: 2006-07-15
forum: General Help
---

### Post by Poka64 on 2006-07-15
Can I use the update-manager through the terminal without breaking the system or something like that?
Of course I use sudo to be able to use it, but is there any reasons that I can't do it this way ?

The reason I'm doing this is because I'm running blackbox and I don't want update-notifier running at startup.

---

### Post by Rui Pais on 2006-07-15
Of course. 
You can run what ever you want from terminal line!

Some people around seems to believe that if you run gui apps from command line you can get file ~/.ICEauthority  with wrong permitions (that used to happen in the past, at least), so if you want to feel more secure instead of
```
sudo update-manager
```
do
```
gksudo update-manager
```

---

### Post by Poka64 on 2006-07-15
cool,thx for the help!

---

