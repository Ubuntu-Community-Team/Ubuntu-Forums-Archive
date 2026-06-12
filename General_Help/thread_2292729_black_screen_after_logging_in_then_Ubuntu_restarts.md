---
title: "black screen after logging in then Ubuntu restarts"
date: 2015-08-30
forum: General Help
---

### Post by ethernetfast on 2015-08-30
Hi Ubuntu community
 I have a problem logging in Ubuntu.
 Problems started after forcing shutting down Ubuntu, from power button,  while it was updating.
 Next restart, it displays the users in have in Ubuntu, but when i choose one of the user names and enter the password, after i hit enter key, it just shows a black screen and then the same logging in option shows up.
 Its just as in a loop without booting in the OS.
 Any help is greatly appreciated.
 Thank you very much!

---

### Post by CantankRus on 2015-08-31
At the geeter login, hit ctr+alt+F1 and login.
Run...
```
sudo apt-get update
sudo apt-get upgrade
```

If you enconter errors run...
```
sudo apt-get install -f
sudo dpkg --configure -a
```

Then repeat the first 2 update and upgrade commands.
Any errors?

ctr+alt+F7 to get back to greeter or
to reboot...
```
sudo reboot
```

---

### Post by ethernetfast on 2015-08-31
Thank you CantankRus.
Problem solved using your help steps.

---

