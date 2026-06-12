---
title: "Cannot select a higher resolution ;_;"
date: 2007-08-17
forum: General Help
---

### Post by Mr. Snuggle Bunny on 2007-08-17
Hello again, I know there are other topics but the whole sudo dpkg-reconfigure xserver-xorg thing scares me. So can anyone explain that to me? OR is there another way to change my resolution? I want to change it to 1280 by 1024. Thanks again in advance.

---

### Post by ddrichardson on 2007-08-17
If you backup /etc/X11/xorg.conf then you can reconfigure but be able to undo it if it all goes wrong.

---

### Post by Amazona aestiva on 2007-08-17
If you use Nvidia card type:
```
sudo nvidia-settings
```
then analyze the window that appears.

---

### Post by Mr. Snuggle Bunny on 2007-08-17
Well the thing is, I dont know what you guys are talking about with all that stuff =/ I'm fairly new to Ubuntu nad Linunx in general

---

### Post by ddrichardson on 2007-08-17
1. Open a terminal.
2. Type ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you need to go back to your previous settings:

1. Press CTRL-ALT-F2
2. Login
3. Type ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
4. Logout by pressing CTRL-D
5. Press CTRL-ALT-F7
6. Press CTRL-ALT-Backspace

---

### Post by maybeway36 on 2007-08-17
I don't think there will be any other way to do it except sudo dpkg-reconfigure xserver-xorg until Gutsy.
I suggest run that command, then just keep pressing enter until you get to the screen resolutions.

---

### Post by Johnny.P on 2007-08-17
Applications/Accessories/Terminal  then type in      sudo dpkg-reconfigure xserver-xorg

Work through using arrow keys and space to enter- should help.

---

