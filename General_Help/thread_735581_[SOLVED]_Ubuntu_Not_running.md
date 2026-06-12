---
title: "[SOLVED] Ubuntu Not running"
date: 2008-03-25
forum: General Help
---

### Post by titico on 2008-03-25
Hello
well i was updating my nvidia card driver, and when I restarted the pc, ubuntu didnt recognize the driver, and my card does not work, so i cant work with ubuntu...
if someone know what i must do...thank you :)

---

### Post by scragar on 2008-03-25
you need some form of command line(the second option in grub is often command line, alternativly you can hit ctrl+alt+F1 to reach a command line), and run:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by titico on 2008-03-25
thanks, i'll try with it 
and post again

---

### Post by titico on 2008-03-25
i tried with that code, and all the detection stuff, but it didnt work =[

---

### Post by titico on 2008-03-26
someone can help me?
I could not find the way to solve this problem 
:S

thanks

---

