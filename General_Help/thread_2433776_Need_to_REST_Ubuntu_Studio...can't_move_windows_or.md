---
title: "Need to REST Ubuntu Studio...can't move windows or see menus"
date: 2019-12-25
forum: General Help
---

### Post by ic-racer on 2019-12-25
I have been trying to setup Ubuntu Studio for the last month (I'm on a different computer now). I did create some DAW files in Ardour and Qtractor, but today can't navigate through the desktop to do anything anymore. 

This is what I see when I start the computer
1) The mouse shows and "X"
2) FireFox and Qtractor keeps automatically opening at every re-start. 
3) FireFox takes up the left side of the screen and its menubar does not show. So I can't move the window or close it. But I can type in the ULR field.
4) Can't see any menu items. I was able to open terminal and download and start "Resetter"
5) Can't copy from the FireFox screen (to copy terminal commands), so I'm trying to type things into terminal to reset the system. 
6) With this limited functionality I was able to save my HOME and DOCUMENTS and some other folders to an external disk.
7) Before totally re-installing everything I thought I'd try "Resetter"
8) Resetter gives some errors like "Manifest not found" and the buttons just seem to lock up the screen. 

Anything else I might try to reset Ubuntu Studio via the Terminal?   I was able to get to the "Settings" menu but the "Windows" and "Panels" and "Menu" commands just lock up and don't run.

---

### Post by CelticWarrior on 2019-12-25
At this point and knowing that you already have backups, my suggestion is to reinstall. Then, when recovering from the backups, start with your personal files and your personal files only. Your problem can be related with some rogue user setting and it may come back if you recover all of your /home, which includes those settings.

---

### Post by ic-racer on 2019-12-25
Thanks for quick reply. I found this link to re install Studio which I recall might be how I got studio running with my initial install of ubuntu

https://askubuntu.com/questions/298581/updating-to-ubuntu-studio

---

### Post by ic-racer on 2019-12-25
Update, the link I found did not work. Just to update, every time I reboot (maybe ten times now) FireFox and Qtractor and now Terminal all boot up, but the mouse can't move the windows around. Also can't "copy" from the mouse. It shows the menu for copy with left-click but when I move to select the "copy" item it disappears.  Curser is still an "X"

This is what I have tired and nothing has any effect on the desktop view

sudo apt-get install ubuntustuido-desktop
reboot
##NO CHANGE

sudo apt-get install ubuntustudio-audio linux-lowlatency
## this just indicated it was allready installed

try:
sudo apt-get remove ubuntustudio-desktop
sudo apt-get install ubuntustudio-desktop

These commands looked like they did something in the terminal with successful completion of the commands and no errors,
after reboot
NO CHANGE#@#@#!!

Next I tried:
sudo apt ubuntustudio-installer

I ran the installer and rebooted

NO CHANGE!!


I also disconnected my external drive (with the copy of my 'home' folder) just to make sure none of the commands were directed toward that folder 

So at this point I don't know how to re-install Ubuntu Studio or remove it. Nothing seems to work.

---

### Post by ic-racer on 2019-12-25
So now I'm downloading the ubuntustidio 19.10-dv...64.iso  to make a new boot CD and will re-install that way. Will report back if this works in case anyone else finds this thread and also needs to reset the desktop.

---

### Post by ic-racer on 2019-12-25
So, disk image is burning now. Why i don't already have this is because i installed ubuntu from a different disk image (the standard or non-Studio) and after plahying around with it for a few days then ran the Studio installer. This was about a month ago. So I never did have the Studio ISO image until now.

Also, looking back through my notes it seems all heck broke loose with the desktop when I tried to use a FireWire audio/midi interface last week. 

To get that to work it said I had to install jackd1-firewire, which did now work, so I had to install jackd1 ,but I saw lots of bad things fly by in the terminal window during that install, like it was removing big chunks of ubuntu studio
The FireWire did suddenly start working but the desktop and menus all got messed up.

---

### Post by ic-racer on 2019-12-25
Closure on this thread. I installed the CD and it is back to normal. Now I need to do all the months-woth of tweaks over again to get it to work right. 

Stumped now on how to exchange command and control keys. I was able to do it previously but xkeycaps does not seem to do it any more. Spent already 2 hours on this.

Second major issue is there is no 'shut down' or 'reboot' button anywhere. I had worked on this for a couple weeks with no result, but maybe this is how I messed up everything; trying to change those menus. there seems to be no documentation on the Ubuntu Studio menus and how to change them or even add a shut down button. 

I'll just use the terminal for now to shut down and re-boot. 

Good news is Qtractor and Ardour both booted up with Jack working first time. I was able to find all the plugins too.

---

