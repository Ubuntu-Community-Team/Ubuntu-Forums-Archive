---
title: "Windows overrides my boot menu - No menu present and cannot load Ubuntu"
date: 2020-05-15
forum: General Help
---

### Post by robert71 on 2020-05-15
I installed Ubuntu recently and everything was looking fine until windows updated. 

After the update I am unable to boot into my Ubuntu and my boot menu is gone. 
I can manually boot into windows by selecting it in the BIOS Override (feature on Ax370 Boards). 

I used boot repair and everything goes back to normal until i load windows it messes with the configuration somehow and im left with the same problem. 

Ive tried : 

1. Boot Repair
2. Recommendations from this thread [https://askubuntu.com/questions/838780/windows-10-changes-uefi-boot-order-every-time](https://askubuntu.com/questions/838780/windows-10-changes-uefi-boot-order-every-time)

Among many others types of fixes but none seems to work. 

Here is the Boot repair link for my config:

[http://paste.ubuntu.com/p/7WSF67JqxY/](http://paste.ubuntu.com/p/7WSF67JqxY/)

Can anyone assist me in restoring my setup and stop windows I would be most grateful, 

thanks

---

### Post by CelticWarrior on 2020-05-15
Windows feature updates tend to do that, for your convenience (!), because such updates require many reboots.
Just open UEFI settings > Boot menu (or equivalent) and change it back to "Ubuntu". That should be all.

---

### Post by robert71 on 2020-05-15
Ive tried that many times, unfortunately Ubuntu seems to be missing and only the disk is present. 

If i set the disk nothing comes up.

---

### Post by CelticWarrior on 2020-05-15
You need to look better because it's there. Or you may try the EasyUEFI tool in Windows as mentioned in the Q&A you linked.

---

### Post by dragonfly41 on 2020-05-15
If you look at line 877 in your pastebin report there is reference to efibootmgr.

You can test that in your terminal.

[FONT=monospace][COLOR=#000000]efibootmgr -v

Ubuntu is right at then end of the list.

You can change boot order through efibootmgr.

I also have the added benefit of rEFInd installed.
[/COLOR]
[/FONT]

---

### Post by oldfred on 2020-05-15
You also show grub installed to MBR, so must make sure system is booting in UEFI boot mode.
And you show Windows is hibernated, or fast start up is on. You need to turn that off.
You were set in UEFI to boot SSD, which probably was a BIOS boot. The re-install of grub that Boot-Repair did reset to make Ubuntu first in UEFI boot order.  Grub uses efibootmgr to change boot order. 
Line 1646 shows change of boot order.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by robert71 on 2020-05-15
[COLOR=#000000](And you show Windows is hibernated, or fast start up is on. You need to turn that off.)

I Did, im not sure why it is showing up as off, probably updates as you mentioned. 

So heres what happened, apparently windows Hides the Ubuntu entries and it does not show up in my Bootloader (see attached). 

The blank space is actually the Ubuntu Grub2, if i hit enter to load it it loads grub2 and all the entries. :) 

So to remedy the situation i have disabled all boot devices in my BIOS(UEFI) and so now it loads the correct boot loader upon startup. 


There is an issue though i would like to get fixed or find the root cause: 

 To fix the original issue of the Grub Bootloader not being brought up to select a device to boot from I:

1. Reinstalled Ubuntu - which only lists the grub loader as long as i dont load windows
2. Used boot repair - same as above as long as i dont load windows 
3. Tried pointing the windows entry to use my Grub loader using - [/COLOR]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
    This never worked, says command completed successfully when running cmd as admin but the entries never changed i Know this because of:
4. Used EasyUEFI to check the Boot order in windows and verify Boot Entry Information 

```


Description:Windows Boot ManagerGPT partition GUID:{75423061-9F85-4995-8404-8B64AD302813}
Partition number:2
Partition starting sector:1085440
Partition ending sector:1290239
File path:\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI


```

5. Tried 

```
bcdedit /enum {fwbootmgr} 

Firmware Boot Manager
---------------------
identifier              {fwbootmgr}
displayorder            {e8b12970-901a-11ea-8e62-806e6f6e6963}
                        {2e2d35b6-9624-11ea-8e6d-806e6f6e6963}
                        {2e2d35b7-9624-11ea-8e6d-806e6f6e6963}
                        {2e2d35b8-9624-11ea-8e6d-806e6f6e6963}
                        {2e2d35b9-9624-11ea-8e6d-806e6f6e6963}
                        {d48f9feb-8b98-11ea-8e66-806e6f6e6963}
                        {bootmgr}
timeout                 1




bcdedit /set {fwbootmgr} displayorder <ID_OF_NEW_OS> {bootmgr}



```

6. Using BCDEdit confirmed none of the above made a difference 

```


bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\UBUNTU\SHIMX64.EFI
description             ubuntu
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {81eeb5ed-fe56-11e9-ac0b-f50b831b217f}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 10
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {81eeb5ef-fe56-11e9-ac0b-f50b831b217f}
displaymessageoverride  StartupRepair
recoveryenabled         Yes
testsigning             Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {81eeb5ed-fe56-11e9-ac0b-f50b831b217f}
nx                      OptIn
bootmenupolicy          Standard

```

After all of the above all i know for sure is that after updating Windows hides the Ubuntu Entry and lists itself as first in the boot order. 

Nothing i did changed that except re-installing Ubuntu and using boot repair fixed that until i loaded windows it broke it again back to step 1. 

Right now in my BIOS (UEFI) all boot devices are disabled. The entry for Ubuntu is still hidden (see EasyUEFI Attached), but GRUB is loading because all the others are disabled. 

Can anyone help me explain / fix what is going on here ? 

Thank you everyone for your time and expertise it is really appreciated.

---

### Post by oldfred on 2020-05-15
What brand/model system?

Some like Acer need UEFI update & then set password to rename "unknown" UEFI entry to ubuntu.
Some like HP need UEFI update, but change in boot order with efibootmgr (which grub uses) only works once. Most after UEFI update were able to reset order in HP's UEFI.
Some just seem to sync UEFI & Windows BCD and you have to add the BCD entry in Windows.

---

