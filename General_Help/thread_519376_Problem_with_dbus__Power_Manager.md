---
title: "Problem with dbus / Power Manager"
date: 2007-08-07
forum: General Help
---

### Post by DeadCone on 2007-08-07
I have Ubuntu 6.06, Xorg7.0 and an ATI Radeon 9200.

The problem is the following:
When I try to log in, the computer freezes and then goes back to the log-in screen.
If I log in "Recovery Mode" and do "startx" it appears the following message: 
"[I]Power Manager
This program cannot start until you start the dbus system service.
It is strongly recommended you reboot your compter after starting messagebus.[/I]"
If I activate dbus (/etc/init.d/dbus start) everything goes fine but when I reboot nothing changed.

I read that this problem might be caused by interferences between the Ati Driver and dbus.

My xorg.conf says:
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Now:
1) Does anybody know a way to solve this?
2) Does anybody knows a simple way to upgrade to xorg7.1?

Or links ... or suggestions ...

Thanks for your attention :)
  DeadCone

---

### Post by eggdeng on 2007-08-07
> this problem might be caused by interferences between the Ati Driver and dbus
I recently had similar problems when a kernel update broke my fglrx (proprietary ati) driver.

> My xorg.conf says:
Section "Device"
Identifier "ATI Technologies, Inc. RV280 [Radeon 9200]"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection 

Check if you have two of these sections because according to this, you are not using either the ati ot the fglrx driver! Radeons under 9500 are not supported by fglrx, so you should be using the ati driver which comes bundled with dapper. Try changing
```
Driver "vesa" 
```to 
```
Driver "ati" 
```
You may get lucky.

If you can't log in to gnome, you can do this from a terminal with
```
sudo nano /etc/X11/xorg.conf
```
Edit the file, then press Ctrl+x, Enter Y to save. Type ```
startx 
```to start an X session.

---

### Post by DeadCone on 2007-08-08
Thanks for the reply! :)

If I change "vesa" to "ati" when I start X the screen goes blank and the computer freezes. :(

I have attached the xorg.conf.


Other ideas?

---

### Post by eggdeng on 2007-08-08
Seems clear that you are going to have to reinstall the free ati driver. There is a how-to at [https://help.ubuntu.com/community/RadeonDriver#head-368070d1b267b9a4789bae87c118924bef7d203f]("https://help.ubuntu.com/community/RadeonDriver#head-368070d1b267b9a4789bae87c118924bef7d203f")

---

### Post by DeadCone on 2007-08-08
> **eggdeng said:**
> Seems clear that you are going to have to reinstall the free ati driver. There is a how-to at [https://help.ubuntu.com/community/RadeonDriver#head-368070d1b267b9a4789bae87c118924bef7d203f]("https://help.ubuntu.com/community/RadeonDriver#head-368070d1b267b9a4789bae87c118924bef7d203f")

Problems:
1) The tutorial is for xorg7.1, I have 7.0
2) I follow the instructions but it doesn't work

So, first I should upgrade to Xorg7.1: I'll go to the "Absolute Beginner" and ask there.


Thanks again,
  DeadCone

---

### Post by DeadCone on 2007-08-08
Ok, back again: now I have upgraded to 6.10.

I had a problem with the acpid that I may have solved but what matters is the I followed the tutorial again and nothing changes.

I'm still stuck with the same problem:
1) With "vesa" I cannot log in
2) With "ati" it goes blank and freezes just after log in

Any other ideas?


Thanks,
DeadCone

---

### Post by DeadCone on 2007-08-08
Oh, btw

It gives the following error:

> 
root@desk:~# glxinfo | grep vendor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
root@desk:~# 


---

### Post by eggdeng on 2007-08-08
My idea was that the problems were being caused by a failed install of the fglrx driver, but the how-to you tried should have taken care of that. Do a ```
lsmod
``` to check there are no signs of fglrx. Blacklist the module by adding ```
blacklist fglrx
``` at the end of /etc/modprobe.d and set ```
DISABLED_MODULES="fglrx" 
```in /etc/default/linux-restricted-modules-common. 
If none of that helps, I'm out of ideas. The issue may well have nothing to do with the ati driver. So unless someone comes up with a better solution, you might as well go the whole hog and do a fresh install. 
Sorry not to have been of more help.

---

### Post by DeadCone on 2007-08-08
It did not work.

I was trying to avoid a reinstallation.
Also, adding irony to injury, now it doesn't mount blank cds or dvds: great!


Thnaks anyway,
Dead Cone

---

