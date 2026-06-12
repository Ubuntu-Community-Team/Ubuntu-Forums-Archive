---
title: "i want to remove certain boot record by grub"
date: 2014-09-22
forum: General Help
---

### Post by jhwon0415 on 2014-09-22
i installed ubuntu recently, and through this, i made few mistakes
i removed windows MBR in accidentally, and i recovered it
when i recover it, i made to MBR ... 
in grub.cfg.. it shows like this

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root XXXXXXXXXXXXXXXXXX
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root YYYYYYYYYYYYYYYYYYYYYY
    chainloader +1
}

XXXXX.. and YYYY is hardware id.
those two boots exactly same windwos7, and i want to remove one, 
i want to remove upper one, cuz it is on linux-hdd
how can i remove it?

---

### Post by oldfred on 2014-09-22
Did you run Boot-Repair?

Since many users do not realize the 100MB boot partition is essential to Windows booting, they delete it. So one of the first things Boot-Repair does is copy bootmgr and BCD to your main install. You may not be able to use f8 to get into repair console if you delete the 100MB partition, but when booting from grub Windows loads so quickly f8 does not usually work. Better to make a Windows repairCD or flash drive to repair Windows.

You can copy the Windows boot stanza that you want into 40_custom or if you want Windows first in grub menu copy 40_custo to 06_custom and then copy boot stanza into that. Then turn off os-prober so grub is not auto finding anything. If later you reconfigure you can turn it back on.

       Copy the  boot stanza from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Once you know new entry works, add a new line in grub configuration file:
      
 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

Grub runs all scripts that are executeable and start with two digits and an underscore. And it processes in number order.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

