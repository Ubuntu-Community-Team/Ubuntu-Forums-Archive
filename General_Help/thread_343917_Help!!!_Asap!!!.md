---
title: "Help!!! Asap!!!"
date: 2007-01-22
forum: General Help
---

### Post by Th1eF` on 2007-01-22
i have logout from Ubuntu and when i try to login back it doesnt load anything...!
i cannot login even as root. it dosnt load anything :(

what to do to fix that?](*,) ](*,)

---

### Post by Th1eF` on 2007-01-22
i forget to mention that i have try to install Automatix but then when i was trying to open terminal,Home,System does not open
i have log out and try to login
but it doesnt load anything

---

### Post by Terryj1974 on 2007-01-22
Have you tried to boot Ubuntu with the live CD? This should at least allow you to sign in, and diagnose whatever it is that might be causing the issue

---

### Post by Th1eF` on 2007-01-22
i have install the fluxbox and i have loged in....but i cannot open the gnome anymore...any solutions??

---

### Post by Paul41 on 2007-01-22
You could try to reconfigure your xserver setting.
```
sudo dpkg-reconfigure xserver-xorg
```

It will take you through some prompts to reconfigure. You can just select the default if you aren't sure. When you get to the graphics driver chose the nv driver (assuming you have a nvidia graphics card) and see if that fixes it.

---

### Post by Th1eF` on 2007-01-22
i have done this but nothing

---

### Post by Th1eF` on 2007-01-22
.

---

### Post by Th1eF` on 2007-01-22
is there any way to reinstall GNOME or try to fix what happend?

---

### Post by Tomosaur on 2007-01-22
Try this command:
```

sudo dpkg-reconfigure ubuntu-desktop

```

---

### Post by jelkimantis on 2007-01-22
You can always click "reinstall" on the synaptic package manager, or if synaptic has been eaten (that is you can't access it anymore).  You can simply do an:

sudo apt-get --reinstall gnome


Also, you're liable to get more responses if you don't keep posting blank responses to keep your post on top.

Jelki

---

### Post by Th1eF` on 2007-01-22
i have try: 
sudo dpkg-reconfigure ubuntu-desktop

and i get:
/usr/sbin/dpkg-reconfigure: ubuntu-desktop is not installed

and when:
root@kleftisx-desktop:~# sudo apt-get --reinstall gnome

i get:
E: Invalid operation gnome

i have try using Synaptic Manager to install again GNOME but i also get an error 

gnome:
 Depends: gnome-desktop-environment but it is not going to be installed
 Depends: gnome-office but it is not going to be installed
 Depends: rhythmbox but it is not going to be installed

---

### Post by Th1eF` on 2007-01-23
any idea someone?

---

### Post by bigken on 2007-01-23
at the promt 

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install ubuntu-desktop :)

---

