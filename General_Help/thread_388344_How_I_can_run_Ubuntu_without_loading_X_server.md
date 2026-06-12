---
title: "How I can run Ubuntu without loading X server?"
date: 2007-03-19
forum: General Help
---

### Post by Davigetto on 2007-03-19
Hi, I am in a laptop, and I need saving as much battery as I can every day. In the terminal my laptop don't spend so much battery, so, how can I run ubuntu in terminal mode, without loading gdm and xorg, and without "destroying" xorg.conf?

Greetings

---

### Post by dfreer on 2007-03-19
First, to stop GDM from loading on boot (I used [*_this thread_*]("http://ubuntuforums.org/showthread.php?p=2250022") as reference): 
  From X: System > Administration > Services. Uncheck box next to *Graphical Login Manager (gdm)*
  From Terminal: ```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```
  
  When you reboot you should only see your command prompt. To get back into the GUI, type the command. ```
startx
```

---

### Post by Davigetto on 2007-03-19
thank you very much, that was what i want ^^

---

### Post by WalmartSniperLX on 2007-03-19
thanks for that too :D I needed it as well

---

