---
title: "[SOLVED] Log Out Automatically After A Set Time."
date: 2008-02-19
forum: General Help
---

### Post by nothingspecial on 2008-02-19
My kids love playing games on the pc. We limit the time but this causes major arguments, also you can`t police things all the time. 
  What I`d like to do is create an account for them that only my wife and I know the password for and set it to log out after say 30 minutes whatever they`re doing, even if they`re furiously clicking the mouse blasting spaceships to pieces. Anyone any ideas?
  I`m a complete novice by the way.

---

### Post by jan quark on 2008-02-19
Shutdown after x minutes
```
sudo shutdown time
```

replace time with 30 for 30 minutes

it will shutdown not log off :)

---

### Post by aashay on 2008-02-19
Use the sessions app on preferences to add this to startup of that account:
```
sleep 1800 && gnome-session-save --kill --silent
```
1800  = 30mins expressed in seconds in case you dint figure it out already

---

### Post by nothingspecial on 2008-02-19
Great guys but how do I add that to the start up of the account? Remember I`m a complete novice.:)

---

### Post by nothingspecial on 2008-02-19
Sorry reread your post. Can do it now. No more argumnents. Thanks guys.

---

