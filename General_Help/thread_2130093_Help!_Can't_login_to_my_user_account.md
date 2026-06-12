---
title: "Help! Can't login to my user account"
date: 2013-03-28
forum: General Help
---

### Post by noersetiawan on 2013-03-28
I'm using Guest account right now.

I'm just working on VirtualBox and listening some music with Rhythmbox when suddenly my computer becomes laggy, and seconds later, everything disappear except my cursor and wallpaper. I call terminal using CTRL+ALT+T and type startx, sudo startx, and the last one sudo shutdown -h now. After booting up my computer again I cannot login to my user account, after typing password and hit enter, black screen for 2 second, and login screen again. Please help, I need fast solution.

---

### Post by steeldriver on 2013-03-28
Typing 'sudo startx' has probably caused your Xauthority file to become owned by the root user and therefore unwritable when your regular session tries to start

Try switching to a non graphical 'virtual terminal' using Ctrl-Alt-F1 and logging in at the console prompt. If that works you can do 

```
sudo chown *user*:*user* ~/.Xauthority
```

where *user* is your username; or (if you don't have sudo permission)

```
rm ~/.Xauthority
```

(it will ask you to confirm). Then hit Ctrl-Alt-F7 to get back to the GUI login screen and try again.

BTW 'startx' is meant to be used from a non-graphical environment not when you're already in an X session (however broken)

---

### Post by noersetiawan on 2013-03-28
It really works! Thanks man. I figured there is something wrong with LightDM so I tried GDM and I'm able to login to continue my assignment, but I don't like GDM, and I want LightDM back so bad, and you give me my LightDM back, Thank you. I love this forum.

---

