---
title: "Dual Boot machine won't shutdown but will restart (Windows 8.1 AND Ubuntu 14.04)"
date: 2014-06-08
forum: General Help
---

### Post by RookY2K on 2014-06-08
Hello everyone,

I am racking my brain trying to figure out what's going on and I cannot figure it out. When I shutdown, in Windows 8.1 or Ubuntu 14.04, my computer will not finish the power down process. The system will halt, but it will not finish powering down. On windows, the screen will actually shutdown, but some of the LED's will stay lit. In Ubuntu, the screen won't even shut off. If I have "quiet splash" enabled in the LINUX_GRUB_COMMAND_LINE, then it will simply hang when 4 of the 5 dots are filled in. If "quiet splash" is disabled, it gets all the way to the entry "<some number string> reboot: system power down", or something like that, and then just hangs. I've tried any number of things including:

1) Changing the LINUX_GRUB_COMMAND_LINE variable (before I realized that my Window's partition was having an issue too).
2) Turning off my WIFI adaptor
3) Updating any number of drivers
4) Returning my BIOS settings to default
5) Reformatting and reinstalling Windows.
6) And a few other minor things
 
Nothing has worked (obviously since I'm posting here). Any help tracking down the potential issue would be a huge help.  Thank you!

---

### Post by RookY2K on 2014-06-08
Hi again, 

A piece of information I forgot to mention in my first post: this all started when I tried to boot into Windows and I got a stop error. I can't remember the exact error code, but the message was that ACPI.sys was missing or corrupt. I ran Windows recovery tools and used the utility to fix boot issues. I'm fairly certain that is when the issues started. 

Any help at all would be very appreciated. I realize you might not know exactly what my issue is, so even just helping me track it down would be extremely helpful. I need to narrow down the problem set because searching for possible solutions isn't getting me anything specific enough. Thank you!

---

### Post by oldfred on 2014-06-08
That is was showing UUID for partition, I thought it might be a drive issue. What is drive configuration in UEFI/BIOS? AHCI or something else?

But ACPI is power related and can be just about anything. Historically lots of issues with ACPI and various hardware and software and what actually works. Do not know much more than that can be a real can of worms. 

What system? And is UEFI/BIOS the most current version?

The only related issue I have saved was this, you can experiment with a boot setting in grub with e for edit and scroll to linux line and next to quiet splash add settings;
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off and nomodeset
pci=nomsi  or  ACPI=Off

Some laptops needed this:
 Some other boot options
acpi_osi=Linux  acpi_backlight=vendor

---

### Post by RookY2K on 2014-06-08
Thank you for the reply, here's the answers to your questions:

> **oldfred said:**
> That is was showing UUID for partition, I thought it might be a drive issue. What is drive configuration in UEFI/BIOS? AHCI or something else?

ACHI

> What system? And is UEFI/BIOS the most current version?

I've included a screen grab of my system information, so hopefully that will be helpful.




> The only related issue I have saved was this, you can experiment with a boot setting in grub with e for edit and scroll to linux line and next to quiet splash add settings;
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off and nomodeset
pci=nomsi  or  ACPI=Off

Some laptops needed this:
 Some other boot options
acpi_osi=Linux  acpi_backlight=vendor

I'll try these, but I'm thinking it has to be something that is shared between Ubuntu and Windows since it affects both OS's. Also, I'm not afraid of trying a nuclear option like reformatting everything and re-installing my OS's... but I'm not familiar with how to set up a boot partition or load a UEFI or anything like that, so I'd need to be directed to some instructions or a tutorial. Also, I don't want to go through all that if I'm just going to end up with the same issue, which is why I'm trying to track down what it is and where the problem is located.  Thanks again for your help.

---

### Post by oldfred on 2014-06-08
It says you have UEFI and systems pre-installed with Windows 8 are always UEFI.

Asus laptops sometimes do need added settings. And some seem to have power issues.

        Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by ytiani99007 on 2015-02-19
Hi,

I was working with my machine model X553MA which came with win8.1 and I have install ubuntu 14.04 with originally the same problem which now is solved
I think this may work on some of the cases I saw here....
Hope this help:

Freezes happen upon booting and shut down from ubuntu 14.04
but I can boot in and out of windows without any problem

So I started to suspect BIOS is asking the OS a question (i.e. fast start up or something similar) where Windows 8.1 knows how to answer, but Ubuntu 14.04 has no idea what that is (thus, the freeze)

I have tried turning off secure boot/fast boot in BIOS and also turned off hybernation within Windows 8.1, the problem was still there.

I started digging into the BIOS and found an option 'OS selection' under 'Advanced'
and there are two options: 'windows 8.x' or 'windows 7'
and the default selection was 'windows 8.x'

my immediate question was:
So this BIOS is only going to recognize win8.x or win7?
what if I want to install other OS?
isn't there suppose to be an option of 'ANY OTHER OS', at least?

So I made the decision to try changing this option to 'windows 7'
[ATTACH=CONFIG]260094[/ATTACH]

And the result is probably what you can imagine. I am now booting Ubuntu 14.04 faster than any FAST/SECURE/HYBERNATE boot crap.
I can still use grub to boot into Windows 8.1 (and you know what, not really that slow compared to FAST BOOT)

I am really disappointed by the two things done by ASUS here:

1) creating an obstacle here for no reason but to cripple any other OS other than Windows 8.1 
(you might argue that is an ADVANCED option to facilitate any OS that support HYBERNATION, but that should be designed so that IF the OS support hybernation, it goes to hybernation, and if not IT SHOUDN'T INTERUPT normal starup/shutdown)

2) Calling the other option "Windows 7"
That is a misleading name.
Because what it actually is, is 'Any other OS'.
And I suspect the wording of that is created solely on the purpose of troubling users of other OS.
This is a nasty dirty tactics.

I wonder if that happens in brands other than ASUS.
WATCH OUT!!

---

