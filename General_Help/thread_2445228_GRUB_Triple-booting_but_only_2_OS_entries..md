---
title: "GRUB: Triple-booting but only 2 OS entries."
date: 2020-06-10
forum: General Help
---

### Post by abdullahtrees on 2020-06-10
Hello everyone!

I am using a decapitated laptop(HP Envy m6-1105dx) as a retro-station for playing oldschool games while maintaining high productivity sessions. 

**Currently I am triple-booting Windows XP + Windows 8.1 + Ubuntu 18.04 **(installed in respective order), and **my system is working** quite all right. **No problems/errors whatsoever.**

There is just one thing I want to **improve.** I like the GRUB Bootloader and I think it's very cool and looks awesome, and so would like to use it as my only bootloader. The problem is...

When I turn on my PC this is the first thing I see:
[IMG]https://i.postimg.cc/g26WZwmK/20200611-060619-1.jpg[/IMG]

And if I want to boot Windows XP, I have to select Windows 8 first, wait for about 20-30 seconds for its graphical bootloader to load, and then I get:
[IMG]https://i.postimg.cc/436RWrK7/20200611-060728.jpg[/IMG]

(yeah I know, I could just do bcdedit from cmd.exe from Windows 8 to use the non-GUI bootloader to skip the loading time for the graphical bootloader: but that is erratic(graphical bootloader ends up coming anyway), and I've done it twice already and yet this stupid graphical one appears after I boot up and shutdown Windows 8.1, so now I'm placing my hopes on Ubuntu and GRUB to manage booting all OS'es)


**However I'd like the current GRUB menu to look more like this **

[TABLE="width: 250"]
[TR]
[TD]GNU GRUB    version 2.02[/TD]
[/TR]
[TR]
[TD]---------------------[/TD]
[/TR]
[TR]
[TD]Ubuntu 18.04
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)[/TD]
[/TR]
[TR]
[TD]Windows 8.1 (on /dev/sda1)[/TD]
[/TR]
[TR]
[TD]Windows XP Professional (on /dev/sda2)[/TD]
[/TR]
[/TABLE]

I tried using ```
os-prober
``` and ```
grub-repair
```, but they don't change anything, as the only bootloader they can find is the Windows 8 one, and thus do not make Windows XP accessible from GRUB.

So I guess I have **two goals**: [B]1) Make Windows XP appear on the list of OS's in GRUB menu. 2) Change the name of the listings in GRUB menu.
[/B]I'd also like to note here that **I am **completely **new to Linux and Ubuntu**. In fact, this is how I'm trying to learn and adapt to this new environment and fulfill my goals and work requirements. I hope I have successfully managed to describe my problem and hope there are a few kind Linux power users out there who can help me out on the usage of GRUB. 
Thanks in advance :)

---

### Post by oldfred on 2020-06-10
I am assuming both are BIOS installs on MBR partitioned drives.
Are both Windows installs in primary NTFS partitions? Then it can be done.

You need to separate boot files, usually by moving boot flag & running that versions repairs. Or maybe moving the boot files. 
Windows normally has only one primary NTFS partition with boot flag. Newer install overwrites old installs boot files & adds it to BCD to be able to boot both.
Windows has to have boot flag, but grub only looks for the Windows boot files, so that is why if boot files are spit it will work.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by abdullahtrees on 2020-06-11
> **oldfred said:**
> I am assuming both are BIOS installs on MBR partitioned drives.
Are both Windows installs in primary NTFS partitions? Then it can be done.

Yes! They are, whew... Even though I thought that my first post was quite informative, I somehow ended up missing out on critical information, and for that I apologize. Please check these images, but I think I can safely deduce that Windows XP and Windows 8 are both installed on Primary partitions.

[IMG]https://i.postimg.cc/YCJVw01v/20200611-201418-1.jpg[/IMG]

[IMG]https://i.postimg.cc/bNVW33rH/20200611-202241-1.jpg[/IMG]


