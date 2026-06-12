---
title: "automatic decryption of /home/ fails"
date: 2013-02-28
forum: General Help
---

### Post by fruchtoase on 2013-02-28
Hi everyone,

my first post here and as you may have guessed already I need your help. :)
My problem is, I don't have access to my home directory any longer. The automatic decryption at login seems to fail.

Some basic info first:
lubuntu 12.04 always kept up to date
```

-Computer-
Processor        : Intel(R) Pentium(R) 4 CPU 2.40GHz
Memory        : 2579MB (737MB used)
Operating System        : Ubuntu 12.04.2 LTS
User Name        : martin
Date/Time        : Do 28 Feb 2013 21:12:42 CET
-Display-
Resolution        : 1680x1050 pixels
OpenGL Renderer        : GeForce 7600 GT/AGP/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ICH4 - Intel ICH5
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 MLK Wireless Desktop
 MLK Wireless Desktop
-Printers (CUPS)-
EPSON-Epson-Stylus-Office-BX525WD        : <i>Default</i>
-SCSI Disks-
PLEXTOR DVDR   PX-L890SA
ATA ST3120026A
ATA SAMSUNG SP1614N
ATA SAMSUNG SP1614N
```

My system was stable and running smoothly until one day it didn't let me login anymore (if I recall correctly I had an update the day before). It just kept on returning me to the login screen. I was able to login as guest and as myself via console. I was not able though to start x. With help from the German Ubuntu forums I was able to manage to login to my account via the usual login screen again ([http://wiki.ubuntuusers.de/Homeverzeichnis#Rechte-korrigieren](http://wiki.ubuntuusers.de/Homeverzeichnis#Rechte-korrigieren)). The problem now being that I don't have access to my home directory. Somehow the automatic decryption seems to be messed up. I tried ecryptfs-mount-private manually then with the following result.

```
Inserted auth tok with sig [e4070676864e80f0] into the user session keyring
mount: Operation not permitted
```

Now I'm pretty much clueless and relying on your help.
Help would be appreciated.

Greetings

---

### Post by fruchtoase on 2013-03-01
If any further information is neccessary to help solve the problem, please feel free to ask.
I don't know what to add to make this easier to solve.
Thanks.

---

### Post by fruchtoase on 2013-03-03
Quick Update
With ecryptfs-recover-private I can access my files. So they have not been damaged or anything. I just seems to be some sort of authorisation problem.

---

