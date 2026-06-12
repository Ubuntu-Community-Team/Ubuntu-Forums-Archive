---
title: "How do I modify boot loader"
date: 2015-09-06
forum: General Help
---

### Post by thetexan on 2015-09-06
After installing Ubuntu on my 7 machine the computer always goes to the boot loader, of course, but Ubuntu is the top choice and it default loads Ubuntu. If I want windows I have to select windows. 

How can I change the boot order of the loader so tha windows is the default choice?

Thanks
Tex

---

### Post by yancek on 2015-09-06
Change this line in the file:  /etc/default/grub.  It should be near the top of the file.  You need root privileges to edit this.  If you have a default Ubuntu, you should have the text editor gedit installed.  If you don't you'll have to figure out what text editor you have, so to open with gedit, in a terminal type:  sudo gedit /etc/default/grub  This should open the file and you will see the line below.  When you boot the system, count the entries down to windows and change the number zero to the proper one.  Count starts at zero so if windows is the third entry, change the line below to 2.  Run sudo update-grub in a terminal after the change is made.

> GRUB_DEFAULT=0

---

### Post by oldfred on 2015-09-06
[https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub](https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub)

Another way is to use description, but it must be exact, so copy it.
       find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

