---
title: "Help me install this...(slowly going insane)"
date: 2008-05-25
forum: General Help
---

### Post by asintu on 2008-05-25
I've been trying to install this nvidia driver package for 2 hours now.
Right now I'm at this stage:

- I boot in "safe mode" (or whatever its called) and try to run it but it recommends to switch to runlevel 3. So I type "telinit 3" and then I'm restarted into the regular mode (not the safe mode) where if I try to run it it says I'm running X server and it won't install it. What is going on??!!

---

### Post by Zoja on 2008-05-25
had this problem ... when the loging screen apears , select options -> log in terminal mode , or something like that .. then you'll have the X server shut down. good luck :)

---

### Post by jken146 on 2008-05-25
You can shut the X server down.  Press Ctrl+Alt+F1, log in and type ```
sudo /etc/init.d/gdm stop
``` then do whatever you need, then ```
sudo /etc/init.d/gdm start
```
You may need to press Ctrl+Alt+F7 now to see the GUI.

---

### Post by asintu on 2008-05-25
> **jken146 said:**
> You can shut the X server down.  Press Ctrl+Alt+F1, log in and type ```
sudo /etc/init.d/gdm stop
``` then do whatever you need, then ```
sudo /etc/init.d/gdm start
```
You may need to press Ctrl+Alt+F7 now to see the GUI.

perfect..i've finally installed it. Now the problem is that I don't see any fan speed settings...uhhhhhh

---

### Post by asintu on 2008-05-25
i've also installed nvclock but when i try to change fanspeed it says:
"adjustment of the fanspeed isn't supported on your type of video card".
What to do now?

---

