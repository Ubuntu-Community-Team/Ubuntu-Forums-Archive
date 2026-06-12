---
title: "[SOLVED] nvidia drive problem"
date: 2007-12-24
forum: General Help
---

### Post by cotcot on 2007-12-24
I want to get rid of the newest nvidia driver to check if this solves the well known freezes in my gutsy 64 bit with nvidia 7300GS.
I used envy to install an older version (9643). In the restricted drivers manager i see that the 9643 driver is in use WITHOUT the check box showing that it is enabled. Obviously this prohibits to use compiz as it asks to enable the nvidia driver. Is this driver to old for compiz ?
How can this be solved.
If not what is another way to install an older nvidia driver (i would like to have 9755) ?
Thanks

---

### Post by PmDematagoda on 2007-12-24
Download the Nvidia driver for 64bit Linux from [here]("http://www.nvidia.com/object/unix.html").

After that is done, kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

Navigate to where the installer has been downloaded to and execute it using:-
```
sudo sh nameofinstaller
```

After the installation is completed, do:-
```
sudo dpkg-reconfigure xserver-xorg
```

After the X-Server is reconfigured, start the GUI using:-
```
sudo /etc/init.d/gdm start
```

That should fix your problem.

EDIT:- Thank you for the correction cotcot:).

---

### Post by cotcot on 2007-12-25
Thanks for taking your time to reply. 
Unfortunately it did not work. 
I ran the installer from the nvidia website. It went all through and after reboot I saw that it was not installed at all. 
The code ```
sudo dpkg-reconfigure xserver-xorg
``` gave an an unknown message command. It did not search further because the installer did not install anything. 
I found on [[COLOR="Red"]the envy blog[/COLOR]]("http://albertomilone.com/wordpress/?p=138") some tips (item 4) that gave my compiz working with the older driver. Only during  boot when i have to fill user and password i get a low resolution (800x600) but finally it gives me compiz on a 1280x1024 screen.

Finally the goal was to avoid freezes with an older nvidia driver. It looks promising.

---

### Post by PmDematagoda on 2007-12-25
Did you get any errors during the install?

---

### Post by cotcot on 2007-12-25
No errors seen. The text scrolls fast. I might have overlooked it. I did not check a log file.

---

### Post by PmDematagoda on 2007-12-25
Wait, did:-
```
sudo dpkg-reconfigure xserver-xorg
```
work at all? Or did it fail?

---

### Post by articpenguin on 2007-12-25
try using envy
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by cotcot on 2007-12-26
> **PmDematagoda said:**
> Wait, did:-
```
sudo dpkg-reconfigure xserver-xorg
```
work at all? Or did it fail?
I got the error message "command unknown".

I do not search any further. I got nvidia 96 43 on both system (64 and 32 bit). 

Articpinguin : I started the thread with the message that i did an installation with envy but that it did not allow me to enable compiz effects. This is meanwhile solved with a suggestion from the envy author's blog.

---

