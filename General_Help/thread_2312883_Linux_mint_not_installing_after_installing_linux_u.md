---
title: "Linux mint not installing after installing linux ubuntu on hp mini 110-1000"
date: 2016-02-08
forum: General Help
---

### Post by Jacob_Collins on 2016-02-08
Hi
My computer is a HP Mini 110-1000 (Windows XP Originally) and after trying to install kali, it deleted my OS(Well only the boot so the whole os was still there)
After a week my friend got linux mint cinamon for my computer. I tried to install it but i kept getting errors and the installation would crash. Also when i finally got to the installing part it would be frozen and not go anywhere. After attempting to install it, my computer had no space left. My friend is reinstalling ubuntu for me now bit is there a way that i can delete everything off my hard drive so i can install ubuntu without anything else.
Heres what happens
1) i turn on my computer, it displays the hp logo and "press f10 for BIOS, Press F9 For to change device boot order" thing. I chose bios and changed boot order to usb.
2) it has the linux mint with the countdown to boot, i press tab and select "Start Linux Mint"
3) it shows a grey screen, then the top right of the screen displays ""[     12.336084] ACPI PCC probe failed"."
4) it then goes to a blue screen woth avtext box in the middle saying "MDM Could not write a new authorisation entry to disk. Possibly out of disk space. Error: no space left on device"
5) It Then Goes to Another blue screen saying "Could not start the x server(your graphical environment) due to some internal error. Ease contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart MDM when the problem is corrected."
6) i then press enter and it says "[     12.336084] ACPI PCC probe failed" Again. Then i need to turn the computer off and it starts all over again.

I have tried to use the nodmraid or whatever command but it didnt work.

If anyone knows how to format my hardrive, please tell me.
Or any other possible fixes
EDIT: also if anyone knows of a program that i can put on my usb to make bootable, wen i boot it up i will have a file manager so i can delete anything without errors (like aroma for android recovery) or something that just resets my whole computer that would be great
Thanks :))

---

### Post by sudodus on 2016-02-08
If you install linux 'to the whole drive' it will overwrite whatever is there, so you need not erase the previous content. ***Backup*** valuable files before going ahead. You can backup files from your internal drive while booted into a USB pendrive.

In some very unusual cases  there are some very special data, that might confuse the installer. In such cases it is usually enough to wipe the first megabyte of the drive, and after that create a new partition table. You can use the same tools for your internal drive as described for USB drives in [this post](http://ubuntuforums.org/showthread.php?t=2311414&p=13429703#post13429703) in your previous thread.

I read a description of your computer via the internet, and I think you should try a light-weight flavour of Ubuntu: ***Lubuntu***, ***Xubuntu*** or ***Ubuntu MATE*** of the ***version 14.04.1 LTS***.

See these links and links from them,

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

After trying live, select the flavour that you like best, and ***install it to the whole drive***. It is the easiest way. This will overwrite whatever was there before.

Trying to install it alongside the current systems or into current partitions is possible but will be more complicated.

---

### Post by stalkingwolf on 2016-02-08
i have this same netbook. I run mint 13 mate with no problems

---

