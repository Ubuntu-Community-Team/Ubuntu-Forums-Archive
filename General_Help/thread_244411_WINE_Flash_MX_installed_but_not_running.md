---
title: "WINE: Flash MX installed but not running"
date: 2006-08-26
forum: General Help
---

### Post by rdlfo on 2006-08-26
Hi, i wonder if someone can help me. I've installed WINE using the synaptic package manager (0.9.9-0ubuntu2). Next, i installed Flash MX from the cd-rom:

wine cdrom/path/to/flash/mx/setup.exe

And it was very neat, the wizard came up, i entered the serial and everything was installed, just like in win.

Then, Wine File started and i saw all this windows-like structure. I tried to run the Flash MX double clicking the Flash.exe, the splash screen came and inmediatly shut up. The process didn't continue...

Then i went to the terminal and found the exe and WINE it directly:

~/.wine/drive_c/Program Files/Macromedia/Flash MX$ wine Flash.exe

Same thing, splash screen a half of a second and gone, but i got this output:

fixme:ole:CoRegisterMessageFilter stub
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  175
  Current serial number in output stream:  175

Since i'm such a noob, i have no idea what do i need to fix, suppose is a matter of X, but no clue at all. Any help will be appreciated really,

thanks in advance,
rdlfo.

---

### Post by thesmartace on 2006-09-02
A friend of mine had the same problem. After a quick trip to the Wine App Database ([http://appdb.winehq.org/appview.php?iVersionId=1027]("http://appdb.winehq.org/appview.php?iVersionId=1027")) I found a solution. You have to edit your **xorg.conf**:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```
And then comment out the sections containing Wacom. Make sure you comment out the bit at the start of the file that refers to those sections as well or you will have issues when you restart X (reboot or whatever).

If you do have problems when you restart X you will prolly end up with just the terminal so just revert back to your old xorg.conf and startx:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
startx
```
(if you do revert, Flash wont work but at least you will have gnome back).

Save the file and restart X.


That worked for them, so I hope it works for you :D .

---

### Post by rdlfo on 2006-09-04
Thanks, i'll give it a try. That´s the second time i got that recommendation, unfortunately oi haven´t got the time to try it, but i´m on it.

best regards,
rdlfo.

---

