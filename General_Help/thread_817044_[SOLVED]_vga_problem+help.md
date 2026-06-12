---
title: "[SOLVED] vga problem+help"
date: 2008-06-03
forum: General Help
---

### Post by ravicplk on 2008-06-03
guys i installed ubuntu 7.10 and in the first log it gave me a message to install my vga drivers

my vga card is Geforce fx 5200. i installed the drivers and then restarted the machine,

when i came to the log in  screen the display is going wild.cant see anything clearly..
some lines are going up and down ,, i think this is a resolution problem.
please help mee

new to the forum..
thanks in advance/

---

### Post by ravicplk on 2008-06-03
:(:(:(:(:(
plzzzzzzzz help meee!

---

### Post by chewearn on 2008-06-03
Try login anyway, type username<enter> password<enter>.

If it is now able to shows the desktop, we can go to fixing the login screen.
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

---

### Post by ravicplk on 2008-06-03
> **AstalaVista said:**
> Try login anyway, type username<enter> password<enter>.

If it is now able to shows the desktop, we can go to fixing the login screen.
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

hmm i can login . but cant see anything clearly,with those lines moving like crazy, 
how can i fix this,

---

### Post by chewearn on 2008-06-03
Press CTRL+ALT+F2, you will be prompted to login the console.

Run this command to reconfigure your display:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

You choose nvidia for the driver, and the exact resolution of your monitor.

Then, restart X by pressing: CTRL+ALT+Backspace

---

### Post by ravicplk on 2008-06-03
> **AstalaVista said:**
> Press CTRL+ALT+F2, you will be prompted to login the console.

Run this command to reconfigure your display:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

You choose nvidia for the driver, and the exact resolution of your monitor.

Then, restart X by pressing: CTRL+ALT+Backspace

lets see.
thanks a lot.

---

### Post by ravicplk on 2008-06-06
> **AstalaVista said:**
> Press CTRL+ALT+F2, you will be prompted to login the console.

Run this command to reconfigure your display:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

You choose nvidia for the driver, and the exact resolution of your monitor.

Then, restart X by pressing: CTRL+ALT+Backspace

hii,sorry to disturb again but it didnt work for me..

when after entering this one
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
it says it is not installed and no info is found what to do now.??

---

### Post by chewearn on 2008-06-06
Could you post the actual error message?  You could be making a typo error.


Also, to clarify, your first post stated you have ubuntu 7.10, this is confirmed?  If you have 8.04 Hardy, this won't work.

---

### Post by ravicplk on 2008-06-07
> **AstalaVista said:**
> Could you post the actual error message?  You could be making a typo error.


Also, to clarify, your first post stated you have ubuntu 7.10, this is confirmed?  If you have 8.04 Hardy, this won't work.

i have ubuntu 7.10
wait i will post the error message.it is a bit long one.

---

### Post by ravicplk on 2008-06-07
it said that xserver xorg is not installed.i install it using "aptitude"........now it is giving another error message

start like
dpkg:conflicting actions -e(control) ...
type dpkg --help,,,

like that.

i am sick of this now.

---

### Post by chewearn on 2008-06-07
> **ravicplk said:**
> it said that xserver xorg is not installed.

I'm not sure where the typo is (while you are posting, or while you are running this command.  But there is a hypen between xserver and xorg, like this:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Don't miss any of the hypens.


> i am sick of this now.

Hang in there.

---

### Post by ravicplk on 2008-06-07
> **AstalaVista said:**
> I'm not sure where the typo is (while you are posting, or while you are running this command.  But there is a hypen between xserver and xorg, like this:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Don't miss any of the hypens.




Hang in there.

didnt miss anything bro..

---

### Post by chewearn on 2008-06-07
Ok, I'm not sure what else is wrong there.  The command should run in any Gusty install.  For reason I'm not familiar with, dpkg could be broken in your system.

I guess we might need to manually fix the problem.  Please copy out the file /etc/X11/xorg.conf from the system and post it here.  There are a few ways to do this, but try this first:

Boot into safe mode.  You do this by pressing <ESC> after POST, at the prompt (unless grub display the boot menu in your system by default).  I hope the display is ok when going into safe mode, and you are able to get internet access.  Else you might need to copy out the file via a USB drive or something.

Note of caution: when booting into safe mode, you have root privileges; be careful of the changes you made to the system, as you might inadventently broke it.

---

### Post by ravicplk on 2008-06-18
> **AstalaVista said:**
> Ok, I'm not sure what else is wrong there.  The command should run in any Gusty install.  For reason I'm not familiar with, dpkg could be broken in your system.

I guess we might need to manually fix the problem.  Please copy out the file /etc/X11/xorg.conf from the system and post it here.  There are a few ways to do this, but try this first:

Boot into safe mode.  You do this by pressing <ESC> after POST, at the prompt (unless grub display the boot menu in your system by default).  I hope the display is ok when going into safe mode, and you are able to get internet access.  Else you might need to copy out the file via a USB drive or something.

Note of caution: when booting into safe mode, you have root privileges; be careful of the changes you made to the system, as you might inadventently broke it.

ahhh thanks for u r great help. i finally figure it out.it was a problem in my monitor. some higher resolutions are not supported my monitor. so i changed the monitor . noow its ok..thanksssssssss AstalaVista for u r great help.

---

