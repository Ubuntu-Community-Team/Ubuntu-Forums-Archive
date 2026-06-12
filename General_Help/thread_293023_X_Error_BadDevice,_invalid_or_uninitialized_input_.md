---
title: "X Error: BadDevice, invalid or uninitialized input device 169"
date: 2006-11-04
forum: General Help
---

### Post by janhenderson on 2006-11-04
I get this error when I install software. It still installs the software, but I get this error nonetheless. 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.


Any ideas?

---

### Post by jimisdead on 2006-11-05
I get the same message whenever I run a X application from the command line. precisely: 

```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by Iarwain ben-adar on 2006-11-05
Hi guys,
the problem is probabely the "wacom" devices in your /etc/X11/xorg.conf

to edit it, do this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```

Than just comment out (place # in front of those lines)
the lines that mention anything "wacom" related. Don't forget the Endsection etc..

Btw, to save and exit in nano, press CTRL+X

To see if it has worked, restart your X (log out, and restart X)


PS: first see if it IS the wacom stuff that is giving those errors:```
sudo cat /etc/X11/xorg.conf
```

And see if the "wacom" stuff isn't already commented out ;)


Iarwain

---

### Post by ehuru on 2006-11-13
Hi larwain

I tried to do what you suggested and commented out all devices with wacom-drivers (3 to be exact). After this I couldn't start X, it complained the xorg.conf was incorrect/incomplete and I had to remove the comments to be able to restart X. I did comment out the start and finish-lines.

Any idea?

---

### Post by Iarwain ben-adar on 2006-11-14
Hi,
could you show me the xorg.conf that you tried? (the one that failed)


Iarwain

---

### Post by ScoobyDan on 2006-11-15
Iarwain,

I get the same problem, and it is causing Beryl to not work :(

Attached is my xorg.conf file. Can you take a look?

Many thanks,

Daniel

---

### Post by ScoobyDan on 2006-11-15
:D Problem solved! :D

See: [http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen](http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen)

I hadn't commented out these lines:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection
```

ehuru - maybe this will help you?

Daniel

PS Hasn't solved my Beryl problem, but that is for another thread! ;)

---

### Post by kwilliam on 2007-06-22
Wow!  Thank you so much.  I was getting so sick of 
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```
getting spewed into the terminal output all the time.  Commenting out those three lines did the trick!  (And chances are I'll never need them because I do not have a Wacom tablet, nor do I plan on using one with Linux.)
It's nice to have clean, plain output.  :D

---

### Post by casperfelix on 2007-09-05
Thank you. Another fix and my Kubuntu 7.04, Feisty Fawn now runs even sweeter.
Seems to me that setting up xorg.conf and installing graphic card drivers is the only thing that now holds Ubuntu/Kubuntu back from being an operating system for the computer illiterate masses.:lolflag:

---

### Post by allCuExpMa on 2008-02-17
cheers larwain ben-adar, that annoying message disappeared after i commented the "wacom" out....

any idea for what does "wacom" stands for??

thanks alot


T[m]

---

### Post by kwilliam on 2008-02-22
Wacom is a brand of tablet input devices.  (Largish touchpads that use styluses.)  Useful for artists, designers, etc.

---

