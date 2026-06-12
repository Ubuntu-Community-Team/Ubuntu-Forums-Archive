---
title: "videocard + glxgears problem (noob alert)"
date: 2005-09-08
forum: General Help
---

### Post by grimdeath on 2005-09-08
ok, well ive been doing good with learning ubuntu and linux over my last week or two of using it, i managed to get a great understanding of how things work, gotten warmed up to the command line and updates and installations and such, even got my soundcard working FINALLY tonight heh...

well i may have gotten too brave as ive been trying to get my videocard drivers up and running, ive ran into a bit of a problem, i was following this guide:
go into command mode:
control + alt + F1
login as root
/etc/init.d/gdm stop
modprobe -r fglrx
apt-get install --reinstall linux-restricted-modules-2.6.10-5-386 xorg-drivers-fglrx (yes im running i386)
startx

BUT when i did the second to last line(apt-get install....) i received a error during long list of messages during the "installation" and then startx wouldnt do anything so i just did a command to reboot

now when i do "fglrxinfo" or "glxgears" i get this message:
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

any idea WHAT i screwed up here heh, i AM in the learning time so its ok to screw up...if worst comes to worst ill just reformat and reinstall right? everything ive done so far before this is easily redo-able

let me know if you need more info, and any help would be appreciated, thanks!

---

### Post by Lux Perpetua on 2005-09-08
What was the error?

---

### Post by alphonce on 2005-09-08
make sure you have mesa installed
```
sudo apt-get install libgl1-mesa libgl1-mesa-dri
```or else type 'locate libGl' to see if you have it at all

---

### Post by grimdeath on 2005-09-08
my results:

grimdeath@grim:~$ sudo apt-get install libgl1-mesa libgl1-mesa-dri
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgl1-mesa
grimdeath@grim:~$ locate libGL
/usr/lib/libGLU.so.1
/usr/lib/libGLU.so.1.3
/usr/X11R6/lib/libGLU.so.1.3
/usr/X11R6/lib/libGLU.so.1
/usr/X11R6/lib/modules/extensions/libGLcore.a
/home/grimdeath/Downloads/usr/X11R6/lib/libGL.so.1.2
grimdeath@grim:~$

hmmm ideas?

---

### Post by grimdeath on 2005-09-08
hmm, not sure what the standards are here, is it too early to bump?

---

### Post by grimdeath on 2005-09-09
bump, not sure if i can get to the error message, its been a couple days since i did this...is there a way to set my video settings back to a "default" or something as i just need the basic setup ubuntu runs after you install or w/e

*update* i managed to get drivers installed and the ati control panel using this method:
[http://www.ubuntuforums.org/showthread.php?t=32495&highlight=default+video](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=default+video)

glxgears now works but im not getting any change from the before:
1729 frames in 5.0 seconds = 345.800 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1582 frames in 5.0 seconds = 316.400 FPS

btw im running this videocard:
sapphire ati radeon 9800 pro

do i need to adjust something to get this to work or what? 3d screensavers and such now work again but they arent running smooth, theres not really options to change in the ati control panel, perhaps i need the fglrx control panel or something? btw i may have that whats the command to use it?

THANKS!

---

