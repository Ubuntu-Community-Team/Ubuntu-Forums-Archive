---
title: "Dual-boot issue: Windows won't start after upgrading from Ubuntu 20 to 22"
date: 2022-08-20
forum: General Help
---

### Post by earthboundbob on 2022-08-20
OK, I've got two apparently related problems here, and I'm stumped on both.

**First problem**: I've been running a dual-boot with Ubuntu 20 and Windows 10. Yesterday, I upgraded to Ubuntu 22. The upgrade worked well, but when I attempted to boot into Windows, I was met with a blue screen with stop code "I01: Initialization failed." The screen said it would restart my computer for me, which it did, but then, I was hit with Problem #2.

**Second problem**: After restarting, my monitor lost signal. The computer would still turn on, but the signal to the monitor was kaput. This has happened to me past, but  only after gaming in Windows: When I'd shut the computer down or restart after gaming, my monitor would lose signal. *The only solution I found was to physically remove the graphics card and reinsert it.* Somehow, this seemed to "reset" things, and the monitor would display on the next power cycle. This time, though, that did not immediately work. I had to re-seat the card a few times before I could get the monitor to pick up a signal again. (I tried plugging the monitor into the onboard graphics, but that didn't work.)

I managed to get the monitor working again, and booted back to Windows, which showed me the error but this time allowed me to select options from the blue screen. I did a system reset (nothing else was successful), but then I was returned straight back to the same stop code after that completed--which then cut the signal to my monitor.

So that's where I am. Windows appears to be broken, and the screen that *tells* me it's broken seems to cut the signal to my monitor, which requires physically re-seating my card (a GeForce GTX1050) to work again.

I should mention that I didn't just simply upgrade to the new version of Ubuntu; I installed the new version over the old one because I ran out of disk space on the initial upgrade and it broke. I'm thinking I may have accidentally did something to mess with the Windows partition during the reinstall, but I don't recall messing with anything Windows-related in the partitioning scheme.

I'll be grateful for any help you can offer me!

**UPDATE: **After much trial and error, I determined that, somehow, Windows was no longer being detected on my disk. I checked the partitions and, sure enough, while my file directory was there, the Windows OS itself was not. I imagine the only way this could have happened is that I accidentally deleted it when re-installing Ubuntu. I did a fresh Windows install and everything seems to be working well.

I never did figure out the loss of signal to the monitor, though.

Thank you for all your help, everyone!

---

### Post by oldfred on 2022-08-20
Cannot help on  a hardware issue which it sounds like you video issue is. May be a Windows driver?

What brand/model system? 
When installing Ubuntu did you install using safe boot and install proprietary/restricted drivers. That installs correct proprietary nVidia driver automatically.

Can you boot Ubuntu or live installer? If so run this report, just to see details of your configuration. 

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dragonfly41 on 2022-08-20
I would search around for OldFred et al advice on dual booting.
Also have a LiveUSB at hand.
And then Boot Repair file.
Finally when booting up (F2 ?) read your BIOS to check settings.
I don't remember what has to be enabled/disabled in BIOS. Check forum discussions on Secure Boot etc.
Your monitor problem adds a new twist.

Ah! OldFred popped into room.

---

### Post by earthboundbob on 2022-08-20
Apologies if I struggle answering these questions; I'm relatively inexperienced here and don't know a lot of the lingo.

My computer is one I built myself. I know I'm using a Gigabyte motherboard. It's about eight years old and some of its functionality has failed, including audio and Ethernet, both of which I bypass using (respectively) a USB adapter and a wireless card.

I do not remember using safe boot when I installed Ubuntu, and I know that I did not install proprietary drivers.

How do I run the report you are referring to?

---

### Post by earthboundbob on 2022-08-20
OK, I ran Boot Repair. Here is the link to the report:

