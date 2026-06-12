---
title: "booting problems"
date: 2007-02-06
forum: General Help
---

### Post by smacd on 2007-02-06
I'm not new to Linux, but I am new to installation/admin stuff involving it.

I am working on a laptop (Toshiba A15-S157 ?), and have twice installed edgy eft on it. I am working on a project that requires some very recent versions of a number of programs. However, while in the process of installing these programs- my laptop has experienced a number of problems.

The first time, the screensaver came on (which had been working previously), when I tried to come back from the screensaver, there was a graphical artefact (a window that looked like it was trying to come up, but couldnt), and the screensaver remained active. So I powered down the machine and tried to reboot. Ubuntu loaded to the point where the busy mouse icon was there (the circle thingy), and just never advanced, after numerous tries

So I re-installed Ubuntu. I reached about the same point in the installation of the programs, and then there was a software update that Ubuntu tried to do. I let it go, and afterwards re-boot the machine. Again, it will boot as far as the loading mouse icon (only this time the moving circle inside moves halfway around then restarts), and never fully boots up.

The programs I am attempting to install is the latest version of GTK+-2, latest version of GSL, and the latest version of about 15 other programs that GTK+- relies on (or that the required programs rely on that it claims can't be found). Maybe some of them are there and I just don't know how to tell it where they are, but I feel that its fine, since I am able to make sure I have the latest versions that way.

The only other thing of note, is that I've had the version of gaim that is installed with edgy eft active and online at the time of the problems or rebooting, and a wireless connection to the internet at that time.

Any help would be appreciated.
-Sean

---

### Post by smacd on 2007-02-06
(I posted this in the Laptop section as well, but I'm not sure if the laptop is the reason for the problem I'm having so I'm posting this here as well-- my apologies if that is a problem)

I'm not new to Linux, but I am new to installation/admin stuff involving it.

I am working on a laptop (Toshiba A15-S157 ?), and have twice installed edgy eft on it. I am working on a project that requires some very recent versions of a number of programs. However, while in the process of installing these programs- my laptop has experienced a number of problems.

The first time, the screensaver came on (which had been working previously), when I tried to come back from the screensaver, there was a graphical artefact (a window that looked like it was trying to come up, but couldnt), and the screensaver remained active. So I powered down the machine and tried to reboot. Ubuntu loaded to the point where the busy mouse icon was there (the circle thingy), and just never advanced, after numerous tries

So I re-installed Ubuntu. I reached about the same point in the installation of the programs, and then there was a software update that Ubuntu tried to do. I let it go, and afterwards re-boot the machine. Again, it will boot as far as the loading mouse icon (only this time the moving circle inside moves halfway around then restarts), and never fully boots up.

The programs I am attempting to install is the latest version of GTK+-2, latest version of GSL, and the latest version of about 15 other programs that GTK+- relies on (or that the required programs rely on that it claims can't be found). Maybe some of them are there and I just don't know how to tell it where they are, but I feel that its fine, since I am able to make sure I have the latest versions that way.

The only other thing of note, is that I've had the version of gaim that is installed with edgy eft active and online at the time of the problems or rebooting, and a wireless connection to the internet at that time.

Any help would be appreciated.
-Sean

---

### Post by smacd on 2007-02-07
I've had this experience happen on two separate installs, and I do not know enough about linux administration in order to find the fix to the problem.

After a fresh install of Edgy Eft, I can use the system just fine for a short while (a day or two). However, for some reason, occasionally when I try to boot up the computer, the GUI locks up before bringing me to the desktop. However, I can switch over to a command prompt using ctrl+alt+F1.

I don't know why the boot starts locking up (and once it happens, it always does it when I try to boot up). And I don't know what I can do from the command prompt that might be able to fix this. Further... I have no idea how to boot from the cd in a way that I can access the installation that is on my hard drive (it always brings me back to the install environment).

Any help would seriously be appreciated. if not, I'm at the point where I'll just give up on Ubuntu and try a different distro.

---

### Post by CPtAJ on 2007-02-07
What exactly happens to the GUI? I had a similar problem where the login GUI wouldn't let me in and just reloaded itself. However I could ctrl+alt+f1 out and login there. The problem happened when my main HD partition was full. Try checking that while you wait for other responses.

Also, try using ctrl+alt+backspace to reload the x-server.

---

### Post by smacd on 2007-02-07
all I know, is that when I try to boot up my laptop, after a few times of booting where it works-  it starts doing this thing where it loads up to the off-brown orange screen, and the mouse icon turns into the loading spin-wheel thing. and it just sticks there until I turn it off. (the moving part of the loading only goes halfway around before it starts over). It never gets to a login screen.

I can log in using the command terminal I can get to... but as I dont have any experience with linux adm stuff, I have no idea what I can do from there to fix whatever problem the system is having.

edit: I'm fairly sure the partition isn't full-- its 10GB, and I have little more than a fresh install of Ubuntu on it.

---

### Post by CPtAJ on 2007-02-08
Seems like no one else saw this. Anyway, does ctrl+alt+backspace work to reset the whole thing?

It might be worth reinstalling gdm (gnome)

---

### Post by smacd on 2007-02-08
yeah, this is the second time I've asked, and havent gotten much help. I tried CTRL-ALT-Bksp, but it didnt help. I'm going to try booting normally, switching to a terminal, and trying startx (i think i saw that on another post). If that doesn't work, and if no one can give me a pointer to some sort of boot log (since I really don't know my way around the linux system... just how to use it mostly), I'll try Xubuntu/Kubuntu, or Dapper. And if either of those continue with this problem, I'll just try a different distro altogether.

---

### Post by smacd on 2007-02-08
Third time is the charm. hopefully. I've been having boot problems: the GUI wont load. I keep asking for help, but havent really gotten much response.

After a fresh install, installing some programs, and then rebooting, I can no longer boot into the GUI (it hangs while attempting to load). It boots fine before I install the other programs.

I can Ctrl+Alt+F1 into a command prompt. on tty1, I found:

> Starting up ... 
[17179571.916000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0

I have no idea what this means or how to fix it, but I'm assuming it is why I can't boot into the GUI anymore.

---

### Post by defishguy on 2007-02-08
Are you using a laptop (any make or model) with ATI video?

---

### Post by smacd on 2007-02-08
I am using a Toshiba A15-S157 model laptop- it has an intel based gpu

---

