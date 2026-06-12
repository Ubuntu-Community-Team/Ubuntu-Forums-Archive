---
title: "Phone is recongized in Ubuntu but cannot be found in dev/sdb"
date: 2016-02-15
forum: General Help
---

### Post by shadowfire452 on 2016-02-15
So I have a LG v10 and when I plug it in to Ubuntu 12.02 it is recognized and Ubuntu says its mounted but when I run ls /dev/sd* it's not listed. It is found under lsusb but i need the device name. I also can't view any files on the device, I get the error 

"Sorry, could not display all the contents of "LGE Android Phone": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I've tried several USB cables but they all give the same result. also, my end goal here is to work on a bricked G4 so using adb or anything like that isn't going to help, I need to be able to see the device in /dev/sd* 

Any thoughts?

Edit: after waiting for a while I can view the files on the phone but it's still not detected under /dev/sd*

Edit 2: running gdisk -l /dev/bus/usb/xxx/xxx for the phones bus and ID returns an error stating that the device is a character device

---

### Post by mcduck on 2016-02-17
It's a MTP device, not a block device, so as far as I know it's not going to be listed as /dev/sd*.

What's stopping you from using ADB? If you can power on the device (which you need to be able to do to connect to it anyway) you should be able to boot it to recovery mode, which should give you access to both ADB and mounting the device...

---

