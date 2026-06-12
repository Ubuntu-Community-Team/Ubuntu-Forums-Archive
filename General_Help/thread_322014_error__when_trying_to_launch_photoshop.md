---
title: "error:  when trying to launch photoshop"
date: 2006-12-19
forum: General Help
---

### Post by Magiczero on 2006-12-19
Hey guys!

I have a big problem I am trying to run photoshop on my system but I get an error:

> tanner@tanner-desktop:~$ wine /home/tanner/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/photoshop.exe
fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  34
  Current serial number in output stream:  34
tanner@tanner-desktop:~$ wineserver: could not save registry branch to /home/tanner/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/tanner/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/tanner/.wine/user.reg : Permission denied

tanner@tanner-desktop:~$ 



I have tried another ls command to see if I can figure out what is wrong but I can't

> tanner@tanner-desktop:~$  gksudo /home/tanner/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/photoshop.exe

(gksudo:11903): Gtk-WARNING **: Unable to locate theme engine in module_path: "bluecurve",


I need help!
Please?

Thanks a lot!

---

### Post by josephmc on 2007-01-11
same here

---

