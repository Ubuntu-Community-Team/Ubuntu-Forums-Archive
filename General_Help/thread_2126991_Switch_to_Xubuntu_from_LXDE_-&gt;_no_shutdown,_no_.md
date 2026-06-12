---
title: "Switch to Xubuntu from LXDE -&gt; no shutdown, no title bars and no wireless"
date: 2013-03-18
forum: General Help
---

### Post by olddave1 on 2013-03-18
Hi,

Used forum Search, which is very slow and could not find a coverage of my problem.

I have LXDE, Ubuntu and Xubuntu all installed. I used LXDE and switched to Xubuntu, but each time I had to do "metacity -- replace" to get title bars and also it never allowed me to shutdown or restart or log out, I had to hit the reset button. But it did allow me to work. I added "metacity --replace" to my .profile and it now allows me to login but stalls immediately after. I used Ctrl Alt F1 and login in shell though I do get a msg "Window manager error: Unable to open X Display". Then when I try "sudo shutdown now" it fails "Killing all remaining processes". I managed to remove that line from my .profile and I get past the login, but the shutdown and metacity problems remain. I made sure it is up to date. I can also no longer connect to wireless it just spins it's wheels. All this from switching to Xubuntu from LXDE. I did install a new graphics card a HD7770, on Satruday, but was working fine all Sunday with it.

What next? Is there a way to debug these shutdown problems and the wireless. 


Thx.

David

---

### Post by Frogs Hair on 2013-03-18
To restart the window manager in XFCE use ```
xfwm4 --replace
```

---

### Post by FabulousCabbage on 2013-03-18
You could try removing Xubuntu and just install XFCE,I've heard that you can avoid a lot of problems by installing XFCE rather than the whole Xubuntu package, I don't know why.

sudo apt-get install xfce4

---

### Post by r.stiltskin on 2013-03-18
Even though I've read many times that you can have multiple desktops installed & just choose which one to use when you log in, my recent experience has been that it's a formula for trouble.  I was having problems similar to what you described, and worse.  For a while, I was even getting "no keyboard" errors while booting up.  How conflicts between desktop managers or window managers could corrupt my BIOS I have no idea, but apparently it did.  More than once.

If you want to use Xubuntu (xfce4) I suggest that you uninstall ubuntu-desktop, gdm, metacity and nautilus and as much of gnome as possible and use xfwm4, lightdm, xfce4-panel and xfce4-session, etc.  Once you get your system working normally again, you can reinstall whichever specific gnome apps that you want, as few at a time as possible so if something starts acting badly it'll be easier to identify the culprit.  (And if you want to reinstall nautilus make sure you configure it to NOT manage the desktop.)

---

### Post by williejones on 2013-03-18
Each desktop environment uses your hidden config files, writing their own and different information.  The desktop environments can get confused with another desktop writing to these files.  I would suggest only using one desktop.  You might want to do a clean install (to clear everything up) with your preferred desktop.

---

### Post by Impavidus on 2013-03-19
ubuntu-desktop and xubuntu-desktop seem to work together (at least, I have them both and never have had trouble), but adding lxde or kde to the blend seems to cause more problems.

---

### Post by Frogs Hair on 2013-03-19
I use the XFCE session which includes far less packages then the Xubuntu desktop and LXDE has a session outside of the Lubuntu  desktop as well . To clean up your system see the link.   [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by olddave1 on 2013-03-19
Hi,

I attempted to remove the packages you mentioned. But in the process it wants to install a bunch of other packages? And because my wireless networking is not working it cannot. The packages it wants to install are: compviz-kde comvizconfig-backend-kconfig kdelibs5-data libattica0.3 libdlrestrictions1 libkdecore5 libkdeui5

I do ifconfig wlan0 and the inet line is missing, inet6 line is there, UPBROADCAST RUNNING MULTICAST MTU:1500 Metric:1 is there. How do I debug this to see why it no longer connects? I also ran iwconfig and there is signal strength, nothing changed there.

Thx.

David

---

### Post by Frogs Hair on 2013-03-19
You will have to provide specific information  about what desktops and how they were installed and your wireless which I can't help with. It may be much less painless to backup your Ubuntu files and start fresh as suggested on an earlier post. You have a mess in your configuration and sorting it out with multiple desktops installed could be difficult.

---

