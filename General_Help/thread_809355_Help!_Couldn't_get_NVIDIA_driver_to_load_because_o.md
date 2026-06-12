---
title: "Help! Couldn't get NVIDIA driver to load because of x-server."
date: 2008-05-27
forum: General Help
---

### Post by jwill1515 on 2008-05-27
Unmarked x-server in Synaptic. Just get a black screen now. Tried all sorts of ways to enable Nvidia driver through threads in forumwith no luck. Said it couldn't load because xserver was running. Unmarked xserver in Synaptic because I tried about everything else. Everything worked fine with 22.14 kernel. Can't get NVIDIA to work with newer kernels. Using HP Pavilion dv9205us laptop, 2GB RAM, AMD Turion dual 64-bit processors.

---

### Post by _godbout_ on 2008-05-27
Try this if you're running the 32bits version:

0 - Download the nvidia driver for linux here: [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)
0.5 - Extract the file where you want
1 - Open a tty by Ctrl+Alt+F1
2 - Type sudo /etc/init.d/gdm stop
3 - Enter your password
3.5 Type cd path_of_the_NVIDIA_driver
4 - Type sudo sh NVIDIA_..._.run
5 - Enter your password, and follow the instructions

The installation should work and you should have your card working with the latest kernel.

---

### Post by jocko on 2008-05-27
> **jwill1515 said:**
> [COLOR=Red]Unmarked x-server in Synaptic.[/COLOR]
Without an x server (the base for the entire graphical system) there is no point to install any video driver.
The nvidia installer tells you to *stop* the x server, not *remove* it (or perhaps it tells you that it cannot be run while the x server is running, which is silly).

To reinstall xorg, you could probably reinstall the package "ubuntu-desktop", which will bring back everything that was removed together with xorg.
You can still log in to a command line, right?
In that case, type this command:
```
sudo apt-get install ubuntu-desktop
```After that, you should be able to start the login screen by typing this command:
```
sudo gdm
```And, finally, to install the nvidia driver, **do NOT use nvidias installer, there are two much simpler methods available**:

[SIZE=3] 1. [/SIZE]Start the restricted-manager (System --> Administeation --> Hardware Drivers).
    It should tell you that there are proprietary drivers available for your video card.
    Click "enable", let it do it's magic, reboot and all should work.

If method 1 does not work (but try method 1 first, it should be the preferred method):

[SIZE=3] 2. [/SIZE]Install the package envyng-gtk (you'll find it in synaptic).
   Start the program (type envyng-gtk in a terminal or find it in the menus).
   I've never used envyng-gtk, so I can't explain any more, but it should not be too hard.

---

### Post by jwill1515 on 2008-05-27
> **_godbout_ said:**
> Try this if you're running the 32bits version:

0 - Download the nvidia driver for linux here: [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)
0.5 - Extract the file where you want
1 - Open a tty by Ctrl+Alt+F1
2 - Type sudo /etc/init.d/gdm stop
3 - Enter your password
3.5 Type cd path_of_the_NVIDIA_driver
4 - Type sudo sh NVIDIA_..._.run
5 - Enter your password, and follow the instructions

The installation should work and you should have your card working with the latest kernel.

I tried that and it didn't work.

---

### Post by jwill1515 on 2008-05-27
> **jocko said:**
> Without an x server (the base for the entire graphical system) there is no point to install any video driver.
The nvidia installer tells you to *stop* the x server, not *remove* it (or perhaps it tells you that it cannot be run while the x server is running, which is silly).

To reinstall xorg, you could probably reinstall the package "ubuntu-desktop", which will bring back everything that was removed together with xorg.
You can still log in to a command line, right?
In that case, type this command:
```
sudo apt-get install ubuntu-desktop
```After that, you should be able to start the login screen by typing this command:
```
sudo gdm
```And, finally, to install the nvidia driver, **do NOT use nvidias installer, there are two much simpler methods available**:

[SIZE=3] 1. [/SIZE]Start the restricted-manager (System --> Administeation --> Hardware Drivers).
    It should tell you that there are proprietary drivers available for your video card.
    Click "enable", let it do it's magic, reboot and all should work.

If method 1 does not work (but try method 1 first, it should be the preferred method):

[SIZE=3] 2. [/SIZE]Install the package envyng-gtk (you'll find it in synaptic).
   Start the program (type envyng-gtk in a terminal or find it in the menus).
   I've never used envyng-gtk, so I can't explain any more, but it should not be too hard.



Thanks, I will give that a try and post back later this evening.

---

### Post by Riffer on 2008-05-27
> **jocko said:**
> 
   I've never used envyng-gtk, so I can't explain any more, but it should not be too hard.

First uninstall the nvidia driver, reboot.  Then reinstall the nvidia driver, reboot.  Thats it!

---

### Post by jwill1515 on 2008-05-27
Still stuck. Guess I need to be online to sudo apt-get instal ubuntu-desktop. I won't be able to get online in Linux until I get this fixed. Any other ideas?

---

### Post by jwill1515 on 2008-05-28
That worked. I got my desktop back but still can't load the NVIDIA driver. It's not listed in the Hardware Drivers and I Installed with driver Envy NG and rebooted. Still no NVIDIA.

---

### Post by KnavishClout on 2008-05-28
I had the same problem.  A few months back I tried and got it to work.  Last week I hit the same group of problems and I ended up spending a few hours messing with stuff.  In the end I used a workaround, but it works.

Open your xorg.conf file.  Find where the video is listed and make sure it says "nvidia" and not "nv" or whatever the other default may be for you system.

You'll need to use "gksudo gedit" to get permission to write to the file.  Then use the  above method to enable restricted drivers.

---

### Post by jwill1515 on 2008-05-28
Thanks for the reply. I tried to edit the xorg.conf file but it said I didn't have permission. Why is that? Shouldn't I be able to access all files?

So, how do I run that command? gksudo gedit /etc/X11/xorg.conf?

---

### Post by pedro_orange on 2008-05-28
> **jwill1515 said:**
> Thanks for the reply. I tried to edit the xorg.conf file but it said I didn't have permission. Why is that? Shouldn't I be able to access all files?

So, how do I run that command? gksudo gedit /etc/X11/xorg.conf?


sudo nano -w /etc/X11/xorg.conf

---

### Post by jocko on 2008-05-28
> **jwill1515 said:**
> Thanks for the reply. I tried to edit the xorg.conf file but it said I didn't have permission. Why is that? Shouldn't I be able to access all files?

So, how do I run that command? gksudo gedit /etc/X11/xorg.conf?

If any user had permission to edit system files, the system would be very insecure (viruses, hackers and inexperienced users would be able to destroy the system).
You need to use sudo or gksudo to get temporary permissions to edit the file.
Open up a terminal and type:```

gksudo gedit /etc/X11/xorg.conf
```

---

### Post by jwill1515 on 2008-05-28
OK. I tried all of that and still nothing. I edited the xorg.conf file, uninstalled NVIDIA driver, rebooted, installed NVIDIA driver, rebooted. No driver in Administration/Hardware Drivers. Anything else I can try? Thanks.

---

