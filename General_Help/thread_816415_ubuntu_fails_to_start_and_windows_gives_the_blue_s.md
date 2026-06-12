---
title: "ubuntu fails to start and windows gives the blue sc"
date: 2008-06-02
forum: General Help
---

### Post by dewdropper on 2008-06-02
nither windows or Ubuntu will start. windows gives me a blue screen ubuntu gives me this


BusyBox V1.1.3 (Debian1:1.1.3-5ubuntu12) Built - in shell (ash)
enter 'help' for a list of built-in commands

(initramfs)_


i am wondering if i disable restart on system failure if i could see what the blue screen says which from what i have seen is about the same as ubuntu 
when i press esc in ubuntu it gives me two things repeated 
i am not sure if it is suppose to or not anyway there are
ubuntu 8.04, kernel 2.6.24-17-generic and that with (recovery mode)  then it repeats i don't even begin to understand the last option ,sorry complete noob,  but it is ubuntu 8.04, memtest86+

if anyone knows why there are two of those there i would like to just know

when i click on the recovery option it does a lot of stuff that is to fast to read then it says

$logfile indicates unclean shutdown (0,0)
failed to mount '/dev/sdal':operation not supported mount is denied becouse NTFS is marked to be in use. chose one action

Choice 1: if you have windows then disconnect the external devices by clicking on the safely remove hardware' icon in the windows taskbar then shutdown windows cleanly 

(can't do that blue screen of death)

Choice 2 if you don't have windows then you can use the 'force' option for your own responsibility. for exaple tyoe the compand line mount -t ntfs-3g /dev/sdal /root -o force

or add the option to the relevant row in the /etc/fstab file:
   /dev/sdal/root ntfs-3g /dev/sdal /root -o force
mount : mounting ?dev/disk/by-uuid/28C4CF7ECF4CAE on /root failed: Success mount: Mounting /root on /host failed: Invalid argument
alert! /host/ubuntu/disk/ root/disk does not exist. dropping into shell!

then it goes into the same thing as before 

as far as i can tell both windows and Ubuntu thick i have devices connected that i don't then they crash sorry i am a complete noob,even though i can't even spell it, i know a lot of that was worthless i am sure. thank you for any help you can give me.

---

### Post by Dave2k6 on 2008-06-04
> **dewdropper said:**
> BusyBox V1.1.3 (Debian1:1.1.3-5ubuntu12) Built - in shell (ash)
enter 'help' for a list of built-in commands

(initramfs)

Hi

To fix the initramfs issue, do the following...

Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

Windows issue, you need to run chkdsk /r on the drive somehow, as the NTFS drive is marked as 'in use' by Windows.

---

