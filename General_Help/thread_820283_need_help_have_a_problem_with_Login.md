---
title: "need help have a problem with Login"
date: 2008-06-06
forum: General Help
---

### Post by vizzerdixx on 2008-06-06
good day ,

i have  Kubuntu installed  on my  pC  but  now i c´ant login ..

i have  tryed  to  login in text modus  but only i can write my name  but  by  passwd  c´ant write  anything 

by KDE login false 

greetings 

vizzerdixx

---

### Post by talktoari on 2008-06-06
Were you able to ever login in ur Kubuntu desktop? Use the same user id and pwd u might have created while installation.

Hope this helps.

---

### Post by vizzerdixx on 2008-06-06
sure  i use  the  same

yesterday  i  was logged  on it  was ok.

But  today  c´ant log in :S


D ónt  know

---

### Post by Toufik on 2008-06-06
In text mode, the password in never written (not even stars).

Either you know your login and password but make a mistake while writing:
- type your password in place of your login to check your keyboard is correct
- take care of lower and upper case

Either you forget your login and/or password
- start your computer in Recovery-mode from GRUB. Then in the terminal, change your password by typing
```
passwd <your-login>
```
or create a new user:
```
adduser <new-login> admin
```

---

### Post by vizzerdixx on 2008-06-06
Thank  you

---

### Post by vizzerdixx on 2008-06-06
> **Toufik said:**
> In text mode, the password in never written (not even stars).

Either you know your login and password but make a mistake while writing:
- type your password in place of your login to check your keyboard is correct 
- take care of lower and upper case

Either you forget your login and/or password 

- start your computer in Recovery-mode from GRUB. Then in the terminal, change your password by typing
```
passwd <your-login>
``` 
or create a new user:
```
adduser <new-login> admin
```

- type your password in place of your login to check your keyboard is correct   It  works


- Either you forget your login and/or password      No


start your computer in Recovery-mode from GRUB. Then in the terminal, change your password by typing
```
passwd <your-login>
```  Thats  not work


```
adduser <new-login> admin
```[/QUOTE] 

I  try  yet

---

### Post by vizzerdixx on 2008-06-06
now  i`m  Recovery menue 

i see :

resume resume  normal Boot

Root Drop the  Root shell promt 

Fix  Try  to fix  Server 

In  root dónt understand 

fix the  server 


my Keybord not warks in text  modus  only the mouse

---

### Post by talktoari on 2008-06-06
Check whether your keyboard is connected properly or not.

OR

Remove the wire of keyboard and connect it again, if it is a desktop.

The changing of password / creation of new account should work.

---

