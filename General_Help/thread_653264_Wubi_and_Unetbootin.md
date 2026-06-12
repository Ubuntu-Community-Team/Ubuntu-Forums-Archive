---
title: "Wubi and Unetbootin"
date: 2007-12-29
forum: General Help
---

### Post by habibi88 on 2007-12-29
Yesterday I downloaded and "installed" WUBI, but nothing happened.  My system rebooted to Windows.

Then, today I downloaded and "installed" UNetbootin, but nothing happened either.  My system just rebooted to Windows.

I wonder if it is because my C drive is formatted as NTFC and not FAT.

I deleted both programs.

Any ideas?  Thanks in advance.

---

### Post by K.Mandla on 2007-12-29
Moved to Wubi subforum. :)

---

### Post by tylerspaska on 2007-12-30
i've never used UNetbootin, so i can't say anything about that.

as for Wubi, it should work fine on any windows partition. you said that you installed on NTFC, i think you mean NTFS, but that is what i have installed it on several times. after installing, look for a folder on the drive you installed on called wubi. usually C:\wubi. that should contain all of the wubi files and everything else. it is a folder within the windows filesystem that is formated separately as an ext3 filesystem. 

when you reboot you don't get options to boot from windows or from wubi? it just goes straight to windows?

---

### Post by habibi88 on 2007-12-30
Yes, that's right.  When I reboot the computer boots right into Windows, and there is no option to boot into Ubuntu (or Linux for that matter.) Thanks for your prompt answer.

---

### Post by ago on 2007-12-30
Unetbootin uses the same mechanism as wubi to modify the bootloader.
You may want to find out why, check c:/boot.ini

---

### Post by habibi88 on 2008-01-01
Hi:

This is a copy of C:/boot.ini  -----

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
c:\grldr.mbr="UNetbootin-ubuntu710rev10"

Don't know what it all means.

Thanks for your help.

---

### Post by ago on 2008-01-02
looks good to me, you should have 3 boot options: windows, recovery console and unetbootin
If you do not chances are that another boot.ini is used instead or a different bootloader alltogether

---

