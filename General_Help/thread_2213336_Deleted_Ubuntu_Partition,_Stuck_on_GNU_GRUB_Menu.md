---
title: "Deleted Ubuntu Partition, Stuck on GNU GRUB Menu"
date: 2014-03-26
forum: General Help
---

### Post by Sawyer_Stahl on 2014-03-26
Hi there. I recently tried out Ubuntu. I decided to run it alongside Windows 8.1. I set up a separate partition, and installed it there. After awhile I decided it wasn't really my thing. I then deleted the partition and melded the free space back with my Windows partition. I was able to boot into Windows 8 just fine, and all of my stuff was still there. However, when I turned it off and back on again, I get stuck with a GNU GRUB screen. 

I'm going to explain what happens for every one of the things I try when turning on my computer. I'm sorry if I'm a bit too detailed, but I want to cover all the bases.

**_TURNING ON NORMALLY_**

When I turn on the computer normally, I get the following screen:

[CENTER]GNU GRUB version 2.00-19ubuntu2.1

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_
[/CENTER]
I can then type things, but I don't know what to type.


_**TURNING ON WITH USB STICK**_

When I turn the computer on with the USB Stick inserted (the one with the original file I used to install Ubuntu in the first place), it gives me this screen:

[CENTER]
GNU GRUB version 2.00-19ubuntu2

-Try Ubuntu without installing
-Install Ubuntu
-OEM install (for manufacturers)
-Check disc for defects

Use the [up arrow] and [down arrow] keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command line. ESC to return previous menu.

[/CENTER]
              **_Try Ubuntu without installing: _**it goes to Ubuntu, and I can use it just fine. It's what I'm using right now to type this.
              **_Install Ubuntu: _**Goes to Ubuntu install. It does not recognize that Windows 8 is on my computer, so I choose "something else" (as opposed to erase disc completely). It then lists my partitions. I choose to stop here. If you want info about my partitions I can give it to you.
              **_OEM Install: _**It takes me to an installation menu. I don't go any further.
              **_Check disc for defects: _**It shows me a purple Ubuntu screen, and it checks the discs. When it's finished it says "Check finished: errors found in 2 files! Press any key to reboot your system." When I reboot my system, it goes back to the original USB menu.

[B][U]PRESS ASSIST BUTTON TO TURN ON

[/U][/B]Because I have a Sony Vaio, it has a special "Assist" button near the Power button. It then takes me to a menu that shows the following:

[CENTER]
VAIOCare | Rescue Mode
This screen is displayed when you pressed the [ASSIST] button. To start Windows, press Esc button, or shut down [F4] then press Power button.

-Recover or maintain your system [F10]
-Start from media (USB device/optical disc) [F11]
-Start from network [F12]
-Start BIOS setup [F2]
-Shut down [F4]
-Start Windows [Esc]
-Select language [F1]

Model: SVT13134cxs | Serial: 54528232-0005801 | Service Tag: C90559TQ

[/CENTER]
          **_Recover or maintain your system_**: goes to GNU GRUB screen (same as turning on normally)

          **_Start from media: _**if the USB is inserted, it's the same as Turning on with USB. If it isn't, it says OPERATING SYSTEM NOT FOUND.

          **_Start from network: _**black screen which then says "checking media". It then goes to GNU GRUB screen (same as turning on normally)

          **_Start BIOS setup: _**It's a grey and blue screen with a few tabs and several options. If you need more information I can give it to you, but the ones I find to be related are:

[CENTER]Secure Boot: I have it disabled.
Boot Mode: I have it set to UEFI.
Boot Priority: External Device, Internal Hard Disk Drive, Network
[/CENTER]
          **_Shutdown: _**Shuts the computer down.

          **_Start Windows: _**goes to GNU GRUB screen (same as turning on normally)

          **_Select Language: _**Brings me to a language menu.



That's all the information I can think to give you. If you need more let me know. All I want is to go back to just Windows, preferably without losing the files I have in it.

---

### Post by mastablasta on 2014-03-26
tldr...

use windows disk to "repair" master boot record (MBR). iuf you use uefi then it's probably efi boot loader you need to "repair". the repair function replaces any other boot loader (such as grub) with windows only bootloader stuff.

edit: for example: [http://answers.microsoft.com/en-us/windows/forum/windows_8-system/how-to-fix-windows-8-mbr/3d5439e9-521d-445c-ad52-a1d4b7f17237](http://answers.microsoft.com/en-us/windows/forum/windows_8-system/how-to-fix-windows-8-mbr/3d5439e9-521d-445c-ad52-a1d4b7f17237)

anyway Microsoft window issue (since it can't use Grub) you will get better support on windows forums.

---

### Post by Mark Phelps on 2014-03-26
For a Windows forum, try eightforums.com -- the premier Windows 8 forum.

---

