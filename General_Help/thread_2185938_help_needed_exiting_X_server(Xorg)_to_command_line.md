---
title: "help needed exiting X server(Xorg) to command line."
date: 2013-11-05
forum: General Help
---

### Post by joseph2 on 2013-11-05
i'm trying to install a video driver for a video card and i need to exit the X server (Xorg) to do so. but i don't know how to do it. i am running Lubuntu 13.04 (raring).

---

### Post by sudodus on 2013-11-05
Start a text screen with the hotkey combination ***ctrl + alt + F1***

Stop the graphical environment with

```
sudo service lightdm stop
```

install the driver and either run

```
sudo service lightdm start
```

or ***reboot*** the computer.

[COLOR=#696969]The graphical environment is at ***ctrl + alt + F7***, and you can have six text screens at ***ctrl + alt + F1 ... F6***[/COLOR]

---

### Post by joseph2 on 2013-11-06
thanks for the help sudosus. it work perfectly. :)

---

### Post by sudodus on 2013-11-06
I'm glad you succeeded :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help others find the solution.

---

