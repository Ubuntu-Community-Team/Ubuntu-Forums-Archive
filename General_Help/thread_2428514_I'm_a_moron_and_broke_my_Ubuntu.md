---
title: "I'm a moron and broke my Ubuntu"
date: 2019-10-04
forum: General Help
---

### Post by michaelmcole on 2019-10-04
Okay, I did something stupid and need help to fix it.

I ~had~ ubuntu Mate installed, decided I didn't like it and wanted to go back to plain Ubuntu (19.10).
Googled and found instructions for removing it.
restarted laptop......
Now I have my desktop background image, and a trashcan, no menus, no titlebars, not even a mouse cursor.

I assume i'll need a live CD to fix it, just not sure how. (cannot even open a terminal with ctrl-alt-T, doesn't work)

Can someone help?

---

### Post by Skaperen on 2019-10-04
the best way is to do a fresh new install if you have a backup of your own data.

---

### Post by cruzer001 on 2019-10-04
Wouldn't it be better to reinstall 19.10 at this point?

Go to console and log in.
Ctrl + Alt + F1
Try installing the ubuntu desktop.
```
sudo apt install ubuntu-gnome-desktop
```
and
```
sudo reboot
```

---

### Post by michaelmcole on 2019-10-04
> **cruzer001 said:**
> Wouldn't it be better to reinstall 19.10 at this point?

Go to console and log in.
Ctrl + Alt + F1
Try installing the ubuntu desktop.
```
sudo apt install ubuntu-gnome-desktop
```
and
```
sudo reboot
```

Tried ctrl-alt-f1, just takes me back to the login screen and back to the blank desktop.

---

### Post by cruzer001 on 2019-10-04
Try the console command at the login screen.

---

### Post by michaelmcole on 2019-10-04
> **michaelmcole said:**
> Tried ctrl-alt-f1, just takes me back to the login screen and back to the blank desktop.

I managed to get a console from grub, tried reinstalling gnome desktop, no joy, I get the same blank desktop.

I guess i'll just reinstall 19.10

Thanks anyway guys!

---

### Post by cruzer001 on 2019-10-04
Let us know how it goes

---

### Post by rbmorse on 2019-10-04
You can get a tty console from <ctrl><alt><F3>.  sudo apt install-ubuntu-desktop may work from there. 

Under the current scheme (19.10 for sure, maybe 19.04):
 <ctrl><alt><F1> GUI login, 
<ctrl><alt><F2> restore current GUI session, 
<ctrl><alt><F3> thru <F6> open a TTY console 
<ctrl><alt><F7> hung GUI and blinking cursor that doesn't do anything...at least with the Nvidia driver.

---

### Post by cruzer001 on 2019-10-04
> **rbmorse said:**
> You can get a tty console from <ctrl><alt><F3>.  sudo apt install-ubuntu-desktop may work from there. 

Under the current scheme (19.10 for sure, maybe 19.04):
 <ctrl><alt><F1> GUI login, 
<ctrl><alt><F2> restore current GUI session, 
<ctrl><alt><F3> thru <F6> open a TTY console 
<ctrl><alt><F7> hung GUI and blinking cursor that doesn't do anything...at least with the Nvidia driver.
Hummm

Things are a changing

---

