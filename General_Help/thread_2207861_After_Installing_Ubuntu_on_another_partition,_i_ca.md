---
title: "After Installing Ubuntu on another partition, i can no longer access windows 8.1"
date: 2014-02-25
forum: General Help
---

### Post by xepherxv on 2014-02-25
i created a new partition just for Ubuntu, but when grub appears it only shows diffrent versions of linux and ubuntu, i still have the 1.5terabyte partition windows would be on, but i cant seem to access it, ive tried everything, the issue is that i dont have a disc or a key (i used my freinds) so i cant get a direct iso to create a bootable usb for windows 8.1

does anyone have any ideas -- i cant afford to lose windows! i have everything on that thing! thats why i made a new partition!

im just scared depressed and generally out of ideas.

anyone out there that can help?

---

### Post by xepherxv on 2014-02-25
nobody knows how to help? ._.

---

### Post by oldfred on 2014-02-25
Please only bump once per 24 hours. 
We all are volunteers and in many time zones, so you may not get immediate answers. 

Try this in Ubuntu 
sudo update-grub

If you have Windows 8 pre-installed it is in UEFI boot mode. Did you install Ubuntu in UEFI mode also?
UEFI and BIOS are not really compatible so once you start to boot in one mode you cannot change to boot another system at grub menu. But should be able to choose a UEFI system from UEFI menu or BIOS system. But some do not auto switch and you have to turn on UEFI mode or turn off BIOS mode.

Did you leave Windows hibernated or not turn off the fast boot when you installed. You then have issues with Windows.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html

      [/URL]
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

    [URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]
[/URL]

---

### Post by IvoGuerreiro on 2014-02-25
Hi,
I'm new on this, but for my research it seems you are experiencing some GRUB problems.
Try boot repair, read this link:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by xepherxv on 2014-02-25
i have UEFI on my motherboard, i used a WINDOWS 7 tut for installing ubuntu, i realise that this was a mistake. i did not turn off "fast boot"

so am i screwed?

i cant access windows at all


Edit: i have ran boot repair a total of 3 times thus far

---

### Post by IvoGuerreiro on 2014-02-25
No you are not, just as i keep looking and searching, and wait for someone more experience to reply.

---

### Post by IvoGuerreiro on 2014-02-25
Try enable: Attempt secure boot in your Bios

---

### Post by xepherxv on 2014-02-25
after googleing and attempting it: i do not believe my motherboard; "asus crosshair v formula-z" has this feature

---

### Post by IvoGuerreiro on 2014-02-25
Have you Windows 8 disk? If Yes try force boot into the Windows 8 CD from your BIOS and than try repair.
Link:[http://askubuntu.com/questions/336817/dual-booting-problem-with-windows-8-and-ubutnu-12-10](http://askubuntu.com/questions/336817/dual-booting-problem-with-windows-8-and-ubutnu-12-10)

---

### Post by xepherxv on 2014-02-25
i do not, my copy of windows.....well.....wasnt exactly legit. i made my own computer i cant afford a $150 operating system (i did not know about linux at the time) i was planning on buying it later, but i do now have a job atm so im at a standstill

---

### Post by IvoGuerreiro on 2014-02-25
Ok. try this option in your BIOS.
[ATTACH=CONFIG]250670[/ATTACH]

---

### Post by dragonfly41 on 2014-02-25
> Edit: i have ran boot repair a total of 3 times thus far

In the boot-repair window can you click on the *second* button 
**Create a boot-info summary**

and post here the url which is generated.

We can then inspect your system.

---

### Post by oldfred on 2014-02-25
Since you ran Boot-Repair several times, did you say yes to buggy UEFI? Best to undo it.

 buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

Then see if you can boot Windows. If not post link to BootInfo Report from Ubuntu or live installer.

---

### Post by IvoGuerreiro on 2014-02-25
There you have the cavalry has arrived, now it's time to try what they say.;-)

---

### Post by QIII on 2014-02-25
[CENTER]> **xepherxv said:**
> i do not, my copy of windows.....well.....wasnt exactly legit. i made my own computer i cant afford a $150 operating system (i did not know about linux at the time) i was planning on buying it later, but i do now have a job atm so im at a standstill[/CENTER]
By which I take it that you are violating Microsoft's licensing.  We do not condone this on the UF.

Closed.

---

