---
title: "Desktop is broken. Displays no icons, cannot be clicked on."
date: 2008-05-22
forum: General Help
---

### Post by Crypty on 2008-05-22
In the last few days something happened. My desktop(i.e. the wallpapered one) will no longer display icons. I have files on the desktop but it does not display them. The files are present in the desktop folder however when I go to it in "places." 
I also cannot right click the desktop to make a folder, or change the wallpaper or anything like that. The menu simply does not pop up. I also cant click and drag a selection square on my desktop.
Everything else seems to work though, such as all my apps, AWN, nautilus etc. 

Any help is appreciated.

---

### Post by bigken on 2008-05-22
try this in a terminal sudo apt-get install ubuntu-desktop

---

### Post by Crypty on 2008-05-22
steve@steve-laptop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libflashsupport libboost-thread1.34.1 libboost-date-time1.34.1
  libwebkitgtk1d

---

### Post by bigken on 2008-05-22
sudo apt-get update
sudo apt-get upgrade

---

### Post by Crypty on 2008-05-22
That did it!
Thank you!

---

### Post by bigken on 2008-05-22
we got lucky :)


please mark this thread as sloved

---

### Post by Crypty on 2008-05-22
Hmm. I restarted and now the problem is back.

---

### Post by chrisccoulson on 2008-05-22
In a terminal, try:
```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true
```

Edit: You'll probably need to log out and back in again for it to take effect

---

### Post by strabes on 2008-05-22
Does a window appear if you hit alt+f2? If so, run "nautilus"

If not, hit Ctrl+Alt+F1, log in, and then run "nautilus". To get back to your desktop hit Ctrl+Alt+F7. Please let us know if this helps.

---

### Post by Grahamca on 2008-06-05
> **chrisccoulson said:**
> In a terminal, try:
```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true
```

Edit: You'll probably need to log out and back in again for it to take effect

Hello,
I am a Ubuntu Newbie as well and have run into some problems with the desktop similar to the chap above.  

I have a Toshiba Laptop A210, 
Was installing the wireless driver using ndswrapper, when i did the reboot i got the white screen in the upper left hand corner of the desktop.

I followed the "gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true" command in the terminal.  However it will only seem to allow basic functions.  I can not seem to connect to the internet with a wire.  Eventually I get to a point where the desktop is visible and looks normal, however there is no functionality.  I can not even shut down with the desktop.  I end up powering down with the power switch on the laptop.

Question:  Is this fixable, and if not I can easily reinstall, however i would like to recover a few photos i have loaded onto the computer.  Is there a way to access the photos from terminal and copy them to an external ram drive?

Thanks very much for your help.

Graham

---

