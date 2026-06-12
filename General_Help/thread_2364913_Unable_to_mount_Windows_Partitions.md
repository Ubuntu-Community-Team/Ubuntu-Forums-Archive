---
title: "Unable to mount Windows Partitions"
date: 2017-06-29
forum: General Help
---

### Post by plopmon on 2017-06-29
I was using windows before but it was way too laggy and took almost an hour to just load up the lock screen after starting. so i had installed Ubuntu side by side Windows 10. everything is going fine but problem arises when , to get my data from windows partitions, file manager is unable to mount the 2 drives ( C: and E:)
i read a post (which didnt helped me though) which said that either i should log in to windows back and shutdown completely or theres a way to forcibly mount the drives in read or write mode. now logging back onto windwos wont work coz now it shows up a BSOD error of 'bad_system_config' . now i really dont care about C: drive and wont mind formatting it and merging with the Ubuntu drive all i care is about E: drive and want to mount its data safely . 
please advice...

[EDIT 1]
when mounting the C: drive this error shows up form the file manager

Error mounting system-managed device /dev/sda4: Command-line `mount "/mnt/66F87F71F87F3DFD"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


i am new to linux so please suggest somethings

---

### Post by Autodave on 2017-06-29
I would try to get into the BIOS and turn off "Fast boot". However, if you manage to do that, you might still have to reboot Windows once to actually disable the fast boot.

If you get past that, then Ubuntu should be able to mount and read what is on those 2 drives or partitions.

Be careful when in the BIOS and ONLY change the fast boot option!!!

---

### Post by yancek on 2017-06-29
You should have an option in windows 10 to turn it off.  Under Menu, Settings, System, Power & Sleep, Additional Power settings.  Here on the left are options to Choose what the power button does and Choose what closing the lid does.  There is an option under each to Change Settings that are currently unavailable.   Select this, the fast startup check box should be available to uncheck.

---

### Post by plopmon on 2017-06-29
> **Autodave said:**
> I would try to get into the BIOS and turn off "Fast boot". However, if you manage to do that, you might still have to reboot Windows once to actually disable the fast boot.

If you get past that, then Ubuntu should be able to mount and read what is on those 2 drives or partitions.

Be careful when in the BIOS and ONLY change the fast boot option!!!

i have once managed to get back to windows and disabled fast startup throught it. but not from BIOS

> **yancek said:**
> You should have an option in windows 10 to turn it off. Under Menu, Settings, System, Power & Sleep, Additional Power settings. Here on the left are options to Choose what the power button does and Choose what closing the lid does. There is an option under each to Change Settings that are currently unavailable. Select this, the fast startup check box should be available to uncheck.

i would appreciate the method which does not involves logging back to windows and shutting it down since i want to get free from it(windows). i just need the E: Drive basically and would love to format C: drive and merging it with Ubuntu (if it is safe)

[EDIT 1]
plus the shutdown option for me is disabled coz on startup of windows it gives me a BLUE SCREEN ERROR

---

### Post by yancek on 2017-06-29
If your intention is simply to access the windows partition to copy data FROM it, you can mount it read-only.  That is explained in some detail at the site below and if scroll about half-way down the page, you will find a sample mount command for read only.  Make sure you get the correct partition because I can guarantee you it won't be C: or E:.

 [https://askubuntu.com/questions/280530/how-do-i-mount-a-hibernated-partition-with-windows-8-in-ubuntu](https://askubuntu.com/questions/280530/how-do-i-mount-a-hibernated-partition-with-windows-8-in-ubuntu)

---

### Post by plopmon on 2017-07-01
it ain't working again......

what if just format the C: drive using GParted and merge it with linux partiton?

---

### Post by leunam12 on 2017-07-01
sudo ntfsfix /dev/sda4

That command should work to fix the dirty/hibernated issue

---

### Post by SeijiSensei on 2017-07-01
I would strongly recommend not using ntfsfix but the native Windows chkdsk program.  You can see it in the Administrative section of the Control Panel.

---

### Post by leunam12 on 2017-07-01
What is wrong with ntfsfix? Just curious.

---

### Post by yancek on 2017-07-01
If a bootable windows system is available, it is always better to use the proprietary windows software such as chkdsk to make repairs.  ntfsfix will work but only on very minor problems.  No logical reason for any Linux developers to spend their time on writing software to repair proprietary problems, that's up to microsoft as it should be.

---

### Post by johndough2 on 2017-07-02
Hi

Just untick / uncheck the box labeled

Turn on fast startup (recommended)

then do a complete shutdown.

Boot ubuntu, and mount accordingly, then copy off what you want from the windows area, next delete them.

End of microsoft problems.

---

### Post by Mark Phelps on 2017-07-02
Two comments ...

First, Fast Boot is a UEFI boot option; Fast Startup is a Windows hibernation option.  It is the second that prevents mounting Windows filesystems, not the first.

Second, Fast Startup is know to cause problems in some PCs, so unless you have a very long boot time in Win10, it is best to have it disabled.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

### Post by SeijiSensei on 2017-07-03
> **leunam12 said:**
> What is wrong with ntfsfix? Just curious.

From the manual page for ntfsfix:

> ntfsfix is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS inconsistencies,  resets the  NTFS  journal file and schedules an NTFS consistency check for the first boot into Windows.

---

