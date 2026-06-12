---
title: "How does Ubuntu 13.04 mount iso automatically in /media on single click?"
date: 2013-08-26
forum: General Help
---

### Post by eshant_engineer on 2013-08-26
How does Ubuntu 13.04 mount iso automatically in /media on single click? 
I want to know the package(s) used for this functionality.

Thanks You

---

### Post by oldfred on 2013-08-26
Do you want to mount it just to look at it and inspect files or use an ISO directly to install? 

I use Archive Manager to verify I have the correct details in my grub boot stanza. 

And I use grub2's loopmount to directly mount an ISO as a working live installer.

But normally users install ISO by extracting it into a lot of files and creating correct bootable disk, not copying an ISO to a flash drive. 

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
      
 [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick
      [/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

    [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]



[/URL]

---

### Post by sandyd on 2013-08-26
Moved to general help

---

### Post by deadflowr on 2013-08-26
HAL/udev., which allow connecting to external devices.
Which are built into the functions of the file manager, in which case is nautilus.
The ability to automount the mediums in media comes from the user belonging to the group plugdev.
A user who tries to mount external media who does not belong to plugdev, will need extra privileges to do so.

---

### Post by crazymonkey05 on 2013-08-26
i believe the program that does this is nautilus and that program is default archive manger for all supported releases of ubuntu right now. so if you want it on a different OS here are the ppa's for all the programs associated with nautilus [https://launchpad.net/ubuntu/+ppas?name_filter=nautilus](https://launchpad.net/ubuntu/+ppas?name_filter=nautilus)

---

### Post by eshant_engineer on 2013-08-27
Thank a lot all of you for your inputs...:)

---

