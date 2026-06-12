---
title: "Desktop effect could not be enable"
date: 2008-06-29
forum: General Help
---

### Post by Ghostalphas on 2008-06-29
hello .. im having some trouble with my Ubuntu .. 

this is my compiz .. 


ghostalphas@ghostalphas-laptop:~$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

and when i go to system , preference , apparence and go to visual effect
and set it to normal it tell me  desktop effect could not be enable so i 
dont have any effect
please help me ..

---

### Post by forger on 2008-06-29
We need more info, the more you provide, the better we can help you
1) Ubuntu release? Hardy Heron 8.04?
2) Ubuntu 32-bit or 64-bit?
3) Have you installed hardware drivers using System > Administration > Hardware drivers or are you using other drivers (unofficial, say nvidia)?
4) Have you used any non-official drivers in the past? using envy or from their website?
5) What's your graphics card? (full name - vendor, brand and model) Open Applications > Accessories > Terminal, post back the output of: ```
lspci | grep -i vga
```
6) Have you tried enabling compiz through System > Preferences > Appearance > Desktop effects > Normal ?
What does it say?

---

### Post by Ghostalphas on 2008-06-29
> **forger said:**
> We need more info, the more you provide, the better we can help you
1) Ubuntu release? Hardy Heron 8.04?
2) Ubuntu 32-bit or 64-bit?
3) Have you installed hardware drivers using System > Administration > Hardware drivers or are you using other drivers (unofficial, say nvidia)?
4) Have you used any non-official drivers in the past? using envy or from their website?
5) What's your graphics card? (full name - vendor, brand and model) Open Applications > Accessories > Terminal, post back the output of: ```
lspci | grep -i vga
```
6) Have you tried enabling compiz through System > Preferences > Appearance > Desktop effects > Normal ?
What does it say?

Hardy Heron 8.04 ( ultinate 1.8 )
Ubuntu 32-bit
The NVIDIA .. 
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)

Desktop effect could not be enable 

and also every time i run the Ubunt  it say 
unbunt is running in a low grafic mode .. 
your screen and grafic card could not be detected ..  
i have to restart and .. run it in the recover mode and search for the error and repair it .. every time i try to update somthing in my unbunt

NO EFFECT WORK  !! :( ubuntu suck without there effect .. please
help me to fix it !! thank you


and when i open my NVIDIA X SERVER in   Applications , Nvidia x server setting it tell me 

"" You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  "" 

and when i do it .. when i restart it .. i **** up the screen .. and i need to go to recorevery system and repair it .. 
and .. it does nothing i start back from 0

---

### Post by Ghostalphas on 2008-06-29
help??

---

### Post by forger on 2008-06-30
go to terminal and do:
```
sudo apt-get purge nvidia-glx-new nvidia-glx nvidia-glx-legacy
sudo apt-get install envyng-gtk
```

Now go to Applications > System Tools > EnvyNG

Select the NVIDIA driver, follow the instructions (click Apply)
If automatic hardware detection does not work, use "Install the nvidia driver manually" and choose "173.xx.xx" (173.14.05)

---

