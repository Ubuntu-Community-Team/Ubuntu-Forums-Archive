---
title: "ubuntu won't reboot"
date: 2007-08-09
forum: General Help
---

### Post by gregoriotalahib on 2007-08-09
Hello great wubi creators,

I've successfully installed ubuntu using wubi on windows xp and its kicking as* with beryl. i didnt encounter any problems installing and dont have any performance problems as of this writing, its like any linux installed natively i've tried before etc. ubuntu, slackware, so on... on a separate partition. 

However, it won't reboot, it freezes after a blank screen after doing some daemon shutdowns and so on. i've waited for a couple of minutes, and its still w/o hd activities. But if u choose shutdown, it is shutting down successfully with no problems at all. Does anyone have the same problem? If so, please share your success stories. many thanks! ciao!

my pc specs: 1.8ghz yonah, 1gb ram, 120GB sata hd, intel 945gm.

its me gregorio

---

### Post by ago on 2007-08-09
What version did you use? Can you check that you have the files

/etc/init.d/fixsendsigs
/etc/rc2.d/S*fixsendsigs

---

### Post by gregoriotalahib on 2007-08-10
i used this version ubuntu-7.04-alternate-i386.iso on Wubi-7.04.04.exe.
i have this one -> /etc/init.d/fixsendsigs
but i dont have this file -> /etc/rc2.d/S*fixsendsigs :(

i think that's the problem...

---

### Post by ago on 2007-08-10
copy and paste the following into a terminal

sudo update-rc.d cpkernel start 01 0 6 .          
sudo update-rc.d fixsendsigs start 10 0 6 .     
sudo update-rc.d umounthost start 32 0 6 .    
sudo update-rc.d killntfs3g start 99 0 6 .

---

### Post by gregoriotalahib on 2007-08-18
thanks ago! its working! great! ;)

---

### Post by christopherm on 2008-09-04
I'm having a similar problem on Ubuntu 8.04. It simply won"t restart.

I do not seem to have any of these files:

/etc/init.d/fixsendsigs
/etc/rc2.d/S*fixsendsigs

And when i try to copy and paste the following into a terminal

sudo update-rc.d cpkernel start 01 0 6 . 
sudo update-rc.d fixsendsigs start 10 0 6 . 
sudo update-rc.d umounthost start 32 0 6 . 
sudo update-rc.d killntfs3g start 99 0 6 .

..I get:

update-rc.d: /etc/init.d/cpkernel: file does not exist

Please help..

---

### Post by ago on 2008-09-04
No those were commands for previous versions. Run the reboot command from a terminal (ctrl + alt + f2) and report any error you see.

---

### Post by tjflymonkey on 2008-09-04
I have the same problem! Please help
In my case, what I see from the screen was:

-------------------------------------------------
unmounting temporary filesystems....     OK
Deactivating swap....                    OK
Unmounting local filesystems....         OK
Will now restart 
-------------------------------------------------

It just hangs here.

---

### Post by ago on 2008-09-05
If you can see the msg "Will now restart" then all the reboot scripts should be ok. Might it be that you have acpi problems?

---

### Post by christopherm on 2008-09-05
> **ago said:**
> No those were commands for previous versions. Run the reboot command from a terminal (ctrl + alt + f2) and report any error you see.

When I do that, I just get a password prompt. Then when I do a ctr alt del the system goes down for reboot, successfully shuts down some daemons and I get several errors, first one being "libhal shutdown failed".

There are some more errors after that but the screen goes blank pretty quick so i didn"t catch them yet.

no reboot follows

---

### Post by ago on 2008-09-05
There might be reasons not related to wubi for your issues,

see for instance [http://ubuntuforums.org/showthread.php?t=603054](http://ubuntuforums.org/showthread.php?t=603054)

have a look in the general forum, in general if you see the msg "Will now restart", it means things are ok on the wubi side

---

### Post by busta5000 on 2008-09-05
Dear Ago I have a problem with ubuntu I hope u can help me read my thread please reply & help me for no one did reply
[URL="http://ubuntuforums.org/showthread.php?t=909572"]
http://ubuntuforums.org/showthread.php?t=909572[/URL]

---

### Post by christopherm on 2008-09-06
How exactly do I apply the "reboot=b" solution?

---

### Post by christopherm on 2008-09-07
this has been going on since 2004?

[http://ubuntuforums.org/showthread.php?t=5193](http://ubuntuforums.org/showthread.php?t=5193)

---

### Post by tjflymonkey on 2008-09-08
My understand is that if I add "reboot=b" then reboot will pass to Bios to do it. That means it will be independent with the operating system. Sounds like it should work, but it doesn't work for me?

---

### Post by gorilla55 on 2009-01-12
I had the problem on a Dell Optiplex 330.  

By adding reboot=b to the end of the kernel line in the boot loader config file (/boot/grub/menu.lst for grub) solved the reboot problem.

---

### Post by MegaSvensk on 2009-12-18
Hi,

Sorry for bumping an old thread but I have this exact same problem in Ubuntu 9.10 (and Linux Mint, which I understand is just Ubuntu with new eye candy.) And I was just wondering if the commands stated in the thread are still valid? Also, I can't even reboot from the live cds, so maybe my problem is something else. It goes down for reboot and then the screen goes blank and the screen led starts blinking as if there is no signal or in standby and all I can do is press the power button.

Edit

Changing an ACPI BIOS setting seems to have fixed the problem! I have no idea what I changed though. I set ACPI Standby state from S1 (POS) (piece of **** mode? :p) to S3 (STR).

---

