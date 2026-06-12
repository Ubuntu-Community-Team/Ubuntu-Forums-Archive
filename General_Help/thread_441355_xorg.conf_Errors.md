---
title: "xorg.conf Errors"
date: 2007-05-12
forum: General Help
---

### Post by le_vainqueur on 2007-05-12
Whenever I open up the xorg.conf file I receive the following error:

> brandon@the-computer:~$ sudo kate /etc/X11/xorg.conf
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
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-6214' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

I am still able to edit the file as usual, but I'm guessing that things would be better if this error did not exist.

Does anyone have any idea as to what this means, or what I can do to fix it?

---

### Post by taurus on 2007-05-12
Please do not use sudo with kate.  Instead, use kdesu.

```
**kdesu** kate /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by le_vainqueur on 2007-05-12
Thanks for the advice, I'll be sure to be more carefull on that end.  I am still getting the following portion of the error, though:

> brandon@the-computer:~$ kdesu kate /etc/X11/xorg.conf
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


---

### Post by fragos on 2007-05-12
To me, it looks as if kate cn't open the device which seems strange.  I'm a Gnome use so I'd use "gksudo gedit /etc/X11/xorg.conf" which alsways works.  Since you're at the command line anyway try "sudo nano /etc/X11/xorg.conf" which being a command line editor make either work or give you different failure messages.  You could also try that file spec with other commands like "cat" or "ls" to see if they have trouble accessing the file.

---

