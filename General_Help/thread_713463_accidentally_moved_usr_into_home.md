---
title: "accidentally moved /usr/ into /home/"
date: 2008-03-02
forum: General Help
---

### Post by timjayko on 2008-03-02
I was extracting a .tgz file.. when it extracted it was named usr saved onto my Desktop... I wanted to mv the folder into /home/mydesktopname  so I typed (on accident) mv /usr/ /home/mydesktopname ... now I cannot use sudo.. as the /usr/bin/sudo doesnt exist (not in ~/usr,, its now in /home/mydesktopname/usr/bin/sudo .. what do I do now lol

---

### Post by timjayko on 2008-03-02
what I forgot to mention.. was I ultimately am not able to move it back to the right location.. needing sudo

---

### Post by edm1 on 2008-03-02
i would boot on to a live CD, mount your hard drive and move it back.

---

### Post by timjayko on 2008-03-02
thanks for advice.. booted to recovery mode.. and made new usr directory from command line interface, just mv all the folder directors from /home/desktopname to the new /usr directory

---

### Post by aldenhg on 2008-03-02
For future reference, you can also hit Ctrl+Alt+F1-F6 to get to a terminal real quick in pretty much any situation. Hit Ctrl+Alt+F7 to get back to your Xterm.

---

