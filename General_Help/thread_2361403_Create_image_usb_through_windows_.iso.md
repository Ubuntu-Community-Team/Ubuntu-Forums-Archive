---
title: "Create image usb through windows .iso"
date: 2017-05-16
forum: General Help
---

### Post by sed_faster on 2017-05-16
Hello folks,

I use "Make startup disk" on Lubuntu to create a image usb through file .iso. Normally I use this software to ubuntu .iso. But this time I need create windows image usb. I am trying the same software with windows image but the software don't let me choose this image. Which software can I use to create a image usb to my windows .iso?

Thanks

---

### Post by RobGoss on 2017-05-16
Hello and welcome to the forum, You will have to follow the instructions on the MS website to create a bootable **USB** for Windows, I've just used this method and it works pretty well, they have a Windows tool that will allow you to create that USB....[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)

---

### Post by sed_faster on 2017-05-16
I know about this tool. I intend do this on linux environment! With iso windows SO create an usb on my Linux! How can I do this?

---

### Post by LastDino on 2017-05-17
I've never used Ubuntu Disk creator tool to create Win bootable usb. I use "Unetbootin" instead. It is (should) be available in software center.

There is also hard command prompt method to do this if I'm not wrong, but never tried it out.

---

### Post by RobGoss on 2017-05-17
I also tried using the disk writer, to create a bootable USB for windows and It would not work. I don't know what's so different about a Windows ISO file

---

### Post by kchesley on 2017-05-18
You could use wine to install Rufus USB installer. It's a windows application, but it should work.

---

### Post by sed_faster on 2017-05-18
Hooo, forget the wine :)
As @RobGoss says "I don't know what's so different about a Windows ISO file" Maybe the iso to windows is to special and tools on ubuntu don't good enough! -_- :)

Thanks guys :)

---

### Post by yancek on 2017-05-18
What's different is the filesystem and the structure of the system as well as a totally different method of booting.  Most of the tools mentioned are for creating bootable "Linxu" usbs with Rufus being the exception.  You don't need all of that, all you need to do is to loop mount the windows iso, copy it to your flash drive and create a boot entry to put in your Ubuntu grub.cfg file and boot the windows installer.

---

