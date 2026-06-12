---
title: "Splash screen hard freezes every time"
date: 2013-02-19
forum: General Help
---

### Post by vividexstance on 2013-02-19
I didn't know exactly where to put this, so if this isn't the right place, could a mod move it?

After a small update the other day, I restarted my computer and everything is fine until it gets to the splash/login screen.  The mouse pointer pops up and a second later the rest of the login screen except the background pops up.   The background is blackish/purplish with evenly spaced dots both horizontally and vertically.  When the mouse pointer pops up,  I am able to sometimes move it a little bit until the rest of the screen loads up and then it freezes.

I'm running Ubuntu 12.04 and I've been reading about people with similar issues but not exactly the same as mine.  I saw someone suggest to run Memtest from GRUB and I did that and it comes up with some errors.  So I thought it was maybe the RAM, but then I read somewhere how to set ubuntu to auto-login and I set it to do that.

If I boot the computer in a certain way and bypass the login screen, everything works and I can use the computer like normal,  I'm posting from the computer right now.  I can even play games so I don't think it's a video card issue.  This is what I have to do to get it to boot:

1) Turn computer on and hold left shift to get to the GRUB menu.
2) I enter recovery mode.
3) Enable networking
4) Resume and it goes into the OS.

If I do it any other way, it hard freezes.  Once I got into the OS, I backed my files up and I made a bootable USB flash drive on another computer running Windows XP.  If I try to run the install, I can see the logo at the bottom center of the screen for a few seconds and then it appears like its loading the install because the background is changed to that purplish background and there is the light grey panel at the top except the far right of it isn't showing.  I've left it at this screen for more than a day and it just seems like it's another hard freeze.

I really want to figure this out because I don't want to keep hard rebooting and damaging my HDD and whatever else.  I don't need to save any files, so if the easiest way is to reinstall that's fine.  Any help is appreciated.

---

### Post by libarts on 2013-02-19
I had a similar problem with an older computer that ran XP.  My solution was to re-install the entire OS.  If you have any reason not to, I wouldn't recommend it.  From what I remember, the problem had to do with my install disk, and when I re-installed with a new disk, no such problems recurred.

Good luck!

---

### Post by vividexstance on 2013-02-19
It's not just a problem with the install, it's also a problem with the Ubuntu that's already installed.  Also, it's not a disk but a bootable usb drive.  I followed the instructions from the ubuntu docs.

---

### Post by Bashing-om on 2013-02-19
vividexstance;
As some updates were done prior to the start of this situation and you are able to boot via the "recovery mode" -> uses the onboard "vesa" driver: indicates the former driver is broken.
try this:
from the recovery boot: 
Key combo ctl+alt+t to open a terminal:
terminal commands:
To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
```Then;
desktop ->launcher -> System Settings -> Additional Drivers: install an alternate driver.
[INDENT]worth a try

[/INDENT]

---

### Post by vividexstance on 2013-02-20
> **Bashing-om said:**
> vividexstance;
To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
```Then;
desktop ->launcher -> System Settings -> Additional Drivers: install an alternate driver.
I did think of this before but didn't try it.  I did it last night, installing the "recommended" driver.  Upon rebooting, it would load and pop-up tty0 or tty1 whichever the first one is.  I could CTRL-ALT-F7, but it brought me to a screen with all these things being started and all but a couple were ok.  It seemed like it was hanging at this screen, but I could still move to the different tty's and CTRL-ALT-DEL worked fine, so I don't think it was a hard freeze.

I was just about to go on another computer and post that update, but I tried a few things and voila, they worked and I logged in fine with the splash screen and everything.  The steps for what I did are:

1) apt-get remove lightdm
2) apt-get install lightdm
3) I edited the /etc/lightdm/lightdm.conf to turn off auto-login

I had tried this before but it didn't seem to do anything.  I'll keep this thread updated if it does act up again.  Thanks!

---

### Post by Bashing-om on 2013-02-20
vividexstance; Hey, Glad ya got it sorted out, up and running !

When sure, please mark this thread "solved" -thread tools above the post- so others find your solution.

[INDENT][INDENT]happy ubuntu'n

[/INDENT][/INDENT]

---

