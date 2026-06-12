---
title: "ctrl + alt + F1, F2, F3, F4, F5, etc"
date: 2008-05-10
forum: General Help
---

### Post by ThomasWii on 2008-05-10
hi, on ubuntu for some reason i cant click ctrl + alt + any of the f key's to change console

Thanks
Thomas

---

### Post by ghost_ryder35 on 2008-05-10
do any errors appear in
[code]
/var/log/messages
[code]
when you hit the key combination?

---

### Post by ThomasWii on 2008-05-10
no nothing new gets added.

---

### Post by p_quarles on 2008-05-10
What's the output of this?:
```
ps aux | grep /sbin/getty
```

---

### Post by ThomasWii on 2008-05-10
Ok, ```
root@thomas-laptop:/home/thomas# ps aux | grep /sbin/getty
root      4590  0.0  0.0   1716   512 tty4     Ss+  02:05   0:00 /sbin/getty 38400 tty4
root      4591  0.0  0.0   1716   508 tty5     Ss+  02:05   0:00 /sbin/getty 38400 tty5
root      4595  0.0  0.0   1716   508 tty2     Ss+  02:05   0:00 /sbin/getty 38400 tty2
root      4596  0.0  0.0   1716   504 tty3     Ss+  02:05   0:00 /sbin/getty 38400 tty3
root      4598  0.0  0.0   1716   512 tty6     Ss+  02:05   0:00 /sbin/getty 38400 tty6
root      5760  0.0  0.0   1716   508 tty1     Ss+  02:05   0:00 /sbin/getty 38400 tty1
root      6328  0.0  0.1   3008   756 pts/0    R+   02:11   0:00 grep /sbin/getty
root@thomas-laptop:/home/thomas# 
```

Thanks
Thomas

---

### Post by ThomasWii on 2008-05-11
bump

---

### Post by ThomasWii on 2008-05-18
bump

---

### Post by roe_polak on 2008-05-18
Have you made any funky tricks with Xmodmap? I once lost the console shortcuts because I messed up the .xmodmap-file. My solution was to use a keymap provided by X and just use my ~/.xmodmap to alter the handful of keys I needed. Of course, it could be that you've never touched Xmodmap and in that case I'm not sure exactly what to do.

---

### Post by ThomasWii on 2008-05-18
hi thanks, i dont know what Xmodmap is but when i put it in to terminal it gave me this. ```
root@thomas-laptop:/home/thomas# xmodmap
xmodmap:  up to 2 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

root@thomas-laptop:/home/thomas# 

```

Thanks
Thomas

---

### Post by ThomasWii on 2008-05-19
for some random reason it has worked, but i have the felling that it will break again!

Thanks
Thomas

---

