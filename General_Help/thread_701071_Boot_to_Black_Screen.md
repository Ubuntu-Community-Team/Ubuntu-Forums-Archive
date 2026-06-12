---
title: "Boot to Black Screen"
date: 2008-02-19
forum: General Help
---

### Post by hasek522 on 2008-02-19
I recently instialled Ubuntu and immediately after installation i was prompted to install a proprietary driver for my ATI x1600 gfx card.  So i installed the driver and restarted the computer.  Now when ever i choose to boot Ubuntu (i use dual boot) it gets to a blakc screen and my monitor tells me cant display this video mode.  How can i fix this?  I am very new to linux to please be specific.  Thank you very much in advance.
 
System Specs:
2.66 intel processor
x1600 gfx card
512 mb ram

---

### Post by InuIzzy on 2008-02-19
You should know you can press"ctrl-alt-F1" and it will bring you to the black screen with text (i am also pretty new and i dont know its official name) i think its an X-Server problem because that is what happened to me. My friend helped me fix it so i cant help a lot, but what you can do is look around the forum for xserver help. I know there is a simple way to fix it but i cant remember where i saw it. Don't give, it took me al day today to get my sound working But it works!! Even though it is very bad quality and I'll spend another 5 hours fixing that its ok because its fun!

---

### Post by Yellow Pasque on 2008-02-19
Do you know if your card is AGP or PCI-E?

I have a workaround for you. Try using the open-source radeonHD driver. To do this, boot in recovery mode. The option should be offered on a menu when you first start your PC (you may need to hit 'Esc' when prompted) Once there, log in as your normal user.
```
sudo apt-get install build-essential git-core configure-debian automake autoconf xorg-dev libtool linux-headers-`uname -r`
cd ~/
git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
cd xf86-video-radeonhd/
./autogen.sh --prefix=/usr/
make
sudo make install
```

After that's done, you will need to edit your /etc/X11/xorg.conf file:
```
sudo vim /etc/X11/xorg.conf
```
Press the 'i' key to put vim in text edit mode.

Add this code:
```
Section "Extensions"
Option "Composite" "Off"
EndSection

Section "ServerFlags"
Option "AIGLX" "Off"
EndSection
```

Also, change the Driver line in the Device section to:  "radeonhd"
Now, hit the 'Esc' key to tak vim out of edit mode and type the colon-x-{enter} to save the file
```
:x[Enter]
```
Now reboot and see if it works :)

---