[https://paste.ubuntu.com/p/HVF9X2QMjs/](https://paste.ubuntu.com/p/HVF9X2QMjs/)

---

### Post by oldfred on 2022-08-20
Your system is UEFI with UEFI installs of both Windows & Ubuntu.
Your UEFI is set to boot install in sda1, where main drive is  to sdb. Is sdb, a flash or removable drive? Says its a small mSATA drive. while 16GB can work for / (root) it now is not generous. You may need a lightweight flavor and not use any snaps that take more space.

Bit unusual to see swap as sdb1 or first partition. Often Windows has that as recovery partition. But since motherboard with your own installs, that may be normal.

Not really seeing much on Ubuntu side.
Lets get more details on hardware. Copy all three lines & paste as \ is a line continuation.
Review link for more details on how this report works.

Hardware doucumentation script, one line using && \ to make as one entry
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info

---

### Post by earthboundbob on 2022-08-20
Thank you very much for continuing to help with this.

Yes, I have Ubuntu / installed on a 15 GB flash drive. /home is installed on half of a 1TB hard drive, while the other half contains the Windows partition. (At least, I think I am remembering this correctly.)

Here is a link to the report I just ran: [https://paste.ubuntu.com/p/xc7bGTWkBn/](https://paste.ubuntu.com/p/xc7bGTWkBn/)

---

### Post by oldfred on 2022-08-20
That paste is the script/code to create the report of what hardware you have.
Did it not generate output & offer to upload it. 
The uploaded version removes some detail like serial numbers that users may not want to post.
Your saved version should show that extra detail.

---

### Post by earthboundbob on 2022-08-20
I'm sorry, I think I got it this time: [https://paste.ubuntu.com/p/8czt9t2qTh/](https://paste.ubuntu.com/p/8czt9t2qTh/)

---

### Post by oldfred on 2022-08-20
Do you have the newest UEFI from Gigabyte for your Mother board. 
You show f8.
This shows f9 and f10 as beta.
[https://www.gigabyte.com/Motherboard/GA-F2A88XM-D3H-rev-31/support#support-dl-bios](https://www.gigabyte.com/Motherboard/GA-F2A88XM-D3H-rev-31/support#support-dl-bios)

I do not know AMD well, but others have posted IOMMU issues.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to AMD  boards.

Older posts, but some settings may still be required.
Ryzen + Gigabyte installation problem Newer kernels & IOMMU 2017
[https://ubuntuforums.org/showthread.php?t=2362773](https://ubuntuforums.org/showthread.php?t=2362773)
Some Gigabyte boards need acpi=off boot parameter also
Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)

---

### Post by earthboundbob on 2022-08-21
I just updated my BIOS to F9 and made sure IOMMU was enabled.

When I booted into Windows, the Gigabyte screen that appears before Windows loads showed "Preparing" and then "Undoing Changes" for quite some time before the computer restarted itself. I booted back into Windows and was met with the same IO1: Initialization Failed error.

Is the best course of action at this point to try to re-install Windows?

---

### Post by oldfred on 2022-08-21
Do not know Windows, you may do better in a Windows forum.
If you have good backups, then reinstall can work. 
I last installed Windows XP 15 years ago and remember Windows install was a huge hassle over an Ubuntu install.

---

### Post by earthboundbob on 2022-08-21
I will check into a Windows forum. Thanks again for your time!

---

### Post by yancek on 2022-08-21
Several options to repair this error at the link below if you want to try before reinstalling windows.

[https://www.stellarinfo.com/article/hal_initialization_failed-error-windows-10.php](https://www.stellarinfo.com/article/hal_initialization_failed-error-windows-10.php)

---

### Post by oldfred on 2022-08-21
In looking something up I ran across this on Windows Safe boot to get to repair it.

> Yes. Of course, Safe Mode is not always easy to get to since Windows 8 days. You may have to crash the system during boot-up twice (power off during the circling balls or wait for the inaccessible boot problem then power off, twice) to get the system to attempt an Automatic Repair. Then you can get it to go to safe mode.



---

