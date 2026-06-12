---
title: "Creating a bootable Flash Drive"
date: 2013-08-27
forum: General Help
---

### Post by dbeb2 on 2013-08-27
So i have a netbook with windows that is like watching glue dry.  I am interesting in putting an opensource OS on it and what has intrigued me most is possibly looking at Android on it.  Although if it doesn't work well I will be heading to Ubuntu.

Anyways, the point is I used liveusb (i think that is what it is called, it is from Fedora but i used my own ISO i downloaded for Android) and the making of the flash drive seemed to have worked, and when I look at the files on the flash drive, there is a boot folder, but when I try to boot to it, it says there is no bootable partition.  This has happened before and I don't understand why because I thought these programs helped make them bootable.  What do I need to do to get my flash drive bootable?  I know it looks for it when turning the computer on.

Thanks!

---

### Post by oldfred on 2013-08-27
How did you install to the flash drive. 

       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

The download page also has instructions for both Windows & Linux.

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

      
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and still another


 If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by jlh68 on 2013-08-27
This method has always worked for me:   Ubuntu's "Startup Disk Creator"

> Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I currently have two netbooks and that is how I installed the OS on both (on is 32bit, the other is 64bit)

---

### Post by Cyril380 on 2013-08-27
Your Windows netbook can be helpful with this program:
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by dbeb2 on 2013-08-27
I gave up on Android and decided to go with Ubuntu 13.04.  I downloaded the ISO file from the Ubuntu website and then used unetbootin to create a bootable flash drive.  Now when I insert the Flash drive and then reboot, it says that it cannot find the operating system on the flash drive.  Is it possible that this flash drive is not bootable.  it is a sandisk cruzier 4gb.

---

### Post by Cyril380 on 2013-08-27
Ubuntu on a 4G ? No go.

---

### Post by dbeb2 on 2013-08-27
> **Cyril380 said:**
> Your Windows netbook can be helpful with this program:
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

I tried this as well and no luck.

The Flash drive is 4gb, if that is what you mean by 4G and it didn't work.  It still says "Missing Operating System"

---

### Post by community on 2013-08-27
First of all verify your downloaded ISO image with the hash values from Ubuntu website. Use UNetbootin to create a bootable falsh drive. It worked for me.

---

### Post by oldfred on 2013-08-27
The installer version fits on a 2 to 4GB flash drive. 

Only if doing a full install of Ubuntu to a flash drive do you need a minimum of 8GB. Lubuntu may fit on a smaller drive but better to have some room anyway.

---

### Post by dbeb2 on 2013-08-28
> **community said:**
> First of all verify your downloaded ISO image with the hash values from Ubuntu website. Use UNetbootin to create a bootable falsh drive. It worked for me.

Yeah I used the link above to get to download from the ubuntu website, and it still just says that it is missing the OS on the flash drive.  I do have a dual boot already with windows and Joli OS, but plan on getting rid of both of those.  Would that be doing anything?

---

### Post by oldfred on 2013-08-28
Either install is defective, installed incorrectly, or flash drive is defective.

Some flash drives and/or certain USB ports on some computers do not work. Try a different port.

       Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

