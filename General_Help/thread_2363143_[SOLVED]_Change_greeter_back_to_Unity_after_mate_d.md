---
title: "[SOLVED] Change greeter back to Unity after mate desktop install"
date: 2017-06-06
forum: General Help
---

### Post by v4169sgr on 2017-06-06
Hello,

I am using 16.04.02 and just installed ubuntu-mate-desktop as an alternative desktop environment.

I'd like to carry on using the unity greeter, but the mate greeter is being used instead.

How do I switch the greeter back?

Thanks :)

---

### Post by deadflowr on 2017-06-06
Simple method
create a new folder in the lightdm configuration folder
(if it doesn't already exist)
```
sudo mkdir /etc/lightdm/lightdm.conf.d
```
change into it
```
cd /etc/lightdm/lightdm.conf.d
```
make a simply file and place this in the file,
```
[SeatDefaults]
greeter-session=unity-greeter
```
save file with a title like
```
99-my-greeter.conf
```
save it and reload lightdm to see if it worked
```
sudo systemctl restart lightdm
```
(the restart will kill the existing session and send you back to the login screen, so make sure anything you want saved has been saved first)

---

### Post by v4169sgr on 2017-06-06
@ deadflowr,

The simple ones are the best. That worked right away - thank you :)

May your tomorrow be filled with real live flowers ;)

---

