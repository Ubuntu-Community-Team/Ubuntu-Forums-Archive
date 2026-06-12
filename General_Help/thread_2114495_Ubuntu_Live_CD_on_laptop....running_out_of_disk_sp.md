---
title: "Ubuntu Live CD on laptop....running out of disk space"
date: 2013-02-10
forum: General Help
---

### Post by greavette on 2013-02-10
Hello,

I'm running a Live CD of Ubuntu (Lucid) on a laptop and I've run out of disk space?  We haven't installed Ubuntu on the laptop so the live cd is running from memory.  The laptop has 3.5 GB of Ram in it.  I can't understand why it's running out of memory though? I was running ClamAV to scan for some folders on the laptops hard drive.  

I've tried removing some apps like gimp and openoffice from the live cd but with no space I get an error.

What could I do to not have this happen if I reload the live cd in this laptop?  

Thanks.

---

### Post by Cheesemill on 2013-02-10
When you run a Live CD it doesn't use the available space on the hard drive, the OS runs completely out of RAM.

The size of the additional virtual hard drive space available to Ubuntu is equal to half of your RAM. In your case your available hard drive space when running from a Live CD will be limited to around 1.8GB.

Uninstalling applications won't make any difference as these are stored on the CD, this space is unavailable for use for any other purpose.

---

### Post by grahammechanical on 2013-02-10
First of all, once Ubuntu is burnt to the CD then it is not possible to add or remove any thing from it. You cannot remove programs from a CD.

Second, What were you doing when you got the out of disk space message? Were you trying to save data to the CD? There might be space on the CD but it is effectively full. This is caused by the process of burning the ISO image to the CD.

Thirdly, is the Live session running out of disk space or is it running out of memory? You say both. This is confusing.

Remember, the OS and the applications are running in memory. The virus scan may be collecting lots of data. The application can only store it in RAM. This could be why the task is running out of memory.

ClamAV is not a Ubuntu default application. You would have had to download it and install it. That has not gone onto the CD but into memory.

I advise that you install Ubuntu to a USB memory stick with persistance. That will create an area on the USB stick where data/new programs can be stored. It might be a better way of running this test.

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

Regards.

---

### Post by greavette on 2013-02-10
Thank you for the responses.  

I realize that running the live cd is done all in ram...I was hoping that by removing some apps while running the live cd would free up some ram.

I would normally run ubuntu from a usb stick to alleviate these issues, but this is for a family member in another city who has a virus(es) on her computer and I wanted to quickly scan her laptop to copy her important files from the infected laptop to a usb stick.  It's worked quite well so far...I had her burn the ubuntu .iso to a cd.  I walked her through booting into the live cd environment, downloading teamviewer and allowing me to connect to her laptop so I can run some anitvirus scans on her folder of important files.  It was during the scan that I received the out of disk space message.

Thanks for the explanations everyone...very much appreciated.

---

