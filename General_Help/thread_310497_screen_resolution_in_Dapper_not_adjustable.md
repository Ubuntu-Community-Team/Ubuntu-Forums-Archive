---
title: "screen resolution in Dapper not adjustable?"
date: 2006-12-01
forum: General Help
---

### Post by taling on 2006-12-01
Hi,

I just bought the book "moving to Ubuntu Linux" which had the DVD in it with version 6.06 Dapper. I've tried the live version from the DVD but couldn't adjust the screen resolution from the pull down menu. It was not possible to choose another resolution then the default 640 x 480. I've tried the downloadversion of 6.06 en 6.10 and had the same problem. With version 5.10 Breezy Badger I do not have this problem. Is there anyone who can help me,:confused:  (I am new to Linux)

---

### Post by JoeC21 on 2006-12-01
What type of graphics card do you have?  It may be helpful to post your /etc/X11/xorg.conf file as well if you cant change it graphically it will most likely require some editing.

---

### Post by taling on 2006-12-01
> **JoeC21 said:**
> What type of graphics card do you have?  It may be helpful to post your /etc/X11/xorg.conf file as well if you cant change it graphically it will most likely require some editing.

My graphics card is a Matrox G550 and I get in Konsole no permission to access /etc/Xll/xorg.conf file

---

### Post by princemackenzie on 2006-12-01
> **taling said:**
> My graphics card is a Matrox G550 and I get in Konsole no permission to access /etc/Xll/xorg.conf file

Are you sure you are access /etc/X11/xorg.conf?  you typed /etc/Xll (as in XLL) there.  Its x11, as in the letter "x" followed by the number "11"

from konsole type "sudo kate /etc/X11/xorg.conf", and then copy and paste it on over.

Are you using an LCD or CRT monitor?

---

### Post by taling on 2006-12-01
> **princemackenzie said:**
> Are you sure you are access /etc/X11/xorg.conf?  you typed /etc/Xll (as in XLL) there.  Its x11, as in the letter "x" followed by the number "11"

from konsole type "sudo kate /etc/X11/xorg.conf", and then copy and paste it on over.

Are you using an LCD or CRT monitor?

 kate: command not found and I use a CRT monitor

---

### Post by princemackenzie on 2006-12-01
Are you using KDE or GNOME?  

On Gnome its

"sudo gedit /etc/X11/xorg.conf"

on KDE try

"sudo kwrite /etc/X11/xorg.conf"

Thanks...

---

### Post by taling on 2006-12-02
It appears I use Gnome ;) (didn't know that because I am a newbie)

I will try this

---

