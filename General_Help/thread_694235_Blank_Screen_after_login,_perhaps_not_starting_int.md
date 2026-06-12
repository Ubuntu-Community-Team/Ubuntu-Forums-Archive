---
title: "Blank Screen after login, perhaps not starting interface"
date: 2008-02-11
forum: General Help
---

### Post by toomuchcomputertime on 2008-02-11
I am trying to start Ubuntu. I have been using it for several days. I left it alone while installing several packages, and 1.5 hr later, came and found blank beige (login screen color) screen. I have rebooted several times, and after login, I get the same screen. I have tried all the session options.  The terminal session is the only one that worked. This is an HP6745C w/ 512Mb RAM. Thanks in advance.

Summary:
-allows for input of user name and password
-crunches on hard drive for about 5 minutes
-hangs on beige screen
-ctrl-alt-bkspc allows restart of xserver
-allows terminal session (not real helpful for a novice)

---

### Post by neurostu on 2008-02-12
what is your video card?

---

### Post by toomuchcomputertime on 2008-02-12
I am not sure, how can I find out from the terminal? I will reboot, and try to see it that way. Thanks for the reply.

---

### Post by toomuchcomputertime on 2008-02-12
I looked in the CMOS, and didn't find the card type there.

---

### Post by plucky on 2008-02-12
> how can I find out from the terminal?

**Applications > Accessories > Terminal** ```
lspci
```

Look for **vga**

Good luck

---

### Post by toomuchcomputertime on 2008-02-12
The video card is a PCI local bus Intel 810. [http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph05963&lc=en&cc=us&dlc=ru&product=58147#N832](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph05963&lc=en&cc=us&dlc=ru&product=58147#N832). Thanks

Using command Lspci It appears to be Intel 82810 GMCH

---

### Post by toomuchcomputertime on 2008-02-12
Does anyone have any suggestions? This happens with both the normal user, and the administrator.

---

### Post by plucky on 2008-02-12
Try to reset your xorg.conf file with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
startx
``` or reboot

Good luck

---

### Post by toomuchcomputertime on 2008-02-12
It is still doing the same thing. I ran the commands, but it gave these errors 
FATAL: Error inserting battery
FATAL: Error inserting battery
FATAL: Error inserting battery :No Such device

There were also some paths in parentheses. the startx says:
"X: user not authorized to run the X server, aborting"

After the reboot, I have the same problem. 

Thanks for the response.

---

### Post by toomuchcomputertime on 2008-02-12
I have been researching, and appears that it might be a gnome problem.

---

### Post by plucky on 2008-02-12
toomuchcomputertime,

You could try to reinstall the **ubuntu-desktop** with ```
sudo apt-get install ubuntu-desktop
```.

I haven't tried this so I don't know if it will work,but if you haven't got a desktop I don't see any harm if you are going to reinstall the system.


What is the Gnome problem?

Good luck

---

### Post by toomuchcomputertime on 2008-02-12
Thanks everyone for your help, I am reinstalling.

---

### Post by NilsHG on 2008-02-12
> **plucky said:**
> Try to reset your xorg.conf file with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
startx
``` or reboot

Good luck

I had a similar problem. This command messed up my xorg.conf. I stopped gdm, manually edited xorg.conf with vi and restarted gdm. this brought me back to my normal desktop

---

### Post by vmantva on 2008-05-17
I have the same problem. 
I have reason to believe its gnome problem but nothing has worked so far and my console skills are also lacking...
Ref ubuntuforums.org/showthread.php?p=4973794.

---

