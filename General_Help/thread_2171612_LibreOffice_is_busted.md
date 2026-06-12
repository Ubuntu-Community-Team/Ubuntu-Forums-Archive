---
title: "LibreOffice is busted"
date: 2013-08-31
forum: General Help
---

### Post by ruberad on 2013-08-31
Hey all,

I'm working with Ubuntu 12.04, (re)installed maybe a month or two ago, LibreOffice stopped working (in particular, both Calc and Writer). It won't open files that it previously opened, it won't even start. For instance from xterm, 'soffice' shows the splashscreen then dies 'Bus error (core dumped)'.

I tried uninstalling with Software Center, didn't work: error from the Details window is:

dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libmagic1': Input/output error
Error in function: 

(then it didn't give a function, the erorr message just stopped there)

I tried also from commandline:
sudo apt-get remove --purge libreoffice*

It lists a bunch of stuff, asks for confirmation [Y|n], I give it Y, it lists a bunch more stuff, and then ends with the same error.

Just for yux, I tried to sudo apt-get remove libmagic1, but the list of things it would remove seemed way too scary (ubuntu-desktop? ubuntu-standard? I think I need those)

I'm not seeing it anymore, but one of those tries was giving a slightly helpful error message saying I needed to run `sudo dpkg --configure -a`, and I tried it, but it didn't help.

What's going on here? (a) why did LibreOffice suddenly stop working? (b) I don't really care, what can I do to get them back, or at least get something in their place?

If there is any diagnostic command I can run and report here, please let me know...

thx in advance!

---

### Post by bkline on 2013-08-31
It's not hard to find reports of problems installing LibreOffice under 12.04:

[http://askubuntu.com/questions/183507/cannot-install-libreoffice](http://askubuntu.com/questions/183507/cannot-install-libreoffice)
[http://ubuntuforums.org/showthread.php?t=1974285](http://ubuntuforums.org/showthread.php?t=1974285)
[http://ubuntuforums.org/showthread.php?t=2157478](http://ubuntuforums.org/showthread.php?t=2157478)
[http://askubuntu.com/questions/137933/broken-packages-synaptic-and-libre-office-broken-when-upgrading-to-12-04](http://askubuntu.com/questions/137933/broken-packages-synaptic-and-libre-office-broken-when-upgrading-to-12-04)

---

### Post by ajgreeny on 2013-08-31
Which version of LO are you using?  I run xubuntu 12.04.3 and have LO from the ppa giving me version 4.? (I can't remember exactly and I am not on that machine at the moment) and that works faultlessly for me.  I do not remember what comes with 12.04 by default, but the ppa could be worth a try.

---

### Post by tgalati4 on 2013-08-31
Sounds like you have a disk problem.  What is the SMART status of the disk drive?  The fact that it was working and now not working and you are getting core dumps makes me suspect a hardware issue.  Why did you have to reinstall 12.04?

---

### Post by ruberad on 2013-08-31
> **bkline said:**
> It's not hard to find reports of problems installing LibreOffice under 12.04:

[http://askubuntu.com/questions/183507/cannot-install-libreoffice](http://askubuntu.com/questions/183507/cannot-install-libreoffice)
[http://ubuntuforums.org/showthread.php?t=1974285](http://ubuntuforums.org/showthread.php?t=1974285)
[http://ubuntuforums.org/showthread.php?t=2157478](http://ubuntuforums.org/showthread.php?t=2157478)
[http://askubuntu.com/questions/137933/broken-packages-synaptic-and-libre-office-broken-when-upgrading-to-12-04](http://askubuntu.com/questions/137933/broken-packages-synaptic-and-libre-office-broken-when-upgrading-to-12-04)
I had looked a few of those before, but they didn't seem to quite match my situation because they're all about unmet dependencies. Mine was installed, stopped working, so I wanted to uninstall/reinstall, but I can't even uninstall.

---

### Post by ruberad on 2013-08-31
> **ajgreeny said:**
> Which version of LO are you using?  I run xubuntu 12.04.3 and have LO from the ppa giving me version 4.? (I can't remember exactly and I am not on that machine at the moment) and that works faultlessly for me.  I do not remember what comes with 12.04 by default, but the ppa could be worth a try.

What's "from the ppa"? I can't tell what version because I can't start it up. Unless there's some kind of apt-* command that will say what version of something I (supposedly) have installed.

---

### Post by ruberad on 2013-08-31
> **tgalati4 said:**
> Sounds like you have a disk problem.  What is the SMART status of the disk drive?  The fact that it was working and now not working and you are getting core dumps makes me suspect a hardware issue.  Why did you have to reinstall 12.04?
That's scary! I had to reinstall because I had my 64GB Crucial v4 SSD die on me, and I reinstalled on the (refurbished) replacement they sent. The replacement had the latest firmware update already, and I immediately turned on TRIM, as soon as 12.04 was on.

Other hints in this direction:

I have been having trouble with Chromium on startup "can't [read?access?] profile", I was able to rm -rf .config/chromium/ and it was better, but it's acting up again. (when I start it up, it puts a separate chromium icon in the sidebar, not the original one I launched with)

Also maybe not related, but a few days ago no browser could get to any page, but I think that was a network issue, as it was solved by power-cycling the router, and clearing all cache/histories (except normal cache clear for Chromium didn't work, rm -rf .config/chromium did it)

I opened disk utility, and it said SMART status green, I opened up the details, everything was either green or N/A. I kicked off a self-test while I typed this, it didn't pop up a window or anything, maybe it just refreshes the smart statuses? Still everything either Good (green) or N/A (greyed out)

---

### Post by ruberad on 2013-08-31
Also, don't know if it could possibly matter, but yesterday I plugged in for the first time a laserjet 2300, and made it the default printer.

---

### Post by tgalati4 on 2013-08-31
A bad profile in Chromium means that it couldn't read your cache files (pointing to a disk problem).  Why don't you post the SMART data?

Open a terminal:

```
sudo smartctl -a /dev/sda
```

A refurbished disk is a sign that something is amiss.

Check for errors:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Post any disk-related errors.

---

### Post by ruberad on 2013-08-31
> **tgalati4 said:**
> A bad profile in Chromium means that it couldn't read your cache files (pointing to a disk problem).  Why don't you post the SMART data?
Thx so much for suggestions; I tried that, turns out I don't have smartctl installed, I googled to find it is part of smartmontools, and it looks like I've gotten myself into a state where I can't install anything:



> sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  heirloom-mailx
Suggested packages:
  exim4 mail-transport-agent gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  heirloom-mailx smartmontools
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 694 kB of archives.
After this operation, 1,864 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe heirloom-mailx i386 12.5-1build1 [238 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main smartmontools i386 5.41+svn3365-1 [455 kB]
Fetched 694 kB in 4s (158 kB/s)         
Selecting previously unselected package heirloom-mailx.
(Reading database ... 75%[COLOR="#FF0000"]dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libmagic1': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]

Also, I looked through dmesg and found a whole bunch of 'unhandled sense code' errors like this (and more):

[   63.165900] sd 0:0:0:0: [sda] Unhandled sense code
[   63.165914] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   63.165918] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[   63.165945] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[   63.165951] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 cd fe d8 00 00 08 00
[   63.165963] end_request: I/O error, dev sda, sector 13500120
[   64.539942] sd 0:0:0:0: [sda] Unhandled sense code
[   64.539945] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   64.539949] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[   64.539976] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[   64.539983] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 cd fe d8 00 00 08 00
[   64.539995] end_request: I/O error, dev sda, sector 13500120
[   96.395063] sd 0:0:0:0: [sda] Unhandled sense code
[   96.395065] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   96.395070] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]

---

### Post by ruberad on 2013-09-02
Another test, I guess more conclusive:

I did 'dmesg | grep sda' and took note of the last timestamp, and then kicked off 'soffice' (bus error) and did it again, these are the new errors:

[151022.480224] sd 0:0:0:0: [sda] Unhandled sense code
[151022.480228] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[151022.480233] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[151022.480267] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[151022.480276] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 1c f7 10 00 00 08 00
[151022.480306] end_request: I/O error, dev sda, sector 1898256
[151026.314900] sd 0:0:0:0: [sda] Unhandled sense code
[151026.314905] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[151026.314912] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[151026.314956] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[151026.314967] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 cd ff 50 00 00 08 00
[151026.314987] end_request: I/O error, dev sda, sector 13500240
[151036.848535] sd 0:0:0:0: [sda] Unhandled sense code
[151036.848540] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[151036.848547] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[151036.848591] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[151036.848602] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 cd ff 58 00 00 08 00
[151036.848621] end_request: I/O error, dev sda, sector 13500248

Conclusive that soffice and disk errors reported by dmesg are related, but what does it mean? Do I need to send these errors to crucial and see if they'll send me another replacement (refurbished) ssd? Will they just tell me to reformat and reinstall? Can this be repaired in situ?

---

### Post by ruberad on 2013-09-03
OK, I don't think this is a good sign.

I did 'sudo touch /forcefsck' and rebooted, it said it found errors so I did 'F' for fix, when it finished booting and I logged in, my (12.04 default) wallpaper is corrupt. Browsers still work (here I am), xterm still works, soffice still bus errors, leaving the same kind of dmesg errors.

---

