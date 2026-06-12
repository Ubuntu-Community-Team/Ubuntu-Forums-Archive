---
title: "2 questions Kate and Brightness (not mine the screen)"
date: 2007-03-05
forum: General Help
---

### Post by pilot550 on 2007-03-05
Question 1
I miss gedit. Every time I try and edit a text file with kate I get an error message like this one:

$ sudo kate /etc/default/acpi-support
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
No protocol specified
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
No protocol specified
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5734' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
No protocol specified
No protocol specified
No protocol specified
kio_uiserver: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with kio_uiserver, it probably crashed. 


But then it opens kate anyway and I can edit the file. What gives? Am I using the wrong command?

Question 2
I have a Sony VAIO FS550 and I can't adjust the screen brightness in Feisty Fawn. I was able to get the brightness Fn keys to work in Edgy but not in Feisty. Even when I enable laptop mode and unplug it, with battery mode set to 50% brightness, nothing happens. Other than that I love Feisty Fawn. My touch pad scrolling even works. Thanks

---

### Post by dyous87 on 2007-03-05
> **pilot550 said:**
> Question 1
I miss gedit. Every time I try and edit a text file with kate I get an error message like this one:

$ sudo kate /etc/default/acpi-support
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
No protocol specified
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
No protocol specified
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5734' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
No protocol specified
No protocol specified
No protocol specified
kio_uiserver: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with kio_uiserver, it probably crashed. 


But then it opens kate anyway and I can edit the file. What gives? Am I using the wrong command?

Question 2
I have a Sony VAIO FS550 and I can't adjust the screen brightness in Feisty Fawn. I was able to get the brightness Fn keys to work in Edgy but not in Feisty. Even when I enable laptop mode and unplug it, with battery mode set to 50% brightness, nothing happens. Other than that I love Feisty Fawn. My touch pad scrolling even works. Thanks

Why don't you install gedit and see if it works. Also have you checked the shortcut settings to see if its sent correctly?

---

### Post by Arisna on 2007-03-05
As far as question one is concerned, you should use gksu (in Gnome) or kdesu (in KDE), to launch graphical programs, not sudo, which can cause some serious configuration problems for your user account if used to run graphical applications.  Why do you miss gedit?  Did you switch to KDE?

I'm afraid I don't know very much about this second issue.  I don't own a laptop. :(

---

### Post by pilot550 on 2007-03-05
I tried to install gedit and it's not working. This is my first time using Kubuntu, so I'm not use to the differences between KDE and Gnome. Even with kdesu kate I am getting the error messages. I don't know how to check my shortcuts. Thanks.

---

### Post by dyous87 on 2007-03-05
hmm odd...is there any reason you want to use kubuntu over ubuntu?

---

### Post by pilot550 on 2007-03-05
I like the GUI a lot more and I wasn't able to get my touch pad to scroll in Ubuntu Edgy. I tried everything and it was driving me crazy.

---

### Post by taurus on 2007-03-05
If you really need to edit it, try a basic text editor like nano for now.

```
sudo nano -Bw /etc/default/acpi-support
```
Save and exit with <Ctrl>o and <Ctrl>x.

---

### Post by dyous87 on 2007-03-05
try doing a sudo dpkg-reconfigure xserver-xorg and follow all through selecting the right choices. make sure it detects your mouse and keyboard correctly. choose emulate 3 button mouse when you can.

---

### Post by FuturePilot on 2007-03-05
When I tried out Kubuntu I was getting the same thing. 
Although when I did something like
```
sudo kate /etc/X11/xorg.conf
```
I would get  a whole bunch of errors and then kate would fail to open.

---

### Post by pilot550 on 2007-03-05
Well that works. Thanks! What does the -Bw do?

---

### Post by taurus on 2007-03-05
The B stands for backup (making a backup copy in case you screw it up, you can still fall back to the original version) and the w means not to wrap lines longer than 24 characters around.

---

### Post by pilot550 on 2007-03-05
> **dyous87 said:**
> try doing a sudo dpkg-reconfigure xserver-xorg and follow all through selecting the right choices. make sure it detects your mouse and keyboard correctly. choose emulate 3 button mouse when you can.

I went through all the options and configured the mouse to emulate 3 buttons and I still get the same error using kate.

---

### Post by pilot550 on 2007-03-05
> **taurus said:**
> The B stands for backup (making a backup copy in case you screw it up, you can still fall back to the original version) and the w means not to wrap lines longer than 24 characters around.

Good information. Thank you very much.

---

