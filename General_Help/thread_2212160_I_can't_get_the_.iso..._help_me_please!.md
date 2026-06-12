---
title: "I can't get the .iso... help me please!"
date: 2014-03-19
forum: General Help
---

### Post by anthony19 on 2014-03-19
Hello everyone! First post, and soon-to-be linux user.:D
I have gotten my build to post today, and I want to try Ubuntu 13.04 64bit desktop version. Since my new build doesn't have an optical drive, I want to install via flashdrive, installed from my laptop, which I am using now.
When I try to download the .iso image, it take ~25 min, and I had to restart it several times already because the only place it is allowing me to download to, after it has finished, is my (Fdrive), which is my dvd drive, and no other options. Not even desktop! Can someone shed some light on this for me please?

---

### Post by slooksterpsv on 2014-03-19
You will want to use 13.10 as 13.04 is no longer supported. You can download directly from Ubuntu.com or you can downaload it as a torrent (preferred method). After you have downloaded it you'll need the flash drive (at least 1GB in size) formatted as FAT32. 
TO FORMAT DO THE FOLLOWING:
**NOTE THIS WILL ERASE ANY CONTENTS ON THE FLASH DRIVE SO BE SURE TO BACKUP WHAT DATA YOU NEED FROM THE FLASH DRIVE**
You can click on Start -> Computer and right-click on your flash drive (MAKE SURE ITS YOUR FLASH DRIVE) and choose format. Make sure it says Fat32 at the top, and click format.

After that's done, download unetbootin from [http://unetbootin.sf.net/](http://unetbootin.sf.net/)
After you've downloaded that, run it: select Disk Image radio button, click on ... find the file you downloaded (usually in your Downloads folder) click on the drop down where it says Drive: at the bottom middle, choose your  USB drive. Click on OK

This will prepare the drive for you to boot from. After thats done, you'll need to restart and tell BIOS to boot from the USB drive. Depending on the computer there's a specific way to do it depending on your make/model of your computer.

---

### Post by anthony19 on 2014-03-19
Thanks for replying, but you don't really answer my problem. Let me rephrase. 
13.10 is the version I have been trying. I mistakenly typed .04.
My flashdrive is formatted correctly, and instead of that link, I am using pendrivelinux's Universal USB Installer.
The problem I have is: After i wait for the .iso to load at the bottom of my browser, the only option I have is the Windows Disk Image Burner. This pops up with ONLY the option of burning the .iso image to my dvd drive. Obviously not what I want to do. 
I have the loaded download right now, how do I save this to my desktop to put onto my flashdrive, to then install via pendrivelinux.?

---

### Post by Frogs Hair on 2014-03-19
Insert the drive, right click on the iso file and use the send to option move the iso. Read the instructions and see the link provided by [COLOR=#000000]slooksterpsv.

[/COLOR]http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows

---

### Post by Impavidus on 2014-03-19
Sound like your web browser automatically wants to open the .iso instead of save it to disk, and the only programs it knows to open it with is the disc burner. Can you right-click on the link to the .iso and then select "save link" or something like that? Else you may have to change the preferences of your browser so that it always asks, or use the torrent.

---

