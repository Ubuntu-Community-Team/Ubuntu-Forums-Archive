---
title: "I got black screen after boot"
date: 2016-01-20
forum: General Help
---

### Post by OVNI67 on 2016-01-20
Hi:
Please, I need your help. I have Ubuntu 15.4 running in a Dell Laptop, Latitude 6400. When I turn on the computer, I see the Ubuntu sign, with some points indicating that the system is loading. After that, the computer doesn't show the desktop, it shows a Black Screen instead. I only see the mouse pointer, and I'm able to move it. The wiFi indicator is on and blinking letting me know that the networking/wifi operations are working. The hdd indicator turns on and blinks often. But I cannot get my desktop back only a black screen.
Pls, may someone tell me any idea about what can I do?  I'll appreciate greatly, Thanks in advance.

---

### Post by mörgæs on 2016-01-20
Hi, welcome to the fora.

If there's nothing of value on the hard drive then just do a fresh install of 15.10. 
15.04 has only two weeks of support left so there is no point in salvaging the installation.

---

### Post by xp15 on 2016-01-20
Can you open the console? (Ctrl+Alt+F1)
If you do, enter your username (the home folder name which begin with a small letter, not the one you see at login).
press enter and enter your password. press enter and wait for it to stop with the XXX@XX $ thing.

there you can try stoping the lightdm service (the graphic service), just type:
```
sudo service lightdm stop
```

press enter and give him your password.
wait for it to finish (XX@X$) And run the same command but change 'stop' to 'start'.

What does it do? can you picture if theres something interesting?

---

### Post by OVNI67 on 2016-01-21
> **xp15 said:**
> Can you open the console? (Ctrl+Alt+F1)
If you do, enter your username (the home folder name which begin with a small letter, not the one you see at login).
press enter and enter your password. press enter and wait for it to stop with the XXX@XX $ thing.

there you can try stoping the lightdm service (the graphic service), just type:
```
sudo service lightdm stop
```

press enter and give him your password.
wait for it to finish (XX@X$) And run the same command but change 'stop' to 'start'.

What does it do? can you picture if theres something interesting?

I'm sorry, I've just see this advise, and thanks you very much. I did all the steps, one by one 
but at the end I get the same, a Black Screen, and if I move my finger over mouse pad, I get 
the mouse pointer on the screen.
What was I supposed to see? Another idea?
Thanks

---

### Post by xp15 on 2016-01-21
An error. Did it happend after an update or something that you did? or was it like that after installation?

Also, what is your graphic card? from googling your laptop model it should be 'NVIDIA Quadro NVS 160M' _or_ 'Intel 4500MHD'. What do you have?

You can run the next command at the console (Ctrl+Alt+F1):
```
lspci
```

It will show you all your pci things, including your grapic card. if you cant locate it, post a picture here.

---

### Post by OVNI67 on 2016-01-21
> **xp15 said:**
> An error. Did it happend after an update or something that you did? or was it like that after installation?

Also, what is your graphic card? from googling your laptop model it should be 'NVIDIA Quadro NVS 160M' _or_ 'Intel 4500MHD'. What do you have?

You can run the next command at the console (Ctrl+Alt+F1):
```
lspci
```

It will show you all your pci things, including your grapic card. if you cant locate it, post a picture here.

Thanks again. I do know it's an INTEL, **[COLOR=#444444][FONT=Trebuchet MS][B]Intel GM45/GE45/GS45 Integrated Graphics**[/FONT][/COLOR][/B]. Running lspci, the information related to graphics card :

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:02.1 Display Controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I hope this it's enough. Thanks

---

### Post by Vladlenin5000 on 2016-01-21
Well, back to post #2. Please read and understand.

---

### Post by xp15 on 2016-01-28
Well, guess we need to install the right drivers then, but how. I mean, all you got is the textual, though Ive heard you can boot a live cd and installing it from there to your installed system.
Sry for the delay, im not used to be here much, just had a problem by myself so I tried helping others while waiting for an answer.

I'll look and read some related stuff and will come back, if I wont forget.

---

### Post by xp15 on 2016-01-28
Well I got this: [http://askubuntu.com/questions/245410/how-to-install-uninstall-a-driver-on-a-frozen-system-using-a-livecd](http://askubuntu.com/questions/245410/how-to-install-uninstall-a-driver-on-a-frozen-system-using-a-livecd)
And intel driver is available here: [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)
not sure, but still pretty sure you sould download the driver deb package for ubuntu 15.10, but since you has 15.4 then download that one:
for 64: [https://download.01.org/gfx/ubuntu/15.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.2.0-0intel1_amd64.deb](https://download.01.org/gfx/ubuntu/15.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.2.0-0intel1_amd64.deb)
for 32: [https://download.01.org/gfx/ubuntu/15.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.2.0-0intel1_i386.deb](https://download.01.org/gfx/ubuntu/15.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.2.0-0intel1_i386.deb)

First you should download the deb file from another computer or any working system, then you have two options (or more, but I dont know them or too lazy to think of)
1) install it through the console (Ctrl+Alt+F1), but then you need a way to connect the internet in textual mode. If you can connect the pc to router by cable it would be perfect, it will connect you to the internet immediatly.
the installation command is basically:
sudo dpkg -i DEB_PACKAGE

You only need to remember or write on a note the name of your file.
plus you need to learn how to mount your usb... oh god im tired.

connect it.
run "sudo fdisk -l" (its an L) and detect your usb stick directory, which is mostly /dev/sdb. oh foregt it, just:

1) download the right file and save to a usb, then connect it.
2) mount your usb as the guy with a green V says here: [http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal-how-can-i-mount-a-flash-driv](http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal-how-can-i-mount-a-flash-driv)
3) enter the mounted drive (save your files directly on the drive, otherwise you'll have to add next folder as /media/usb/FOLDER): **cd /media/usb**
4) run [B]sudo dpkg -i FILENAME
[/B]5) assuming you are connected to the internet by a cable (wired connection), or that you found a way to connect with a wifi, then all you need to do is relax and wait,
and tell us what it did when it finish.


The second option is running a live cd and doing as mentioned here (Green answer): [http://askubuntu.com/questions/245410/how-to-install-uninstall-a-driver-on-a-frozen-system-using-a-livecd](http://askubuntu.com/questions/245410/how-to-install-uninstall-a-driver-on-a-frozen-system-using-a-livecd)
Im not sure if you can install from the liveCD with the gui, but it should work too so just try, otherwise just install the deb as said at (4).

---

