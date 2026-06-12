---
title: "Grub error normal.mod not found."
date: 2013-03-23
forum: General Help
---

### Post by akshay.sulakhe on 2013-03-23
Hello friends,
                     I have installed Ubuntu 12.04 on my drive. Everytime i try to boot into it, it gives me a error 'grb/i386-pc/normal.mod not found'...I chroot into the environment and installed grub again using grub-install, also tried update-grub..Nothing seems to work. Can anyone tell me what the problem is. Thank you for your time. Have a nice weekend. :-)

---

### Post by jackyboy633 on 2013-03-23
Hi there,

The best solution would be to check the disc that you installed Ubuntu from for errors. Boot the system from the LiveCD, then when the purple screen with the person and the keyboard comes up, press any key, and then select the option to check the disc for errors. If the disc is OK, then reinstall, and it should be fine. If not, then you'll have to download Ubuntu again and make a new LiveCD.

Hope this helps :D

Jackyboy633

---

### Post by akshay.sulakhe on 2013-03-23
Hello,
           The system has installed just fine, coz i have 2 drives and other ubuntu installation detects the installation which does has a damaged bootloader...do i really need to reinstall even if installation is fine.

---

### Post by oldfred on 2013-03-24
If grub is installed correctly normal.mod should be in the /boot/grub folder.

You might have to reinstall grub either a chroot or use Boot-Repair to help do the full uninstall and reinstall.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

You also might be able to boot into your system with Supergrub. Then you can run the uninstall reinstall from inside your system.
      
 [URL="http://www.supergrubdisk.org/"]http://www.supergrubdisk.org/

      [/URL]
 # kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
# HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    [URL="http://www.supergrubdisk.org/"]
[/URL]

---

