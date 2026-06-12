---
title: "Ubuntu loads to blank screen and doesn't respond to anything"
date: 2007-11-08
forum: General Help
---

### Post by alicson on 2007-11-08
I've only just set up Ubunutu.. was trying to take care of important basic stuff, like getting wireless internet to work, and display resolutions..  Was unsuccessful on both fronts, but was till plugging away at them..  Tried installing nvidia drivers again, and it looked successful this time, but upon reboot, the loading screen comes up with the status bar, but then the screen blanks out.  I think that before, both (dual monitors, although Ubuntu so far refused to extend screen from one to the other) monitors were displaying black. 

Now the secondary displays black (nothing nothing) while the main screen shows the plain, solid-colored tan background of Ubuntu.  And nothing else.  No cursor.  No response to any key combinations, including ctrl+alt+F1, ctrl+alt+del...  I've rebooted several times..  It does boot up with the installation CD and that works alright (although it feels slower than it did when I first installed...is that my imagination?), and I can see and navigate there, but I'm not sure what to do in it to repair my installed version..  I've also restarted and booted into Safe Mode Ubuntu.. but don't know what to do at the command line to troubleshoot/repair.

I've looked aorund for existing answers, and am feeling pretty overwhelmed and confused.. But if it is a graphics driver issue, for example, how can I install that now?  I have a spare laptop running Windows so I have good access to internet and can download and transfer files between the two machines pretty easily, but I can barely navigate ubuntu with the graphical interface as it is (still very new to me, and a headache on 800x600 res.which is why I was desperate to install the drivers fo rmy 1600x1200 and second monitor).

It can't possibly be this complicated and trouble-filled to activate wireless and graphics drivers in Ubuntu...is it?

Without the graphical interface (or any interface, for that matter), what can I do?  I guess I have the graphical interface from CD? Is booting from CD the same environment as the installed-to-drive version?  Yes, I am very new....

---

### Post by alicson on 2007-11-08
from terminal, from CD, as ubuntu@ubuntu, 
tried 
```
sudo nvidia-glx-config enable
```

command not found
tried 
```
nvidia-glx-config enable
```
the program can be found in the following packages.... try sudo apt-get install <select package>

with or without "sudo", ```
apt-get install nvidia-glx-config
``` returns:
could not lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

:-/   I'm not even sure I'm on the right track to fixing the blank screen issue....

---

### Post by eZoulou on 2007-11-08
> command line to troubleshoot/repair
try logging in safe mode. 
Then 
```
cd /etc/X11
```
list all files of the folder with 
```
ls -l
```
You must see an xorg.conf and also a backuped file (hopefully) looking like xorg.conf.backup or something like that...
If so, restore the backup that seems the most appropriate (let's say it is called xorg.conf.backup)
```
sudo cp xorg.conf.backup xorg.conf
```
Then see if it works 
```
startx
```
if so, you should acces the ubuntu desktop as a root user. 
If you want to reboot, type Ctr+Alt+Backspace to kill the X server (you should get back to command line) and then type 
```
reboot -n
```

That should just get you back to where you were before the problems occured. 
Good luck/.

---

### Post by nadarockyraccoon on 2007-11-08
had the same problem, fixed it with this.

open the synaptics package manger from your menus (System>Administration>Synaptic Package Manager). Search usplash. Right click usplash and usplash-theme-ubuntu and opt to completly remove both of them. 
Now reboot your computer. Open the package manager and search usplash again. Now install mythbuntu-artwork-usplash and reboot your computer. 
Now completely remove mythbuntu-artwork-uspalsh and usplash, and you probably guessed it, reboot. 
This is the last time I hope. Search usplash, install usplash-them-ubuntu. Now when you boot it will show the usplash screen and boot much faster and all should be well.

I know this is a odd way to go, but it has worked consistently for me. Hope it helps

---

