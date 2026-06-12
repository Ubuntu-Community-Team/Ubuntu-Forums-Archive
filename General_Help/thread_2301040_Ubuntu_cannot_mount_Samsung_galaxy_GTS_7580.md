---
title: "Ubuntu cannot mount Samsung galaxy GTS 7580"
date: 2015-10-30
forum: General Help
---

### Post by arthur24 on 2015-10-30
Normally I use my Galaxy S5 which Ubuntu 14.04 recognizes. But the phone is send for repair and I have a backup phone, the GTS 7580.
Ubuntu however tells me it cannot mount this phone so I cannot acces the folder structure from within ubuntu. I assume the open source drivers did not include this phone, i've done some searching for alternative drivers and solutions but I'm clueless to the right aproach here.

Can anybody help me?

---

### Post by coffeecat on 2015-10-30
You posted to the Ubuntu Phone sub-forum which is for help with Ubuntu phones - that is, phones running Ubuntu. Your problem is one of mounting an Android device in Ubuntu. Therefore,

*Thread moved to **General Help**.*

I've also slightly edited your thread title to make it clearer what the problem is.

I don't know much about this, but I do know that Ubuntu mounts my newer Samsung phone just fine, but not one running an older version of Android. So perhaps details of the versions of Android running on your two Samsung phones may be relevant. In the meantime this thread may give you some pointers before others offer help:

[http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)

---

### Post by slickymaster on 2015-10-30
With my Samsung Galaxy S3 GT-I9300 all I took was to install the **gmtp** package```
sudo apt-get install gmtp
```

---

### Post by arthur24 on 2015-10-30
My bad coffeecat,
Next time I take my time to post correctly.

@slickymaster

Problem still persists.

When installing GMTP the terminal also gave a error. 

```
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

Not sure if that means whether or not the installation of GMTP failed.

---

### Post by howefield on 2015-10-30
> **arthur24 said:**
> Not sure if that means whether or not the installation of GMTP failed.

Looks like a file that shouldn't be in that folder, try..

```
sudo mv /etc/apt/sources.list.d/getdeb.list.bck ~/Documents
```

which will move the file into your Documents folder in case you need it again, then check the install of GMTP.

---

### Post by slickymaster on 2015-10-30
> **howefield said:**
> Looks like a file that shouldn't be in that folder, try..

```
sudo mv /etc/apt/sources.list.d/getdeb.list.bck ~/Documents
```

which will move the file into your Documents folder in case you need it again, then check the install of GMTP.

+1

---

### Post by arthur24 on 2015-10-30
No more terminal errors. Terminal says GMTP is already the newest version.

Phone isn't recognized as of yet unfortunately despite GMTP being installed. It still says that it cannot mount the device.

---

### Post by slickymaster on 2015-10-30
Launch gmtp from your launcher or from a terminal window and see if it connects to your device. If not, then refresh things by unplugging your phone, rebooting the computer, then plugging in your phone again. Then, try to launch gMTP again.
Make sure that the phone is connected as "a Media Device" (MTP), if not click on the notification to change from Camera mode (PTP) to Media Device (MTP).

---

### Post by arthur24 on 2015-10-30
I think that might solve the problem slickymaster, but my problem has just expanded to the point where my phone itself doesn't recognize it being connected to a desktop. So I cannot connect the phone through MTP (or the secondary option) as my device somehow fails to recognize connection to the desktop. I didn't touch any setting on the smartphone prior to this new issue or on ubuntu itself apart from the steps supplied by you and Howfield. 

The problem might have expanded to the smartphone settings but I'm not sure about that, if true I'm clueless how and why. 
In the first instance my mobile device did showed a popup window that it found a connected computer when connected on the USB port where I could choose to connect through MTP among one of 2 options.

But all of a sudden my mobile phone doesn't recognize any connection to a computer and theirfore fails to give me the option to connect to the desktop.
The device is charging so there is a physical connection.
I'm not sure why this just happened, and if the problem is on the end of the smartphone or the Ubuntu operating system.

I restarted both the phone and ubuntu to make sure if that would solve the problem.

I've done a bit of googling to see if the problem is on the end of my smartphone.

I got to this, [http://forum.gsmhosting.com/vbb/f684/gt-s7580-pc-detection-failed-solved-1867586/](http://forum.gsmhosting.com/vbb/f684/gt-s7580-pc-detection-failed-solved-1867586/) but I got lost at step (8) posted by "Caoss" there to set UART to MODEM and cannot find such settings on the smartphone.
Hopefully it has nothing to do with my smartphone since this forum is about Ubuntu, not a Samsung galaxy smartphone.

---

### Post by slickymaster on 2015-10-30
That's odd indeed, but unfortunately I'm clueless about it. As I said in my previous post, all it took me was to install gmtp, launch it and connect the phone.

---

