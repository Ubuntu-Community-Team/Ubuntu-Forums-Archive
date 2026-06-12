---
title: "usb-imagewriter"
date: 2015-12-10
forum: General Help
---

### Post by simon114 on 2015-12-10
Good Afternoon,

I would like to know if there is a way to extract an *.img to a usb with something like usb-imagewriter

Apparently usb-imagewriter stopped after version 12 of Ubuntu and I am running 14.04 , Is there a new version somewhere, Where would I look, Also what is is called...Thank-you for Ubuntu a lifesaver and a fresh alternative to Windows. I changed to Ubuntu almost 4 months ago and haven’t looked back. Thank-you

---

### Post by sudodus on 2015-12-10
Yes, you can use mkusb. It can write image files, compressed image files and also iso files to a mass storage device (for example a USB drive).

See this link: [mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by simon114 on 2015-12-10
> **sudodus said:**
> Yes, you can use mkusb. It can write image files, compressed image files and also iso files to a mass storage device (for example a USB drive).

See this link: [mkusb]("https://help.ubuntu.com/community/mkusb")


Yep That Has done it Thank-you, One note I would add is that it does not detect the *.img file as such, but left within an *.img.gz it works. Thank-you for the help

---

### Post by coldraven on 2015-12-10
AFAIR in 14.04 you can just right click an image file and select "Burn Image with Disk utility" or words to that effect.

---

### Post by sudodus on 2015-12-10
> **simon114 said:**
> Yep That Has done it Thank-you, One note I would add is that it does not detect the *.img file as such, but left within an *.img.gz it works. Thank-you for the help

I'm glad it worked for you :-)

Please explain how your *.img file was not found. mkusb finds such files for me. But it does not find .IMG files. That might be called a bug, I'll try to fix it :-)

---

### Post by simon114 on 2015-12-13
Hi sudodus,

The image file is from [URL="http://releases.openelec.tv/OpenELEC-Generic.x86_64-6.0.0.img.gz"]http://releases.openelec.tv/OpenELEC-Generic.x86_64-6.0.0.img.gz

[/URL]I extracted the *.img file from the *.img.gz into my downloads folder.

Then opened up mkusb and tried to find the previously extracted image file and it would come up with a blank window where the file should be
So I downloaded it again, and directed mkusb to the img.gz and it worked.

Thanks for the advice once again.

---