> **oldfred said:**
> You need to separate boot files, usually by moving boot flag & running that versions repairs. Or maybe moving the boot files. 
Windows normally has only one primary NTFS partition with boot flag. Newer install overwrites old installs boot files & adds it to BCD to be able to boot both.
Windows has to have boot flag, but grub only looks for the Windows boot files, so that is why if boot files are spit it will work.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Thank you, it was a very big, but very informative read. I removed the 'boot' flag from the Windows 8.1 partition using GParted GUI, and then tried running Windows XP Setup Repair through the ISO, but it didn't do much, basically nothing on my system changed, I can still somehow boot from both Windows 8.1+Windows XP even though the 'boot' flag is gone. It's not exactly clear what you meant by 'seperating boot files' and 'moving boot files' (do you mean copying all the files on that partition and then deleting it? 

I want to make one thing clear here. Installing Windows XP on this machine was a very difficult endeavour for me, as it is technically on non-supported hardware, and so it requires hours of driver installation and playtesting to ensure that an XP reinstallation is complete. I already had to reinstall XP and Windows 8.1 twice, so **I really hope to get them to appear on GRUB without having to reinstall XP or 8.1**. If the matter is simple, like making an image of the partition and then restoring it, then I might be able to pull it off, but to have to reinstall XP for the third time... I'd rather live with the current situation of having to wait 40 extra seconds to boot XP.

> **oldfred said:**
> Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe


Uhm, this section did not make sense to me. Can you please explain what you are talking about here? What do I do with these files in order to get GRUB working?

---

### Post by oldfred on 2020-06-11
Please attach screen shots. Not everyone has high speed Internet even though forum tries to reduce screen sizes. You can use forum's advanced editor & paperclip icon to attach screen shots.

That is a list of the essential Windows boot files for XP which uses ntldr and for newer Windows in BIOS mode which used bootmgr.

If youcopy the three files into each install, grub will probably find them. For a Windows boot loader or repairs on any Windows bootable partition you must have the boot flag on that partition. But can move boot flag and repair another one.

With older XP, the boot.ini would have additional XP or other Windows installs.
With newer Windows the boot entries are added into the BCD, which requires Windows tools to edit.
Not sure if any more than three files shown are needed for Windows, but those are the files grub will look for.

---

### Post by dragonfly41 on 2020-06-12
I have multiple boot configuration - but using rEFInd instead of standard loader.
My setup is one Windows OS and multiple Ubuntu OS.
I have never tried booting from multiple Windows but searching around to see if rEFInd can cope with this [I found this thread]("https://superuser.com/questions/1513082/installing-refind-on-dual-boot-windows-10-machine").

One spinoff from using rEFInd is that OP can install custom theme.

Note the fine detail in the above thread .. you need a separate EFI partition for each OS.

*"[COLOR=#242729][FONT=Arial]One way to do this is to have 2 EFI partitions."[/FONT][/COLOR]*

---

### Post by oldfred on 2020-06-12
I do not think rEFInd works on BIOS only systems. 
It uses UEFI boot and was originally developed for Macs when they converted to EFI long before Windows converted to UEFI in 2012 as its standard.
It may be able with UEFI to do a one time UEFI reboot into a BIOS install.

I use rEFInd for my emergency boot flash drives.

I think you do have to have two FAT32 partitions if booting two UEFI Windows installs, again to have boot files in separate partitions, so grub can find them. But only one can be flagged as bootable or the ESP, but I think grub still finds the boot files in other FAT32 partition.

---

### Post by dragonfly41 on 2020-06-12
That is true.

[https://www.rodsbooks.com/refind/bootmode.html](https://www.rodsbooks.com/refind/bootmode.html)

*[COLOR=#000000][FONT=&quot]"rEFInd is useful only on EFI-based computers, not older BIOS-based computers"[/FONT][/COLOR]*

---

### Post by abdullahtrees on 2020-06-17
Sorry for being inactive for so long, but thanks to the combined efforts of your help and an extremely helpful 'SamiCrusader' on The-Eye Discord, I was able to figure out a harmless solution to multibooting from GRUB without making major changes to the system, (and which is also reversible, just in case I want to return to my previous bootloader setup). I consider it a great success and am sharing it with you guys just in case anyone with a multiboot setup with XP might need it in the future. I hope this thread will be of benefit to anyone you might find in the future who uses XP and multiboot.


**A working procedure on multibooting Windows XP + Windows 8.1/10 from GRUB (that hopefully works for everyone)**
 [TABLE="width: 800"]
[TR]
[TD]================================================================================================
**Step 1: **_Check whether critical XP Boot files are present on the drive where XP is installed. _
The XP Boot files are 'NTDETECT.COM', 'ntldr' and (probably) 'boot.ini'
If they are skip to Step 3. If they are not...[/TD]
[/TR]
[TR]
[TD]**Step 2:** Go to the Linux Distro, _run 'GParted'/'GParted-GUI' to remove the 'boot' flag from the partition_ 
(in my case the boot flag was on the XP partition(/dev/sda1), even though the bootmgr(Windows 8) bootloader was on another partition(/dev/sda2)[/TD]
[/TR]
[TR]
[TD]**Step 3: **After the boot flag has been removed, _run Windows XP Setup_ as you normally would, but you do not need to reinstall!! (yay) Just allow the Setup to detect any existing Windows XP installations, _and then choose 'Repair'_. After this phase is done, the _critical XP Boot files should now be at the root of the drive where XP is installed_. This means we can now...[/TD]
[/TR]
[TR]
[TD]**Step 4: **_Test out the custom Windows XP boot-up sequence._ For a Linux noob like me who checked out GRUB by trying to press 'e' and 'c' at the OS selection screen, I initially thought GRUB was a mystical realm of low-level code, that ordinary people would have no chance trying to understand and use, where only assembly code, 'insmod' and nonsensical strings like '4e63fa-09df-dd23-234e91a0' governed the system. The commands from pressing 'tab' in command-line were quite detached from my Windows-habituated brain, and the help documentation in cmd-line barely made any sense (some commands didn't even have help! Like 'recordfail' or 'insmod gzio')

Thanks to a random Linux power user on the internet called Sami, I came to think a bit better of GRUB: [I]GRUB is basically a Linux-based command-prompt shell that selects a bunch of scripts inside grub.cfg. When an OS on the list is selected, it performs a bunch of primitive commands that allows it to just hand-off control to the host OS necessary.
[/I]
Anyways, that was a lot of small-talk. Press 'c' and start typing the following. Press enter after every line, those are 5 seperate commands and they need to be typed in succession. Huge thanks to Sami for coming up with this simple script!

```
insmod part_msdos
  insmod ntfs
  search -s root -f /NTDETECT.COM
  ntldr /ntldr
  boot

```

If all goes well, you should now boot immediately into Windows XP![/TD]
[/TR]
[TR]
[TD]**Step 5:** After you are done testing with Windows XP and are sure the script works on your system, _you might want to permanently add Windows XP boot sequence to GRUB menu._ This can be very easily done with a tool called 'grub-customizer'. 

Install it if you already do not have it with "sudo apt-get install grub-customizer", then _open the GUI app_, and on the top bar select _'Edit' --> 'New'_, which _opens the Entry editor_, and then [U]select 'Other' in the 'Type' drop-down menu. Then type out the following. 
[/U]
```
menuentry 'Windows XP'
   insmod part_msdos
   insmod ntfs
   search -s root -f /NTDETECT.COM
   ntldr /ntldr
   boot

```

This is no more different from the commands that were used in Step 4, so if those worked then, then this should work just as well. Ensure there are no typos, and then click on 'OK'. At this point feel free to customize GRUB however you want but with an air of caution, for example, selecting the default OS, or removing the countdown allowing you to take your time when you select OS's, or changing the name of the OS's in the list, etc.[/TD]
[/TR]
[TR]
[TD]**Step 6: **_Cleanup._ At this point, we can now select to boot into 
   - Ubuntu
   - Windows XP (direct)
   - Windows 8/10 Bootloader (or some other OS that you may have)

*Adding this seperate script for Windows XP has in no way prevented Windows XP from being bootable by the Windows 8/10 Bootloader*! This is why I called it a reversible modification, because at any time you can remove the Windows XP bootup sequence from your "grub.cfg" file, and all should be back the way it was. But _if you want to boot only Windows 8/10 from the Windows Bootloader(bootmgr) to make booting to Windows 8/10 a bit faster_, then all you have to do is....

a) Select the Windows 8/10 Bootloader to _boot into Windows 8/10_, and then _open an administrator command prompt_. This can be done by either opening Task Manager first and then going to the top bar and then selecting 'Run New Task' (be sure to click on the check box with "Create this task with administrative privileges", or you can simply open the Start Menu, locate 'Command Prompt', and then right-click selecting 'Run as Administrator'. Either one, once you have an administrator command prompt open...

b) _Type in "bcdedit"_ and something like this should return...
```

Windows Boot Manager
-------------------------------------------
**identifier    {bootmgr}**
device    partition=\Device\HarddiskVolume1
description    Windows Boot Manager
locale    en-US
inherit    {globalsettings}
integrityservices    {Enable}
default    {current}
resumeobject    #unique hexadecimal string
displayorder    {ntldr}
           {current}
toolsdisplayorder    {memdiag}
timeout    0

Windows Legacy OS Loader
----------------------------------------------
**identifier    {ntldr}**
device    partition=\Device\HarddiskVolume1
path    \ntldr
description    Windows XP

Windows Boot Loader
-----------------------------------
**identifier    {current}**
device    partition=C:
path    \Windows\system32\winload.exe
description    Windows 8.1
locale    en-US
inherit    {bootloadersettings}
recoverysequence    #unique hexadecimal string
integrityservices    Enable
recoveryenabled    Yes
osdevice    partition=C:
systemroot    \Windows
resumeobject    #unique hexadecimal string
nx    OptIn
bootmenupolicy    Legacy


```

Your output might look a little bit different or very different depending on your initial conditions, but all that mostly matters is the **identifier part **for the entries in the Windows Boot Manager. You don't want to do something as major as deleting XP from this list of bootable OS's, that's not necessary(and risky/permanent as well). Instead you can make it as if XP is not in this list at all, by simply setting Windows 8/10 as the default Operating System in the BCD(Boot Configuration Data). 

This command will set Windows 8/10 as the default Operating system for Windows Boot Manager, _replace the {identifier} portion with the identifier part from the information you got above for Windows 8/10. _
```
bcdedit /default {identifier}
```

And this command will remove the time-out period that gives you time to choose between Operating Systems in Windows Boot Manager, making it boot immediately into the default Operating System/
```
bcdedit /timeout 0
```

And we are done! Now selecting 'Windows 8/10' from the GRUB menu will immediately cause you to load Windows 8/10!
======================================================================================================[/TD]
[/TR]
[/TABLE]



Whew! That was quite the long post, I am sorry if it is too long for anyone, but as a token of success I'd like to post one last image if it doesn't offend oldfred (sorry for taking images with my camera, as many of the pictures I take involve boot-time procedures, where screenshots don't work.)

Special Thanks to @oldfred for giving me insight on the importance of the "boot" flag and why it needs to be removed, and Sami/Samicrusader for the Windows XP boot sequence script! Thank you guys so much, my problem here is **solved**!

---

