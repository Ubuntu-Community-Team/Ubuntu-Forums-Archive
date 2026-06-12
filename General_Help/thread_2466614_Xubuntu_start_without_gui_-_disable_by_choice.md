---
title: "Xubuntu start without gui - disable by choice"
date: 2021-09-01
forum: General Help
---

### Post by edgarguedes on 2021-09-01
Hi there. Will need your help. Ive installed xubuntu 20.04 and sometimes i need the gui interface. But ide like most of the time that it boots to no gui interface only text login.  All the guides i found are Ubuntu not xubuntu.
Can anyone help me?
Thks in advance

---

### Post by yetimon_64 on 2021-09-01
I am currently running Xubuntu. Xubuntu and Ubuntu use basically the same commands to do what you want. You set the default login type as either multi-user target (for text/console log in) or the graphical target (for a GUI log in) using the systemctl command as root (using sudo).
 
To change to a console/text boot ...
```
sudo systemctl set-default -f multi-user.target
```
This command above will, on the next boot, land you on a console login only, no gui at all present.

Once logged in on the console, if you wish a gui started...
```
sudo systemctl start lightdm
```
Lightdm can be stopped by using "log out" from within the xubuntu GUI.
To shutdown the greeter screen and return to a pure console environment...
```
sudo systemctl stop lightdm
```

To return your system to a graphical boot ...
```
sudo systemctl set-default -f graphical.target
```
Then do a reboot to get back to a lightdm greeter screen (or whichever greeter screen your set up uses).

I use a couple of root running custom scripts with these basic commands to set my system to always open on a text console (and back to graphical if the second script is used). Basically those two "sudo systemctl set-default" commands should do what you want.

Regards, yeti.

---

### Post by edgarguedes on 2021-09-01
Thks you. Best regards

---

### Post by yetimon_64 on 2021-09-01
_*If*_ this works for you please don't forget to mark your thread as solved. The middle link in my sig line has a link to a guide on marking your thread as solved if it is needed.

Cheer, Yeti

---

