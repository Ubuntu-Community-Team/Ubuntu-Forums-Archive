---
title: "wubi 8.04 installation failed"
date: 2008-02-21
forum: General Help
---

### Post by andy100 on 2008-02-21
I'm testing Wubi-8.04-alpha-rev431, the program down load the iso image and the ask for reboot.
when the system restart I chose ubuntu but the program go in loop:
Buffer I/O error on device fd0, logical block 0
My pc is a laptop without floppy
suggestion ? thank you

---

### Post by ago on 2008-02-21
Can you boot in verbose mode? At what stage exactly does it happen?
Can you interrupt it to get to a shell?

---

### Post by andy100 on 2008-02-21
now I have deleted all file and now I have restart wubi program (47%download..). I'm sorry but I'm not unix expert. 
Tell me what I have to do to boot in verbose mode

---

### Post by andy100 on 2008-02-22
With a new ubuntu.iso I have restart the program and the installation procedure start correctly, but after 3 hours the installation is not finish ... the screen is black and the led of disc blinking occasionally.
Pentium P4 1.6 GHZ CPU
256MB Ram DDR-SDRAM
30GB Hard Disk Drive (with win xp - 25 gb free 10gb to Ubuntu)
:(

---

### Post by ago on 2008-02-22
andy 256MB is borderline for the graphical installer.

You may want to try installing from the ALTERNATE ISO. Which will do fine with your memory. But that will be a full installation. You seem to have enough disk space for that, just free up a partition.

---

### Post by Derek Chai on 2008-02-22
I got that SAME error!

---

### Post by andy100 on 2008-02-23
how can I ask to wubi to download alternate.iso version?

---

### Post by ago on 2008-02-23
Wubi does not work with the alternate ISO (yet). You have to either burn the CD or use netinstallation methods

---

### Post by Derek Chai on 2008-02-23
I get this thing too what should I do?

---

### Post by ago on 2008-02-23
How much memory do you have?

---

### Post by Derek Chai on 2008-02-23
4GB ram ddr2

I get almost the same error with 7.04 installation.

---

### Post by madmunkey on 2008-02-29
I've got this problem too, Running Windows Vista x86 and trying to install hardy-desktop-amd64.iso done a md5 and iso is good, I reboot and the GUI comes up and then reports the install has failed and installation-logs.zip has been saved in /ubuntu/ but its not there, if i push "f1" i can see a Buffer I/O Error on sda1 which is the drive with the iso file

Any Ideas?

---

### Post by ago on 2008-02-29
Can you please use Wubi 443 ([http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)) + latest daily ISO (delete any previous ISO and let wubi download one for you).

If there are problems please attach the logs (which should be under /ubuntu with 443).

---

### Post by madmunkey on 2008-02-29
Thanks its download the ISO now, will report back asap (going to take 15mins to redownload the iso)

---

### Post by madmunkey on 2008-02-29
Attached logs

---

### Post by madmunkey on 2008-02-29
Any ideas why its failing?

---

### Post by ago on 2008-03-01
same as here: [http://ubuntuforums.org/showthread.php?t=706358](http://ubuntuforums.org/showthread.php?t=706358)

---

### Post by madmunkey on 2008-03-01
That isnt the same problem im getting as mine boots to Gnome and then reports the failure to install.

---

### Post by madmunkey on 2008-03-01
Also just to update just tried v444 released today and adding the "--32bit" string to force the 32bit version to download.

---

### Post by samitharansara on 2008-03-02
Wubi gives me the same error..

---

### Post by joshuacollins on 2008-03-07
I've tried Wubi 8.04 on 3 of my computers, all failing.  :(

I've tried rev 440, 441, 444, and the latest one 449.    They all download and install to MBR/BCD okay, then when i reboot and choose Ubuntu it goes into the install script and fails at that point.

Ago, do you want to see logs?    2 of my computers have Vista, one has XP.    So far I haven't been able to use Wubi at all.   

Here are the 3 computers:

Desktop:
AMD64 X2 4200+
4gb DDR2 RAM
Windows Vista 32bit

Laptop1:
Dell inspiron 1300
2gb RAM
1.5ghz celeron M

Laptop2:
Dell XPS M170
2gb RAM
2.0ghz Pentium M

I guess I could try the Gutsy one, but I am itching to check out 8.04...  any suggestions to get it working?

Josh

---

### Post by ago on 2008-03-07
> **joshuacollins said:**
> I've tried Wubi 8.04 on 3 of my computers, all failing.  :(

I've tried rev 440, 441, 444, and the latest one 449.    They all download and install to MBR/BCD okay, then when i reboot and choose Ubuntu it goes into the install script and fails at that point.

Ago, do you want to see logs?

Yes please
No need to try 7.10

---

### Post by joshuacollins on 2008-03-07
which log exactly do you want to see?   there appears to be a whole bunch of them here!
thanks
josh

---

### Post by SpikeZ on 2008-03-08
I seem to be getting stuck when I select Ubuntu from the boot menu.  It gets as far as saying "Booting GRLDR ... "  then "... upper memory ... " and just sits there then.  I let it go for awhile but it seemed to be locked up then so I rebooted and uninstalled.
Any ideas on what is going wrong?

Thanks for the help, this looks like a great method for new users to get into Ubuntu (and Linux in general) once it gets hashed out a bit more.

---

### Post by some109 on 2008-03-08
I installed wubi 8.04, so I rebooted and chose "Ubuntu" from the menu. After the loading screen with the orange bar bouncing around, it just went into a dos-like screen, and I didn't know what to do.

---

### Post by joshuacollins on 2008-03-08
Hey Ago,

Also i should mention that on both of my Vista PC's...    after I've installed Wubi and reboot back into Vista the friggin entire system HANGS.   On both machines.    It boots up into Vista okay but as soon as I open a window or an application its just spinning its wheels.

Uninstalling WUBI and rebooting solves the issue.   Not quite sure what could be causing it?    Both of my vista OS have SP1 installed, one is a laptop one is a desktop.

:/

Like the other guy said its a really cool idea and I would love to use it.  Let me know what log you need me to post up here and I'll copy/paste ASAP.

:guitar:

Josh

---

### Post by joshuacollins on 2008-03-08
Update:    Installing WUBI directly off the alpha6 CD proved to work 100% fine.  

Thanks for your hard work Ago I appreciate it.
Josh

---

### Post by paulcross on 2008-03-08
I tried to install both ubuntu 710 and 804 with wubi,all failed.

The error message is similar.In english sort of like "no root directory"(I used the chinese version)

Back to wubi 704, the installing process is so smooth,but now..............

---

### Post by ago on 2008-03-09
Please make sure you are using the latest version of wubi 8.04. If you have errors i do need the logs and the exact error msg.

Windows logs are in %temp%

If the error is after reboot, the relevant logs are /caper.log and /var/log/syslog

---

### Post by some109 on 2008-03-09
i got wubi working, so I was on ubuntu for a while, then I turned off my computer.
when I came back, I got this error message when booting into ubuntu:

cannot locate file install/grub/menu.lst

Is the virtual disc corrupted? When I attempt to open the disks folder in the ubuntu folder, windows xp says "the directory is corrupted and unreadable".

should I reinstall?

---

### Post by ago on 2008-03-09
Try running chkdsk /r from windows

---

### Post by jjmurph on 2008-03-22
> **SpikeZ said:**
> I seem to be getting stuck when I select Ubuntu from the boot menu.  It gets as far as saying "Booting GRLDR ... "  then "... upper memory ... " and just sits there then.  I let it go for awhile but it seemed to be locked up then so I rebooted and uninstalled.
Any ideas on what is going wrong?

Thanks for the help, this looks like a great method for new users to get into Ubuntu (and Linux in general) once it gets hashed out a bit more.

I just wanted to add that I'm getting this same error.
I'm using the beta of 8.04 and rev 455 of wubi.

7.04 worked fine with wubi on the same hardware.

---

### Post by ago on 2008-03-22
> **jjmurph said:**
> I just wanted to add that I'm getting this same error.
I'm using the beta of 8.04 and rev 455 of wubi.

7.04 worked fine with wubi on the same hardware.

Press insert key rapidly as soon as you select ubuntu there should be more info.

---

### Post by majsalle on 2008-03-23
i'm also getting the "upper memory" message with 8.04.
 installing and running 7.04 went fine. but not 7.10 or 8.04. 
i've tried the many different revisions without luck.

---

### Post by jjmurph on 2008-03-25
> **ago said:**
> Press insert key rapidly as soon as you select ubuntu there should be more info.

I tried this and didn't get any other information.  It just says "...upper memory...".

I've installed ubuntu 8.04 the normal way (without wubi) so I'm all set but if there's anything else I can do to help you debug let me know.

---

