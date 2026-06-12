---
title: "Successful Beryl Install?"
date: 2006-11-20
forum: General Help
---

### Post by redbluemangle on 2006-11-20
I followed [this]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/ATI") guide to a T and now when I boot into Ubuntu the login screen gives a nosignal error to my monitor. ](*,) 

beryl sure is pretty har har!

any tips?

I'm running Dapper and my card is an ATi Radeon 9550 pro

---

### Post by redbluemangle on 2006-11-20
bump +

anybody know what part of those instructions could have cause my GPU to fail?

---

### Post by CowzRule on 2006-11-20
Sounds to me like you have a problem with your xorg.conf file. You're going to need to revert to a (hopefully) backed up copy of that file.
Reboot into "Recovery Mode". After logging in type```
cd /etc/X11
```Then type ```
ls
```A backed up xorg.conf file will look like "xorg.conf.something". You need to rename that file by typing```
sudo cp xorg.conf.xxx xorg.conf
```Then type ```
sudo shutdown -r now
```If that fixes your problem, I would then log into your normall (NOT XGL) session and follow [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25") guide for getting the driver installed correctly.

If you don't have a backed up copy of xorg.cong, then do this```
sudo dpkg-reconfigure xserver-xorg
```That will regenerate a new xorg.conf. I believe the first thing you'll be asked is what "X server driver" you want. Be sure to select "ATI". It'll then ask some more questions and generally you can accept the default selection. After that just reboot then install the driver.
I hope this helps.

---

### Post by redbluemangle on 2006-11-20
your recovery method worked and saved my bacon but the guide you provided led to the same result. 

It seems that my GPU is transmitting beyond my monitor's frequency range. using ctrl alt f2 I am able to log in text mode and from there when I issue the fglrxinfo command I get:

```

Xlib: connection to "0.0." refused by server
Xlib: no protocol specified 

Error: unable to open display :0

```

---

### Post by CowzRule on 2006-11-20
Sorry about the guide I posted not working. I used it when I first discovered Ubuntu and it worked just fine. Of course that was after a fresh install of Dapper. I'm now running Edgy so I had to use a different guide.
Is this problem happening when you select your XGL session only or is it also  happening when selecting the standard Gnome session?

---

### Post by redbluemangle on 2006-11-21
well the problem was occurring before I could even select a session. I would get the monitor error at the login prompt. The standard GNOME session works fine I haven't even tried the XGL sessions because I dont think my drivers are working. 

This is my fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by CowzRule on 2006-11-21
Alright, you need to add some info to your xorg.conf file. First lets back up the file:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Now open the file with:```
sudo gedit /etc/X11/xorg.conf
```Scroll down to the bottom and add:```
Section "Extensions"
      Option "Composite" "false"
EndSection
```Reboot```
sudo shutdown -r now
```
When you're back up do:```
fglrxinfo
```and hopefully it will show something that looks more like:> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.6065 (8.29.6)If it does, then this ```
glxinfo | grep render
```Should show:> direct rendering: YesIf it does, then give your xgl session a try.

---

### Post by redbluemangle on 2006-11-21
alright I'll give this a try next time I get a chance to reboot (I gotta keep  my share ratio up on a BitTorrent thingy) Thanks for the help!

---

