---
title: "How to set a computer to autologin on reboot"
date: 2022-05-22
forum: General Help
---

### Post by srope01 on 2022-05-22
I would like to use my laptop (running Lubuntu 20.04) as a server. So I would like to autologin into my account on every reboot. In Ubuntu 20.04 this is really easy to do as one simply toggles a switch in the GNOME desktop. But how does one do this in Lubuntu?


Following instructions on one website, I have changed /etc/sddm.conf as below


```
[Autologin]
Session=Lubuntu
User=myusername



```
but after the reboot, it still requires a login. Can any one help?


Silverrope

---

### Post by #&amp;thj^% on 2022-05-22
> **srope01 said:**
> I would like to use my laptop (running Lubuntu 20.04) as a server. So I would like to autologin into my account on every reboot. In Ubuntu 20.04 this is really easy to do as one simply toggles a switch in the GNOME desktop. But how does one do this in Lubuntu?


Following instructions on one website, I have changed /etc/sddm.conf as below


```
[Autologin]
Session=Lubuntu
User=myusername



```
but after the reboot, it still requires a login. Can any one help?


Silverrope

Is your user name really "myusername"?
if not set correctly to your user name.
if your unsure use:
```
whoami
```

---

### Post by srope01 on 2022-05-22
> **1fallen said:**
> Is your user name really "myusername"?
if not set correctly to your user name.
if your unsure use:
```
whoami
```

No, I used my real username, the one I created when I installed Lubuntu. There was an option when I installed to autologin, but unfortunately I didn't click on it. I'd rather not reinstall as I have already customised it. Besides, I assume this must be easy to change.

---

### Post by #&amp;thj^% on 2022-05-22
I need facts here, will you show the return of:
```
cat  /etc/sddm.conf
```

---

### Post by srope01 on 2022-05-22
Sorry, but I found out where the problem was. The sddm.conf had user=myusername, not User=myusername. Capitalizing User solved it. Sorry for the bother. Will mark this solved.

---

### Post by anotherChris on 2023-01-27
You can also add 
```
Relogin=true
```
to the sddm.conf file.

---

