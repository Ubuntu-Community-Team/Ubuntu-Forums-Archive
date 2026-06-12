---
title: "grub wont boot windows ten"
date: 2016-09-21
forum: General Help
---

### Post by jaredes291 on 2016-09-21
My specs:
dell inspiron 15 3000
8 gig ram
I5 4 core
500 gig HDD
ubuntu 16.0.4 LTS
Windows 10 


watch the vid:
[https://youtu.be/mxSgXA75hsY](https://youtu.be/mxSgXA75hsY)


so when i boot grub comes up and i enter windows 10
1 of 3 things will hapen


1
 it will boot windows fine


2
 it will show the screen of lines(see [VID]("https://youtu.be/mxSgXA75hsY"))
and then boot windows


3
 it will show the screen of lines and wont boot windows 


I left it for 2+ hours and it did not boot windows 


I have no idea what is going on so ya

---

### Post by oldfred on 2016-09-21
Grub only boots working Windows.
Is system BIOS or UEFI?

In Windows 10 you must have fast start up off.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by jaredes291 on 2016-09-21
windows is working i am useing it 

but when i install a update it will boot ubuntu but not windows

---

### Post by oldfred on 2016-09-21
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jaredes291 on 2016-09-21
[http://paste2.org/EyvPPpcx](http://paste2.org/EyvPPpcx)

---

### Post by oldfred on 2016-09-21
So what is not working?
Report looks normal.

If you can boot Windows that is good.
From grub menu can you boot recovery mode or one of the older kernels?

---

### Post by jaredes291 on 2016-09-21
i need to install windows updates but when i install it asks for a reboot and it reboot then it wont boot windows from grub

i have posted this on a windows forum as well in case it is windows error. but i have ubuntu install too and grub so i posted it here

---

### Post by oldfred on 2016-09-21
Windows updates reset Windows to defaults.
So you may have to turn off fast start up again. Reset UEFI to boot Ubuntu first and perhaps other changes.
Grub only boots working Windows.

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by jaredes291 on 2016-09-22
i dont have UEFI i have BIOS

---

### Post by oldfred on 2016-09-22
I am surprised that Windows updates then did not install the Windows boot loader to the MBR.

But you must make sure Windows fast start up is off, or that Windows does not need chkdsk.

When Windows was working did you make the Windows repair/recovery flash drive?

You will need the Ubuntu flash drive & the Windows flash drive to fully maintain dual booting.

---

### Post by jaredes291 on 2016-09-22
can you put grub in verbose mode when it boots windows

---

### Post by oldfred on 2016-09-22
Once grub starts to boot Windows, it chainloads to the Windows boot files. And does not have any control over the Windows boot process.

---

