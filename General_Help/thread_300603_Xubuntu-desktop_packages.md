---
title: "Xubuntu-desktop packages"
date: 2006-11-15
forum: General Help
---

### Post by lemonsCC on 2006-11-15
I am looking for the list of **all** the packages that are installed when you install xubuntu-desktop.  I am trying to install XFCE on a 200mHz 96MB RAM computer and dont want all the bloat that comes with gimp and the other "extras" that xubuntu-installs.  What is **required** for thw XFCE window manager?  I don't care about running different sessions, locking the screen, etc.  I do however want a little more than IceWM can provide.  Such as icons and a "prettier" looking system.

Also is there any way to not have an splash screen during boot.  I don't mind looking at white text (to conserve CPU and RAM.)  And to have the box autologin as it will only be used for internet access and possibly AbiWord.

Finally I know it exists somewhere on the forums.  How can I change what is started during boot.  This computer won't have a printer so CUPS is useless.  I also don't care about time server syncing, etc, etc.

---

### Post by encompass on 2006-11-15
I wouldn't use xubuntu with that much ram... stick with a text console if you want fun speed.
If you want to see... just look at the details of the xubuntu-desktop package.  But like I said... it takes about 74 to boot and then to run can take upto 200, depending.

---

### Post by encompass on 2006-11-15
To get rid of the splash screen take out the splash command in this file...
/boot/grub/menu.lst
use any editor you like as root to do it.
sudo nano /boot/grub/menu.lst
BTW... did you know you can run video in text mode?  it is called Framebuffer and used with mplayer.  Kinda fun to learn the console stuff.

---

### Post by CatKiller on 2006-11-15
[http://packages.ubuntu.com/dapper/misc/xubuntu-desktop](http://packages.ubuntu.com/dapper/misc/xubuntu-desktop)

---

