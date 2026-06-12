---
title: "USB connection to cell phone not detected"
date: 2007-09-13
forum: General Help
---

### Post by johann_p on 2007-09-13
I would like to access the memory card on my SonyEricsson W800i over the USB connection cable so that I can transfer MP3s to it.
I would also like to synchronize contacts and organizer stuff over USB.

However, when I connect the cable, nothing visible happens on the Ubuntu Feisty GNOME desktop. 

When I do lsusb there is a line "Bus 005 Device 006: ID 0fce:d028 Sony Ericsson Mobile Communications AB " but that's all.

How can one mount the memory card of a W800i as a disk and how can one synchornize data over the USB cable?

And why is there no visual indication that some USB hardware has been connected (I have had similar problems with other USB devices, e.g. a GPS device)?

---

### Post by leonidas666 on 2007-09-13
I don't know the specifics of your phone, but are you sure that the phone works as a USB Mass Storage device? If it works in Windows without a special driver, it  should also work in linux without extra driver. If you need a extra driver for windows chances are that the whole issue is a bit more complicated.

---

### Post by w4ett on 2007-09-13
It seems that the USB worked in Dapper (From what I've read---no first hand knowledge)...but here are some threads with posters who have the same phone.  iIt might help to PM them and see if they might have an answer that they can post here for you.

[http://ubuntuforums.org/showthread.php?t=549398](http://ubuntuforums.org/showthread.php?t=549398)
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/27687](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/27687)
[http://ubuntuforums.org/showthread.php?p=3358298](http://ubuntuforums.org/showthread.php?p=3358298)
[http://ubuntuforums.org/showthread.php?p=1862667](http://ubuntuforums.org/showthread.php?p=1862667)

---

### Post by johann_p on 2007-09-15
Nothing yet. 

Apart from not working, what I find odd is that Ubuntu does not show ANYTHING when pluging the device in. A message like "unknown device connected, cant help you with this one" or similar would be better.

This is what frustrates me the most with Linux: more and more devices are designed to get connected with your PC and most of them either do not work at all, or work only in a totally limited way or with some cryptic command-line tool.

---

### Post by fragos on 2007-09-15
Have you tried the bitpim package.  It may support your phone model.

---

