---
title: "NVIDIA GLX problems..."
date: 2007-02-14
forum: General Help
---

### Post by twkz on 2007-02-14
i installed nvidia-glx,enabled it,restarted x,and now when it's loading i got error that no module found "nvidia",before this my pc freezed many times,something wrong with video :/ any solution ?

---

### Post by Sqwishy on 2007-02-14
run
sudo nano /etc/X11/xorg.conf
and go down to the part where it says device "and your card" and look at the driver, if it's nvidia change it to nv and something is wrong! Otherwise if its nv then make it nvidia and run "/etc/init.d/gdm restart".
What guide did you follow for you drivers? Have you tryed envy? 
[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by r4ik on 2007-02-14
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

For the homepage.

---

### Post by twkz on 2007-02-14
well,i have dapper,i dont know how i get that drivers,i didnt use any guide,i guess it was installed after apt-get upgrade

---

