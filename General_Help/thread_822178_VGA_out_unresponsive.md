---
title: "VGA out unresponsive"
date: 2008-06-08
forum: General Help
---

### Post by eival on 2008-06-08
ive used teh FN+F4 but its not responding.

does Ubuntu not understand those commands?

or is there something else i need to do, i already installed the restricted 3d driver, so i dont know what could be wrong on nVidia's part


im using the 64bit Hardy Heron

---

### Post by underdog512 on 2008-06-08
> **eival said:**
> ive used teh FN+F4 but its not responding.

does Ubuntu not understand those commands?

or is there something else i need to do, i already installed the restricted 3d driver, so i dont know what could be wrong on nVidia's part


im using the 64bit Hardy Heron


What are you trying to do exactly?

---

### Post by eival on 2008-06-08
im trying to get the split screen view on my Laptop and HDTV, which ive been doing in Windows.

i just restarted my laptop while my tv was on and i saw the Ubuntu log-off screen appear on my TV then when it started up again i seen the loading screen but then it went blank.(which is what would happen in Windows XP too)

so that tells me i have the nessisary drivers and capability but the only problem is i dont know how to activate the VGA signal manually. in Windows i could use the (fn+f4) keys.


so what i need to know is how do i tell Ubuntu to activate teh VGA signal? an if theres different variations how do i switch between them, cause in windows i could have Clone View, or extended desktop where the HDTV would just be blank an i can drag a movie player to it without taking up my desktop on the laptop.

---

### Post by underdog512 on 2008-06-08
If you have an nvidia card you should install the Nvidia settings package.

sudo apt-get install nvidia-settings

Once you have installed this you should see the "X Server Display Configuration" when you open it under system > Administration > Nvidia X Server Settings.  This should give you all the options you need to configure your second screen.

---

### Post by eival on 2008-06-08
> **underdog512 said:**
> If you have an nvidia card you should install the Nvidia settings package.

sudo apt-get install nvidia-settings

Once you have installed this you should see the "X Server Display Configuration" when you open it under system > Administration > Nvidia X Server Settings.  This should give you all the options you need to configure your second screen.


awesome! that works thanks alot

---

