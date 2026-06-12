---
title: "Permission Denied on a new USB"
date: 2020-08-21
forum: General Help
---

### Post by kyledefranco2 on 2020-08-21
I have a 16    GB usb drive.
I stick it in my Raspberry Pi.
I drag a simple text file from my desktop to the folder.
It moves over ok.
When I double click the file, I get the following error message:

Failed to open file “/media/kyle/USBSTORAGE/test.txt”: Permission denied

I have formatted the drive through the "Disks" program and the following:

sudo mkfs.vfat /dev/sda1
sudo chmod 0777 /media/sda1 -r
sudo chmod 0777 /media/kyle/USBSTORAGE/
sudo chmod 777 /media/kyle/USBSTORAGE/

reboot.
Remove, then reboot.

Nothing works.

Here is my lsblk:

NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0         7:0    0 48.4M  1 loop /snap/core18/1753
loop1         7:1    0 85.5M  1 loop /snap/core/9806
loop2         7:2    0  112K  1 loop /snap/gtk2-common-themes/16
loop3         7:3    0 48.8M  1 loop /snap/core18/1888
loop4         7:4    0 62.1M  1 loop /snap/gtk-common-themes/1506
loop5         7:5    0   41M  1 loop /snap/leafpad/75
loop6         7:6    0 25.9M  1 loop /snap/snapd/8147
loop7         7:7    0   16K  1 loop /snap/software-boutique/56
loop8         7:8    0   26M  1 loop /snap/snapd/8791
loop9         7:9    0    8K  1 loop /snap/ubuntu-mate-pi/11
loop10        7:10   0 14.9M  1 loop /snap/ubuntu-mate-welcome/540
sda           8:0    1 14.9G  0 disk 
&#9492;&#9472;sda1        8:1    1 14.9G  0 part **/media/kyle/USBSTORAGE**
mmcblk0     179:0    0 58.2G  0 disk 
&#9500;&#9472;mmcblk0p1 179:1    0  255M  0 part /boot/firmware
&#9492;&#9472;mmcblk0p2 179:2    0   58G  0 part /

Any help is appreciated.
Thanks!

---

### Post by TheFu on 2020-08-21
chmod doesn't work for Windows file systems. fat32, exfat, ntfs. None of those work.
Use **f2fs** if you want a linux flash friendly file system with full Unix permissions.

The other option is to set the desired permissions, owner, group thought more complex mount options.

rebooting will never help. that's Windows-thinking.

---

