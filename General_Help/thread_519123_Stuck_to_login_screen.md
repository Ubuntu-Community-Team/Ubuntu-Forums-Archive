---
title: "Stuck to login screen"
date: 2007-08-06
forum: General Help
---

### Post by J.One on 2007-08-06
Problem:
After uninstaling all nvidia stuff from synaptic package manager to get a clean install of the new drivers, i stuck over and over again to login screen, after putting username and password.

It seems to load splash screen with nautilus (the icon that appears on splash) and the other 3, then i have a flash of the screen and BOOP again to login to put username....

When i also press Alt+Ctrl+Backspace, instead of getting me to Grub i got the login screen again.

The only thing i can do is login with Terminal default and type whatever it must.I reconfigure xorg from there but no luck...

Any ideas? I've done at least 5.000.000.000 restarts today....

Thanks in Advance

---

### Post by nitro_n2o on 2007-08-06
```
sudo dpkg-reconfigure xserver-xorg
``` give it shot!!

---

### Post by nitro_n2o on 2007-08-06
> **nitro_n2o said:**
> ```
sudo dpkg-reconfigure xserver-xorg
``` give it shot!!

you must have tried it already... 
then use your terminal to install the new drivers 
first make sure everything is removed 
```
sudo aptitude purge nvidia-glx 
```
then install the new ones 
```
sudo apt-get update
sudo apt-get install nvidia-glx
```

---

### Post by J.One on 2007-08-06
i reconfigure xorg and again the same....Is there a possibility that i erase something that needs to boot?
Everything i erased had the nvidia wordin front..

---

### Post by J.One on 2007-08-06
when i put 

sudo aptitude purge nvidia-glx

i get a command not found

when i type 

sudo apt-get update

i saw many err 404 not found and at the end of dialog "Some idex files failed to download they have been ignored or old ones ised instead

and when i type

 sudo apt-get install nvidia-glx

i get a

Invalid operation nvidia-glx

---

### Post by J.One on 2007-08-06
i was entering wrong the first and last command that i got the command not found and invalid operation....My mistake sorry..
I did it all right and it worked! THNX!!

---

