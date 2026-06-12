---
title: "OK, one final, last ditch effort before trying another distro"
date: 2005-07-07
forum: General Help
---

### Post by SuperKev on 2005-07-07
Hi all,

I have been using Ubuntu for a couple of months now and I need some help to get full use out of it or I need to, unfortunately, dump it for another distro. I will list the things I need to get sorted and hopefully someone will be willing to hekp out. I really like using Ubuntu but it seems that for anything really productive I end up having to use my XP machine, and I hate having to do that. I have Ubuntu and my XP machine hooked up via router and was at one time successful at setting up printer sharing (printer is connected to the XP machine) but for some reason when I went to print out a document last week it had stopped working and I had to re-write the whole document in windows so I could print it. So you can see my dillema. Ok, below are the things I need to get sorted so I can use Ubuntu/Linux to it's fullest. And I thank any and all who take their time to help- Thank You!!

1- Sound, I have no idea how to get this working I have a yamaha OPL3-SAX sound card and I know it works as it does fine when booted up in Windows 2000 which is the dual boot on this box. 

2- Printer sharing, I want to use Ubuntu for all my non-gaming activities so this is important to get running and keep running but this apparently is a hit and miss proposition at the moment. 

3- File sharing, if there is a file or document on the windows box I would like to be able to grab it from there and edit it or whatever on Ubuntu then either save it back to windows, print it or save it to Linux. I tried to set this up but with no success. I followed a tutorial I found to the letter but no joy. 

If I can get these three things working-consistantly- then I will be a very happy camper indeed. I really don't want to switch from Ubuntu if I can aviod it and I hope some of you might be able help me avoid that unpleasant prospect. 

Thank you again!

---

### Post by scoon on 2005-07-07
Hey there, 

Sound: Check the cards compatability with this site: [http://www.alsa-project.org/](http://www.alsa-project.org/)
Printing: [http://www.linuxprinting.org/cups-doc.html](http://www.linuxprinting.org/cups-doc.html)
File Sharing: open up a shell: man samba or [http://us2.samba.org/samba/](http://us2.samba.org/samba/)

Also, threatening to switch distros doesn't really help with solving your problems.

regards, 

scoon

[QUOTE=SuperKev]Hi all,

I have been using Ubuntu for a couple of months now and I need some help to get full use out of it or I need to, unfortunately, dump it for another distro. I will list the things I need to get sorted and hopefully someone will be willing to hekp out. I really like using Ubuntu but it seems that for anything really productive I end up having to use my XP machine, and I hate having to do that. I have Ubuntu and my XP machine hooked up via router and was at one time successful at setting up printer sharing (printer is connected to the XP machine) but for some reason when I went to print out a document last week it had stopped working and I had to re-write the whole document in windows so I could print it. So you can see my dillema. Ok, below are the things I need to get sorted so I can use Ubuntu/Linux to it's fullest. And I thank any and all who take their time to help- Thank You!!

1- Sound, I have no idea how to get this working I have a yamaha OPL3-SAX sound card and I know it works as it does fine when booted up in Windows 2000 which is the dual boot on this box. 

2- Printer sharing, I want to use Ubuntu for all my non-gaming activities so this is important to get running and keep running but this apparently is a hit and miss proposition at the moment. 

3- File sharing, if there is a file or document on the windows box I would like to be able to grab it from there and edit it or whatever on Ubuntu then either save it back to windows, print it or save it to Linux. I tried to set this up but with no success. I followed a tutorial I found to the letter but no joy. 

If I can get these three things working-consistantly- then I will be a very happy camper indeed. I really don't want to switch from Ubuntu if I can aviod it and I hope some of you might be able help me avoid that unpleasant prospect. 

Thank you again![/QUOTE]

---

### Post by DRF on 2005-07-07
Sound - A quick look at the ALSA site and I can't see an OPL3-SAX on the list. But OPL3-SA2 and OPL3-SA3 are on the list as supported. A quick look in my modules directory reveals that there are a couple of modules installed that look like the correct ones (installed by default with my installation as I don't use that sound card). It might be handy for you to run the lsmod command in the terminal and say if anything is listed with opl3 in the name (or something similar). That way we will be able to determine if the driver is loading or not.

Printer sharing - Depends on the type of printer and where it's connected. If it's connected to your ubuntu computer by a parallel cable you should be able to use it. If it's connected to the network there is a good chance it will work. If it's connected to your computer by USB theres a bigger chance of it being a windows only printer. (but there are often ways around this) - basically we need to know more about the printer

File sharing shouldn't be a problem. What you need are the 'samba' packages which are on the ubuntu CD. Follow the instructions in the guide at [www.ubuntuguide.org](www.ubuntuguide.org) but if you just want to access your windows computers shared files and the windows computer has sharing enabled you can just do:
sudo apt-get install samba
sudo apt-get install smbfs
Then go to 'Places' and 'Network servers' and open the correct workgroup for your network and hopefully you should see your windows computer.

Daniel

---