### Post by vividexstance on 2013-02-21
Actually I thought I had it working, but I'm still having the same problem.   Once I started having the problem, which is usually after a reboot, I took these steps:
1) Downloaded ubuntu desktop 12.04 from ubuntu's website onto another computer that is running windows.
2) I ran the program that is suggested by ubuntu to make a flash drive from the .iso that I downloaded. ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows))
3) I then booted the broken pc into the GRUB menu and then into recovery mode.
4) I selected to run a console as root
5) I removed all the partitions from the HDD using fdisk
6) Reboot using the flash drive and the installation didn't freeze like it was before.
7) Everything went ok but after some updates finished downloading and installing it said it needed to reboot.  Then the same problem happens again with the have loaded login/splash screen hard freezing.

The only way I can even use this computer is by running it in recovery mode.  I also ran a memory test and there was no errors.

---

### Post by Bashing-om on 2013-02-21
vividexstance;

I am still looking at this as graphics related... Lemme get caught up on some things to where I can reboot my box to verify what I have in mind.

[INDENT][INDENT]I'll be BACK 
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-02-21
vividexstance;

I'm Baaaaccck

OK. do this and see what results, we take it from there.

Boot to the grub menu -> "e" key for edit mode -> kernel parameters screen ->Arrow down to the line similar to this:
> linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash Arrow across to the term "quiet splash" remove all after the term "ro" and insert the term "text" -with out the quotes. -> ctl+x to continue the boot process to the text login,
Login with username then password. Now enter the terminal code:
```
sudo service lightdm start
```This takes you to the (hopefully) GUI login screen (be patient takes a bit to load Xserver)  ... login here also (be even more patient, takes a while to load the DE, my system is fairly fast and  even so takes more than a bit of time); 
What do you have now for a desk top ?
At this time do ctl+alt+f1 to return to the tty1 terminal. Do you see any reported errors ?
If you can not activate the GUI desktop, then from any terminal (ctl+alt+f1-6) terminal code:
```
sudo shutdown -r now 
``` to bring the system down gracefully.
[INDENT][INDENT]look'n to see what we are going to do
[/INDENT][/INDENT]

---

### Post by vividexstance on 2013-02-22
I'm going to try this now and I'll let you know what happens.  Also,  I think it has something to do with the graphics too because this only happened after I installed Steam and then Counter-Strike Source.

***EDIT***:  I just did what you told me to do and it seems like it worked.  I removed everything after the 'ro' on the line in grub, this was at the end of the line '$vt_handoff' so I removed that as well and added text to the line.  The computer then booted to the text login and I logged in.  Then I ran the command to start lightdm, which didn't take long at all and it loaded the splash/login screen which did not freeze and I was able to login.  I'm going to reboot right now to see if the problem is fixed or not.  I just looked at Ctrl-Alt-F1 and all it says is that it start lightdm and there are no errors.

---

### Post by vividexstance on 2013-02-22
After rebooting and letting it boot normally, the same problem still occurs.  It half-loads the login screen and hard freezes.  I can still get into ubuntu but only using the recovery mode.

---

### Post by Bashing-om on 2013-02-23
vividexstance;
Regret the delay getting back yo ya.

This had got me scratching my head ... I love a good puzzle ..

Tell me again that you are able to get to the desktop via text login and terminally start lightdm and reverting back to the terminal screen no errors are seen.

In this event, log back in terminally, start the desktop (lightdm) terminally and look at these logs just to see if there are any reported error. I really do not expect to see any as the desk top comes up.. But looksee anyway.
In your home directory is a hidden log file .xsessions-errors -> file manager (nautilus)-(ctl+h to hide/inhide the hidden file) and /var/log/syslog.
Might use the "log file viewer" to look at the system logs --dash ->search term "log file viewer", as this utility is tailored to display log files. //

No errors found ??? Ok, Lets see what it will take to load/start "steam" from the command line, and see what happens then.
[INDENT]seek'n anda search'n

[/INDENT]

---

### Post by vividexstance on 2013-03-20
Sorry for not getting back earlier,  but here's the situation.  A friend of mine let me use his video card which is better than mine and after putting the card in, the computer seems to boot fine.  I don't know if it was a hardware issue with the card, so when my friend wants his card back, I'll find out if the problem still occurs.

---

