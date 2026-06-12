---
title: "Separate boot volume with &quot;noauto&quot; in fstab is mounted in 13.10"
date: 2013-10-18
forum: General Help
---

### Post by erike4 on 2013-10-18
I am using a separate boot volume using burg to boot a number of systems.  Previous to 13-10 the boot volume specified with "noauto" in /etc/fstab was not mounted as:
_________________________________________________________________________________________
#/dev/sda3   /boot
UUID=d1b07952-aa4f-4648-bbd3-504e2e3d801a /boot           ext3    noauto,errors=remount-ro 0       1
_________________________________________________________________________________________

Now the volume is mounted after any 13-10 system is running.  This is a minor inconvience as if I remember to unmount the volume during a kernal update or mount is to write the MBR after a install when grub is installed.  

Is this a bug, change in methodolgy or am i dong something wrong?  Is there a way to dismount the volume automatically
after a boot?

---

### Post by erike4 on 2013-10-20
Also 13.10 mounts removable drives in a folder of the logged on user (that is with auto logon) under a folder with the userid in the media file rather in the media folder itself (ie. /media/<userid> folder).

---

### Post by oldfred on 2013-10-20
You should not be sharing a /boot partition with multiple installs. That will lead to conflicts. Only if the partition is a grub only partition may it work. I used that with grub legacy, but not required with grub2.

External devices now are mounted by user. There was some explanation, but I did not save a link. 

Best to see details of systems. I also run the bootinfoscript as part of my rsync backup, just to document my system. The first part of Boot-Repair report is just bootinfoscript.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by erike4 on 2013-10-23
It seems all file systems in /etc/fstab or not (excepting LMV volumes) are now in 13-10 mounted during boot where previously noauto would prevent the mounts (13.04 and before)..  Fstb has noauto specified.  

Since I have muddied up the waters with a separate boot volume for all my systems (with only the burg loader in it (and some various system rescue programmes) and the burg.cfg root set via UUID to  the individual partitions or LVM volumes) I changed the MBR to boot directly to the partition and the results were the same on the 13-10 systems - that the files systems were mounted even with no-auto in FSTAB.  
NB: with the grub (pre-) boot volume being mounted now any changes to the kernal are indeed confused as the proper system's own boot volume is not accessible).  The separate boot volume is being used because Grub and Burg put out many duplicate extra boot selections for each system where Grub ir berg update is not run.  As this can be up to eight entries with recovery etc. for each bootable partition (kubunto, edubunto, SUSE (only four entries) lubuntu etc...) all marked Ubuntu 13-10 (or previous) it makes a mess to try to find which system boots by which entry. so with the seperate boot volume it is a new install Which sets the MBR to the installed system) and zap the MBR back to the boot volume all is orderly

A Side Question: The change of the mountable volumes in a folder for the logged on user in the /media folder is a bit of a pain.  Is there a way to change that back before I have to change the code for my automated backup system which reads /media to see what volumes are mounted to detect which  file systems are to be backed up.

---

### Post by oldfred on 2013-10-23
I just turn off os-prober and add my own entries to 40_custom.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)


 I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

