---
title: "Ubuntu wont shut down or restart"
date: 2018-04-05
forum: General Help
---

### Post by flyinghigh2 on 2018-04-05
Hi Ive been having pproblems with broken dependencies and that seems to have been fixed now

see thrread; [https://ubuntuforums.org/showthread.php?t=2387056](https://ubuntuforums.org/showthread.php?t=2387056)

but now i dont seem able to shut-down or restart  my software, I go to the top right as usual and click shut down but nothing happens

---

### Post by Frogs Hair on 2018-04-05
Try a restart from the terminal and then try the panel icon again.this will require a password.

```
sudo reboot
```

---

### Post by flyinghigh2 on 2018-04-05
thanks Frogs Hair

that seems to have sorted the shutting down problem

can you recommend a IRC program for my OS as X-Chat apparently doesnt work; I want to access Blender user groups for making low poly models

thanks in advanced for any helpdo you know what desktop I have , some programs are for "Gnome"??

rgds

robert

---

### Post by Frogs Hair on 2018-04-05
Post the output of the following.```
lsb_release -a 
``` ```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by flyinghigh2 on 2018-04-05
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


```


```

Unity

```


I have gone with hex chat - I seem to have joined a blender user room too!

---

### Post by Frogs Hair on 2018-04-05
Have you solved  the problem then ?

---

### Post by flyinghigh2 on 2018-04-05
yes the reboot seemed to do the trick. many thanks

---

### Post by mörgæs on 2018-04-05
Good, then please mark the thread solved.

---

### Post by flyinghigh2 on 2018-04-06
ooo how do i do that?

---

### Post by mörgæs on 2018-04-09
Just open the Thread Tools menu in the top right corner.

---

