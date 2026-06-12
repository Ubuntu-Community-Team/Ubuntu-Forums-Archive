---
title: "password problems"
date: 2008-03-21
forum: General Help
---

### Post by libertas on 2008-03-21
ive had ubuntu on my laptop for a long time now and just recently the password changer (in about me) won't work i go to change password, enter the old and the two new and the click change password, it waits... and waits and waits and does not stop waiting... ive never had this problem before, i also don't have a quit button anymore (just hibernate and sleep) i am now forced to shutdown using "sudo poweroff now" i don't know if there is any connection

---

### Post by Rocket2DMn on 2008-03-21
I'm not sure about your shutdown problem, but to change your password, open a terminal and run
```
passwd
```
Or from Recovery Mode
```
passwd *yourusername*
```

---

### Post by libertas on 2008-03-26
i tried that and it gave me a error message that said that i needed a password with at least 6 char. so apparent it won't allow you to have passwords shorter than six characters but when it is it doesn't give an error message (in 'About me') i think this is definitely a bug (the fact that it doesn't tell you that something is wrong)

So what i did was type into the terminal >  Sudo passwd and the process worked just fine thanks for the help

---

