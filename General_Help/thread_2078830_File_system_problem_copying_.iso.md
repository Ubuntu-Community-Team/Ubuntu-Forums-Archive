---
title: "File system problem copying .iso"
date: 2012-10-31
forum: General Help
---

### Post by lemonoid on 2012-10-31
I have started having this problem that is really aggravating. I have a 4.7GB .iso file that I need to transfer to my Windows. Every time I try to copy the file, it begins to copy and gets towards the end, and EVERY time, I get the error that the file is too large to copy. I have tried to copy it onto a 8GB flash drive with 5 GB free storage, a 16GB flash drive with 15.9GB free storage, and onto a 500GB external HD with over 400GB free storage. On the smaller flash drives, the iso file shows up in the contents, but as 4.3GB in size. With the 500gb hard drive, I did not get the error, instead my folder system froze up, as did the process in the terminal. I could not open any folders on the desktop, and I could not open the hard drive on the desktop. When I tried to kill the cp signal, it would not kill, even when I tried various kill signals, I ended up having to restart the computer. This is getting very frustrating. Does anyone have any clue what the problem is?

---

### Post by steeldriver on 2012-10-31
Likely the flash drives are formatted as FAT32 - which has a size limit of 4GB for a single file - you could reformat them as NTFS if your Windows box supports that (Win 7 certainly does)

---

### Post by dwb814 on 2012-10-31
Hi,
I've run into this issue trying to move an .ISO in the GUI. The best way is to move it through CLI. Open a terminal in the folder where the .ISO is and move it to where you want. Here's an example: 
```
dan@dan-desktop:~/Desktop/iso$ mv ubuntu-12.04.1-desktop-amd64.iso /media/92AA-A9E8 
```I have a folder on my desktop named "iso" which has the "ubuntu-12.04.1-desktop-amd64.iso" in it, and I am moving to another drive called "/media/92AA-A9E8".
When you give the command, wait, it will take a bit to move it. The cursor will go back to it's regular flashing when the file has been moved. Also do a MD5sum check afterwards to make sure the ISO is OK.

---

### Post by lemonoid on 2012-10-31
> **dwb814 said:**
> Hi,
I've run into this issue trying to move an .ISO in the GUI. The best way is to move it through CLI. Open a terminal in the folder where the .ISO is and move it to where you want. Here's an example: 
```
dan@dan-desktop:~/Desktop/iso$ mv ubuntu-12.04.1-desktop-amd64.iso /media/92AA-A9E8 
```I have a folder on my desktop named "iso" which has the "ubuntu-12.04.1-desktop-amd64.iso" in it, and I am moving to another drive called "/media/92AA-A9E8".
When you give the command, wait, it will take a bit to move it. The cursor will go back to it's regular flashing when the file has been moved. Also do a MD5sum check afterwards to make sure the ISO is OK.

That's actually the way that I tried to move it onto my hard drive. Maybe I'll try it with the flash drives.

---

### Post by coldraven on 2012-10-31
My 1TB external USB drive came formatted as FAT32. I reformatted it to NTFS with gparted and have no trouble copying files bigger than 4GB using the file manager.

---

### Post by lemonoid on 2012-10-31
> **coldraven said:**
> My 1TB external USB drive came formatted as FAT32. I reformatted it to NTFS with gparted and have no trouble copying files bigger than 4GB using the file manager.
I can't seem to even get the option to do this with my 16GB flash drive. I don't see anywhere on gparted to reformat the file system of this device.

---

### Post by dwb814 on 2012-11-01
use "disk utility", if not installed do ```
sudo apt-get install gnome-disk-utility
```  once open, select your drive on the left and click on "format volume" button. That should do it.

---

### Post by lemonoid on 2012-11-01
> **dwb814 said:**
> use "disk utility", if not installed do ```
sudo apt-get install gnome-disk-utility
```  once open, select your drive on the left and click on "format volume" button. That should do it.
Thanks. I already had disk utility, I just forgot about it because I don't think I've ever used it. I reformatted successfully, I'm trying to transfer the file now and see if that worked.

---

### Post by coldraven on 2012-11-02
> **lemonoid said:**
> I can't seem to even get the option to do this with my 16GB flash drive. I don't see anywhere on gparted to reformat the file system of this device.
You have to select the drive from the drop-down menu in the top right corner.
Then right click on the drive and select format. You can experiment  with the options because nothing will happen until you click the "Apply" button on the menu bar.
Always double check that you have selected the correct drive!

---

