---
title: "Login loops back to login screen (12.10)"
date: 2012-11-23
forum: General Help
---

### Post by rotaryphone111 on 2012-11-23
hello there, I have a problem.

when I login, it loops back to my login screen. however, when I enter the wrong password, it tells me it's wrong.

I am aware that other people have had this problem elsewhere:[http://askubuntu.com/questions/197114/login-not-working-after-upgrade-to-12-10](http://askubuntu.com/questions/197114/login-not-working-after-upgrade-to-12-10), but they posted in the wrong place.

HELP!

---

### Post by Shiro Ishii on 2012-12-12
I am having the same problem.  Is it being discussed/addressed elsewhere?

---

### Post by zombifier25 on 2012-12-13
Press Ctrl + Alt + F1 to get inside a tty, log in, and type this command:
```
sudo chown username:username .Xauthority
```
replace username with your user name.

---

### Post by apochry on 2012-12-13
Have you been using the 'sudo' command with graphical applications lately? This is incorrect and usually the reason why this happens...
One should only use 'gksudo' with such apps.

Here is more info on that: [LINK]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo")
> **Graphical sudo**

 You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo). 
Examples:```

gksudo gedit /etc/fstab
```or 
```
kdesudo kate /etc/X11/xorg.conf
```
[LIST]
[*]To run the graphical configuration utilities, simply launch the application via the Administration menu.
[*]gksudo and kdesudo simply link to the commands gksu and kdesu
[/LIST]


---

