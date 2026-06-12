---
title: "Can't boot from DVD"
date: 2014-12-25
forum: General Help
---

### Post by derek28 on 2014-12-25
My girlfriend's grandma has a very old Dell desktop with Windows XP. I couldn't figure what the model was, but it's old. 
The boot order menu only has the Hard Drive and 'IDE CD-Rom device'. I couldn't fit i386 lubuntu onto a regular CD. The iso was like 750MB, so I burned it onto a DVD+R.
I put the DVD+R in, enabled booting from CD. When I tried to boot, nothing happened at all. It has two cd slots and I tried both. 

Do I need a driver or what? What am I doing wrong? Could this be an impossible task I've been given?

Please help.

Thanks
-Derek

---

### Post by westie457 on 2014-12-25
Chances are you only have CD-ROM drives in the box. These cannot read DVDs.

In the hard drive section of the BIOS is USB hard disk (or something similar) mentioned to use as a bootting device?

---

### Post by derek28 on 2014-12-25
I'll go check in a second. It wasn't in the boot menu at all though.

---

### Post by derek28 on 2014-12-25
Clicked 'hard-disk drive sequence' it lists 'System BIOS boot devices' and 'USB device (not installed)'.

What am I lookin at here boss?

---

### Post by yancek on 2014-12-25
Most computers will show a Boot tab in the BIOS and under that an option for boot priority.  If you see usb there, you might be able to boot with a usb/flash drive but I doubt that you will have that.  It may just mean you can attach and use an external drive connected by usb but not necessarily boot off it.

---

### Post by mörgæs on 2014-12-26
Sometimes a new BIOS is all it takes. Which computer and which BIOS are you using?

---

### Post by coldraven on 2014-12-26
In the meantime why not install Lubuntu? It will fit onto a regular CD and will work better than Unity on a low spec machine. 
After it is working you could always install the Unity desktop and switch between them at the login screen.

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

Or burn the Ubuntu minimal install disc and use that as a basis for a full install

[URL="https://help.ubuntu.com/community/Installation/MinimalCD"]https://help.ubuntu.com/community/Installation/MinimalCD


[/URL]

---

### Post by Bucky Ball on 2014-12-26
Or you could try creating a USB and booting from that using [Universal USB installer. ]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

---

### Post by coldraven on 2014-12-26
Tip: Before you delete XP you should do a couple of things.
If you are thinking of updating the BIOS then it will be easier doing it in Windows.
Don't forget to export all the bookmarks from the browser and save them to an external drive.
If the browser contains username and passwords for various web-sites don't forget to save those too. I usually just take  screen-shots and copy them to an external drive.
It's not a very secure way of doing it but it saves a lot of hassle.

---

