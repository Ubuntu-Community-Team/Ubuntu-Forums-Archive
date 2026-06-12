---
title: "Gnome with Compiz-Fusion,KDE Without Compiz-Fusion"
date: 2007-12-27
forum: General Help
---

### Post by me4oslav on 2007-12-27
Here is my problem,i was using compiz-fusion on both KDE and Gnome for a while,but KDE was having the following errors.When i press Ctrl+Alt+Del i am able only of loging out,not turning of my pc.I was having only one desktop and so my superkarambas were only on it.It was strange that when i tried to rotate the Cube with Ctrl+Alt+Left Click i have 4 desktops.I suppose it was because of the xserver-xgl,which was needed for the compiz-fusion to work.When i first installed Compiz-Fusion KDE was painfully slow,but i was able to fix it with the following commands:
```
**echo "compiz --replace gconf &" "gnome-window-decorator &" > ~/.kde/Autostart/startcompiz.sh**
```
```
**chmod +x ~/.kde/Autostart/startcompiz.sh**
```
If there is a way of using Compiz-Fusion only on Gnome,not on KDE,or have 4 Desktops and to be able to turn off my PC from Ctrl+Alt+Del menu i will be very grateful if you tell me how to do that.I suppose i should make the following thing:
```
**echo "_*COMMAND TO STOP COMPIZ*_ &" > ~/.kde/Autostart/stopcompiz.sh**
```
```
**chmod +x ~/.kde/Autostart/stopcompiz.sh**
```

---

### Post by danwood76 on 2007-12-27
How are you running compiz?

You mention XGL in your post do you have xgl running? If you use an ati card the latest drivers support AIGLX which will make it run smoother and faster.

regards,
Danny

---

### Post by me4oslav on 2007-12-27
well when i tried to execute compiz --replace in a terminal it says that it needs XGL.
```
Checking For XGL:not present
```,that is way i have installed it.
I have Ati Radeon 9550 Series 256 MB with 8.37 Driver(installed from the restricted-manager)

---

### Post by danwood76 on 2007-12-27
You could try using the script envy to install the latest ati drivers.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

There was a huge improvement in the latest ati release as they are using a new code base. This may solve your problem, XGL is quite unstable and not a good solution.

regards,
Danny

---

### Post by me4oslav on 2007-12-27
i can install the newest version just by downloading the run file from the ati official web site and:
```
**cd /path/to/ati/**
```
```
**sh ./ati-bla-bla-bla.run --buildpkg ubuntu/gutsy**
```
I will try it and if that fixes the problems with the four desktops and the shutting down,i will be very happy,but should i use-your script of the .run files?
I have solved the problem thanks to envy.
My Gnome is having a Compiz-Fusion now and my KDE does not have.
Thanks man.
The new ATI Driver provided from Envy eliminated the XGL and everything works perfectly now.

---

