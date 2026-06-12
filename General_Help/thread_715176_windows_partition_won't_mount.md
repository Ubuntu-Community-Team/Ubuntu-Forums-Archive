---
title: "windows partition won't mount?"
date: 2008-03-04
forum: General Help
---

### Post by jusmai77 on 2008-03-04
Right now when I boot into windows it goes to the main login screen, but once i log in it gets stuck at the 'personalizing your settings' screen.  I tried mounting windows by typing this into command prompt:

> sudo mount -t ntfs /dev/sda2 /media/sda2

(my windows partition is sda2) and got this error

> 
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:


i then booted into windows and shut it down from the log in screen menu, went back into ubuntu, typed in:
> sudo mount -t ntfs /dev/sda2 /media/sda2

and got a new error:

> 
fuse:  mount failed:  Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()


i now can access my files in windows from linux, but i'm still having the same problem with getting stuck on the windows loading screen.  does anybody know what i can do???

btw, here's the entry for the windows partition in the /etc/fstab file:
> 
# /dev/sda2
UUID=46D839BDD839ABD5 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1


---

### Post by taurus on 2008-03-04
It means that you didn't shut down your windows cleanly the last time you used it.  So, you need to boot into windows again and this time, shut it down cleanly instead of using the hibernation or sleep mode.  Then, Ubuntu should mount it fine now.

Otherwise, you can use the force option to mount it if you really need to access it.

---

