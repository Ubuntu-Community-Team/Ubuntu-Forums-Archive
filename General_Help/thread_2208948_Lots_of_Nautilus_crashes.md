---
title: "Lots of Nautilus crashes"
date: 2014-03-03
forum: General Help
---

### Post by Pedroski55 on 2014-03-03
I am getting a lot of crashes when I use Ubuntu 12.04 lately. When I browse my folders to open something, the window crashes, and all the icons on my desktop disappear. I can open it again, sometimes it is ok, other times it crashes again immediately. At some stage the desktop icons reappear. I always get a window, 'Ubuntu has experienced an internal error'. I tell it to report it. This has been going on for at least 3 weeks now. 

I always have the latest updates. Is there anything else I can do?

---

### Post by ibjsb4 on 2014-03-03
That popup is "apport"

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

What kernel are you running?

```
uname -a
```

I don't know what it will tell you (I do not have apport installed), but look in /var/log/apport.log for cause.  Also /var/log/dmesg may have some clues.

If this is only happening with nautilus then try opening it in terminal and look for errors.

```
nautilus
```

---

### Post by Pedroski55 on 2014-03-03
pedro@peterpu:~$ uname -a
Linux peterpu 3.5.0-46-generic #70~precise1-Ubuntu SMP Thu Jan 9 23:56:40 UTC 2014 i686 athlon i386 GNU/Linux
pedro@peterpu:~$ 

Well, I entered nautilus in a terminal, a window opened showing my folders. I randomly opened various folders from the window and in the bookmarks section on the left. Sure enough, the wiindow crashed and my desktop icons disappeared. But the terminal did not show any error message.

Now I reentered nautilus in a terminal. I got this message:

pedro@peterpu:~$ nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Segmentation fault (core dumped)
pedro@peterpu:~$ 

Can you tell me please, what does it want me to do?? As far as I know, Samba is a windows share program for accessing windows computers, something I don't do on this laptop.

I just checked. I do not have Samba installed.

---

### Post by ibjsb4 on 2014-03-03
> Samba is a windows share program for accessing windows computers, something I don't do on this laptop.                         

A good place to start by removing samba.

```
sudo apt-get remove samba
```

---

### Post by Pedroski55 on 2014-03-03
pedro@peterpu:~$ sudo apt-get remove samba
[sudo] password for pedro: 
Sorry, try again.
[sudo] password for pedro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not installed, so not removed
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
pedro@peterpu:~$

---

### Post by tgalati4 on 2014-03-03
This is not good.  Looking at the man page there is a --check switch, run that.  It should look like:

tgalati4@Mint14-Extensa ~ $ caja --check
running caja_self_check_file_utilities
running caja_self_check_file_operations
running caja_self_check_directory
running caja_self_check_file
running caja_self_check_icon_container
running caja_self_check_file_utilities
running caja_self_check_file_operations
running caja_self_check_directory
running caja_self_check_file
running caja_self_check_icon_container

*caja* is the MATE version of nautilus.

If that passes, then run nautilus with the --no-desktop switch and see if it loads.

---

### Post by Pedroski55 on 2014-03-03
pedro@peterpu:~$ nautilus -c
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
pedro@peterpu:~$ nautilus --version
GNOME nautilus 3.4.2
pedro@peterpu:~$

Maybe a hardware problem??

---

### Post by ibjsb4 on 2014-03-03
and ..

```
nautilus --no-desktop
```

Edit:  Maybe its samba4 you have installed.

```
sudo apt-get remove samba4
```

---

### Post by Pedroski55 on 2014-03-03
pedro@peterpu:~$ nautilus --no-desktop
pedro@peterpu:~$ sudo apt-get remove samba4
[sudo] password for pedro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
pedro@peterpu:~$ 

Hasn't crashed yet with --no-desktop, see what happens.

---

### Post by Pedroski55 on 2014-03-03
Nautilus crashed again!

Started it again from the terminal, same notification:

pedro@peterpu:~$ nautilus 
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Maybe this is some Chinese Hacker thing? I am in China.

---

### Post by ibjsb4 on 2014-03-03
Chinese Hacker??  There is a lot of hacking going on over there, but I think you are just broke.

Remove the ~/.config/nautilus file. and then ..

```
sudo apt-get remove --purge nautilus && sudo apt-get install nautilus
```

---

### Post by Pedroski55 on 2014-03-03
Thanks, I'll try that tonight gotta go to work now.

Haha, if it could ever be assessed, who hacks the most, would the America Govt. and their side kick Britain, or the Chinese Govt. win??

---

### Post by Pedroski55 on 2014-03-04
Ok, did that, let you know if it crashes again soon!

---

### Post by tgalati4 on 2014-03-04
If it crashes again, then it is time to check your RAM with memtest.  Run it for 30 complete cycles (it will take several hours) then examine the SMART parameters for your disk drive:

```
sudo smartctl -a /dev/sda
```

---

### Post by Pedroski55 on 2014-03-04
PANIC! I did as advised yesterday. This morning I can't log in. I get the log in screen, enter my password, but I it just returns to the log in screen again. Ran recovery mode and fsck, no problems seen. 

alt ctrl f2 gets me into a virtual screen. I tried startx, but I just get the message 'X is already running on terminal 1' 

Help!

I only just read the last post, so haven't done the mem test yet. Below some of the data from smartctl

[pedro@localhost ~]$ smartctl -a /dev/sda
smartctl 6.1 2013-03-16 r3800 [x86_64-linux-3.10.9-100.fc18.x86_64] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Smartctl open device: /dev/sda failed: Permission denied
[pedro@localhost ~]$ sudo smartctl -a /dev/sda
[sudo] password for pedro: 
smartctl 6.1 2013-03-16 r3800 [x86_64-linux-3.10.9-100.fc18.x86_64] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK3276GSXN
Serial Number:    218GD05BB
LU WWN Device Id: 5 000039 31ad01f50
Firmware Version: GB001M
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Mar  5 15:00:28 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  94) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

---

### Post by Pedroski55 on 2014-03-04
I am running on Fed 18 which I keep on another partition, just in case of such problems.

---

### Post by ibjsb4 on 2014-03-05
Well, I am running low on ideas :(

What I see happening is related to samba, but its not installed.  So maybe install and remove it.

```
sudo apt-get install samba && sudo apt-get remove --purge samba

```
Got any third party apps installed?

---

### Post by tgalati4 on 2014-03-05
If Fedora crashes, then there is a good chance there is a hardware issue.  Clean out the machine and reseat everything.

---

### Post by Pedroski55 on 2014-03-05
No, Fedora never crashes. It is just I like the 'look and feel' of Ubuntu, and it is a little easier for a non-geek like me.

I did a reinstall, couldn't think of any other way round the problem.

---

### Post by Pedroski55 on 2014-03-05
somehow doubled up the post. Thanks for your help.

---

