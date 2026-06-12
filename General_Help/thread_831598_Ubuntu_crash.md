---
title: "Ubuntu crash"
date: 2008-06-17
forum: General Help
---

### Post by kienseng on 2008-06-17
i'm a new user here....
few days ago, i've installed Ubuntu 8.04 on my laptop, my laptop model is compaq V5751AU, after installed, i installed the restricted drivers, and it works fine after that.

now the problems come, i keep downloading the driver from the synaptic update manager, after i restart, my Ubuntu crashed, now only can run on low level graphic, wireless not working....

i wanna find a solution for this, is there any way i can format the Ubuntu or re-install or repair it???

---

### Post by PmDematagoda on 2008-06-17
Do you mean that Ubuntu started having problems after installing the restricted drivers?

Edit:- Could you also post the specifications of your PC.

---

### Post by ibuclaw on 2008-06-17
When you next boot up, hold down the "**ESCAPE**" key until the GRUB Boot menu shows.

Select the "**Ubuntu Recovery Mode**" option.

When recovery mode has booted up, select the "**Fix X**" option, wait a few seconds for the autoconfig to run, then continue with normal boot.

And if the autoconfig has guessed rightly, then your display should be back to normal behaviour.

Regards
Iain

---

### Post by kienseng on 2008-06-17
i'll try it, but the GRUB still boot, i only get low level graphic after i go into the window.

---

### Post by kienseng on 2008-06-17
i already tried to press backscape key before GRUB load, no changes, and as u said, choose recovery mode and choose the xfix, but there are 2 recovery mode, i only tried one, but after i've tun the xfix, and let it configure, after that i choose the continue normal boot option, but then it still makes no difference, the display there still 800x600, it seems like the OS cant detect my graphic card, and also the restricted driver there should be display the restricted driver, but there are none, now i cant even online using Ubuntu with wired connection....

---

### Post by housam on 2008-06-17
try this : System > Preferences > Screen Resolution

---

### Post by Tomatz on 2008-06-17
What was the package you installed that caused the problems?

---

### Post by kienseng on 2008-06-17
> **housam said:**
> try this : System > Preferences > Screen Resolution

cannot, there's no other option at there, only 800x600 and 640x320.

---

### Post by kienseng on 2008-06-17
> **Tomatz said:**
> What was the package you installed that caused the problems?

i dont know which package i've installed, yesterday night i just tick the driver stuff and somethings related to openGL i think, then i went to sleep.

what should i do now? delete everything and install back? 

is there anyway to format or re-install the Ubuntu?

---

### Post by housam on 2008-06-17
> **kienseng said:**
> cannot, there's no other option at there, only 800x600 and 640x320.

try the following :



```
sudo nano /etc/usplash.conf 
```
you will got something like that 



> # Usplash configuration file
# These parameters will only apply after running update-initramfs.  




add the required resolution 



> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR] 
yres=[COLOR="red"]800[/COLOR]  


or the settings you want
then reboot and type :



```
sudo dpkg-reconfigure usplash 
```
then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by kienseng on 2008-06-17
sorry, but this seems like doesnt help either, did i need to type any commands after change the yres and xres?

after reboot i typed the command, then i go to the screen resolution tab there it is still the same, even i click on the "test display" button not happen also, do i need to redownload the graphic driver

again, my laptop model is V3751AU

graphic card model is nvidia GeForce 7150m/630m

---

### Post by kienseng on 2008-06-17
can anyone help me with this?? :(

what's the driver version should i download for Ubuntu 8.04?

---

### Post by kienseng on 2008-06-18
can anyone help me??!!!

---

### Post by PmDematagoda on 2008-06-18
To install the Nvidia driver manually, follow these steps:-
1)Switch to a tty by pressing Ctrl+Alt+F1.

2) Uninstall the old driver with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

3) Install Envy with:-
```
sudo apt-get install envyng-core
```

4) Run Envy:-
```
sudo envyng -t
```
and install the Nvidia driver using that.

Then reboot the PC with:-
```
sudo reboot
```

---

### Post by kienseng on 2008-06-18
guys....thx for all your hard work!! i'm really appreciate it! 

my Ubuntu 8.04 have back to normal again :) thx you all for helping me!!

---

