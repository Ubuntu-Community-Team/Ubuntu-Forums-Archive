---
title: "Startup Disk Creator FAIL"
date: 2016-08-29
forum: General Help
---

### Post by cathect2 on 2016-08-29
I have an ISO (FreeNAS) that I'm trying to put on a bootable USB. Thought I'd use Ubuntu 16.04 to do this. The utility recognizes the USB that I want to use, but when I select the .iso file . . . nothing happens. When I select the .iso, click it, it just seems as if nothing happens and there is nothing selected as the source disk image. 

Uh, help? Is there some bug with this?

---

### Post by RobGoss on 2016-08-29
I use** startup disk creator **all the time and it works great,You can also go to your download folder were you have your **ISO** file and _right click_ on that ISO file, choose from the list of programs to write that ISO to your USB drive. I always use **disk image writer **which does the same as the startup disk creator.

Hope this helps

---

### Post by cathect2 on 2016-08-30
@RobGoss You are using Ubuntu 16.04? 

If I try to create a bootable USB using the right click method, I get the following message: 

> Do you really want to keep the current extension for the disc image name? If you choose to keep it, programs may not be able to recognize the file type properly.

---

### Post by RobGoss on 2016-08-30
Yes that's correct I have 16.04 installed. Do you not see any other options to burn that ISO file?

You can also search the Ubuntu center for images writer tool there should be one listed 

You might give this one a try
[https://apps.ubuntu.com/cat/applications/precise/usb-imagewriter/]("https://apps.ubuntu.com/cat/applications/precise/usb-imagewriter/")

This YouTube video might also help you
[https://youtu.be/aVmz-hyzL4E]("https://youtu.be/aVmz-hyzL4E")

---

### Post by cathect2 on 2016-08-30
Can you do the following:

1. Download the FreeNAS OS here: [http://www.freenas.org/download/](http://www.freenas.org/download/)
2. Open Startup Disk Creator.
3. Click "Other" to select the FreeNAS .iso file.

At this point, Startup Disk Creator fails to select the .iso file. Nothing happens. Am I alone in this?

---

### Post by RobGoss on 2016-08-30
It might be something wrong with that ISO file I would try a Ubuntu iso file and see if that works

---

### Post by cathect2 on 2016-08-30
Fails for all iso.

---

### Post by RobGoss on 2016-09-04
I'm assuming you're downloading the Ubuntu ISO file from their website correct?

---

### Post by him610 on 2016-09-04
Down in the Tutorials, there is one by Sudodus (of these forums) on how to download, install, and use ***mkusb***. Included with it is some excellent documentation, Recommend you check it out and use it to install distros on a USB stick. I use it exclusively - it just works.

FWIW: I have been using Freenas 0.68 on an Atom-powered system for five or six years. Bootable Freenas is installed on a 250MB USB stick. The only time it has gone down was during a power outage. You might consider looking into open source ***nas4free*** since freenas has gone commercial.

---

