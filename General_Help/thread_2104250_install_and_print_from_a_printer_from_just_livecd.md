---
title: "install and print from a printer from just livecd?"
date: 2013-01-12
forum: General Help
---

### Post by Not install on 2013-01-12
hi 

is it possible to  install and print from a printer from just live cd? With out actually installing.  Ubuntu?

---

### Post by sudodus on 2013-01-12
Yes, you can install programs (including printer drivers) in a live session. But it will disappear when you shut down or reboot the computer.

Another option is to make a persistent live USB drive. Such a drive contains a file or partition with a file system, and can store files that you have created (user files as well as installed programs). The USB drive can be a flash pendrive, which makes it convenient.

You can use either ***Startup disk creator*** (comes with Ubuntu), ***Unetbootin*** or several other tools to create a live USB drive with Ubuntu.

---

### Post by Not install on 2013-01-12
> **sudodus said:**
> Yes, you can install programs (including printer drivers) in a live session. But it will disappear when you shut down or reboot the computer.

Another option is to make a persistent live USB drive. Such a drive contains a file or partition with a file system, and can store files that you have created (user files as well as installed programs). The USB drive can be a flash pendrive, which makes it convenient.

You can use either ***Startup disk creator*** (comes with Ubuntu), ***Unetbootin*** or several other tools to create a live USB drive with Ubuntu.



great thankful how do I make hp LaserJet 1000 work with ubuntu  live cd please. Is it just a plug and play in ubuntu or do I download stuff?. I have ubuntu on a 700mb disc can I use my printer and still have  room on the cd to download software for that printer that's required by ubuntu . Please and please which software I need my printer is this one please I have HP LaserJet 1000 I see something for linux on page url below will it work that one for linux that's on page for ubuntu or ubuntu  one different?

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=45675&amp;lang=en&amp;cc=us&amp;taskId=135&amp;prodTypeId=18972&amp;prodSeriesId=45674](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=45675&amp;lang=en&amp;cc=us&amp;taskId=135&amp;prodTypeId=18972&amp;prodSeriesId=45674)


do I use the one that say linux on the HP page please to use with live cd please of ubuntu 700mb I burned it to

---

### Post by sudodus on 2013-01-12
You cannot store anything new on the live CD. It is read-only, and everything you install is only kept on a ram-drive, which is wiped at reboot or shut-down.

To store the printer installation you need a persistent live USB drive.

I have no HP printer, but it is common brand, and I have read about linux drivers for it.

***I suggest that you start a new thread with an appropriate title to attract people who know about drivers for your printer.***

We can continue the discussion here about how to make a persistent live USB drive (if you need persistence).

There is even the option to make a regular installation of Ubuntu to a USB drive. It will work 'exactly' like an internal drive, except that it will be slower because USB is slower than SATA. (But with USB 3 it will be much faster than with USB 2.)

---

### Post by Not install on 2013-01-12
> **sudodus said:**
> You cannot store anything new on the live CD. It is read-only, and everything you install is only kept on a ram-drive, which is wiped at reboot or shut-down.

To store the printer installation you need a persistent live USB drive.

I have no HP printer, but it is common brand, and I have read about linux drivers for it.

***I suggest that you start a new thread with an appropriate title to attract people who know about drivers for your printer.***

We can continue the discussion here about how to make a persistent live USB drive (if you need persistence).

There is even the option to make a regular installation of Ubuntu to a USB drive. It will work 'exactly' like an internal drive, except that it will be slower because USB is slower than SATA. (But with USB 3 it will be much faster than with USB 2.)

yes please how do I make a persistent USB what size it need to be 2gb please I'm starting new topic for drivers

I have USB 1.1 or 2.0

---

### Post by Mark Phelps on 2013-01-12
Details are in the thread linked below:

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by Not install on 2013-01-12
> **Mark Phelps said:**
> Details are in the thread linked below:

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")


is that a normal USB injury or a persistent one I don't see persistent one in the sub hoardings


is this one for persistant [http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)



I'm understand this tutorial a bit better but it old has desktop i386  do we still use this version today?
I have 2gb USB 1.1


thankful all that's helping me so far

---

### Post by deadflowr on 2013-01-12
[https://help.ubuntu.com/community/LiveCD/Persistence?highlight=%28%5CbCategoryLive%5Cb%29]("https://help.ubuntu.com/community/LiveCD/Persistence?highlight=%28%5CbCategoryLive%5Cb%29")

For persistence.

---

### Post by Not install on 2013-01-12
> **deadflowr said:**
> [https://help.ubuntu.com/community/LiveCD/Persistence?highlight=%28%5CbCategoryLive%5Cb%29]("https://help.ubuntu.com/community/LiveCD/Persistence?highlight=%28%5CbCategoryLive%5Cb%29")

For persistence.



thankful but can I use this one [http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)


I find easy to follow can I still use i386 ubuntu desktop or shall I select I different version I want it to use with LaserJet 1000 HP printer

---

### Post by Not install on 2013-01-12
Topic can be marked as solved 

Many thanks all

---

### Post by sudodus on 2013-01-12
> **Not install said:**
> Topic can be marked as solved 

Many thanks all
Congratulation :KS

Did you use USB 1.1? I think it will be much faster with USB 2 :-)

And in any case, be patient! Let the system write all the changes to the storage on the USB pendrive at shutdown or reboot. Do not disconnect the pendrive until this writing has finished. Otherwise the storage will be corrupted and you have to make a new storage (reformat the file system of the storage space) and reinstall your printer driver etc.

---

### Post by Not install on 2013-01-13
> **sudodus said:**
> Congratulation :KS

Did you use USB 1.1? I think it will be much faster with USB 2 :-)

And in any case, be patient! Let the system write all the changes to the storage on the USB pendrive at shutdown or reboot. Do not disconnect the pendrive until this writing has finished. Otherwise the storage will be corrupted and you have to make a new storage (reformat the file system of the storage space) and reinstall your printer driver etc.


Thankyou for your advice regarding writing changes to USB at shutdown btw I used 1.1 usb

---

