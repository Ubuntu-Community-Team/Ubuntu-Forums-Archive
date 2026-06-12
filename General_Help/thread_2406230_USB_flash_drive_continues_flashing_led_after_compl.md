---
title: "USB flash drive continues flashing led after completion. Unmount problem"
date: 2018-11-17
forum: General Help
---

### Post by candtalan on 2018-11-17
Ubuntu 16.04 and 18.04, USB stick 8GB, marked BESTR*NNER. May be item hardware, brand specific problem(?)
I became aware of the problem when creating a startup pen drive with this item. It failed to work as a live drive. A 'disk check' in the live usb menu showed errors in one file. Was quite repeatable after re-creation. Another usb item different brand, all ok as normal. I compared the two USBs viewing the files, folders  (nautilus) broad eyeball method, - both looked the same, same number of items, files, and folders indicated. 
odd?
I Formatted the bad item again fat32 (using ubuntu Discs utility), used a single partition. Tested by copy paste 50 files onto it. No problem.
The option offered in nautilus was only 'eject' (safely remove was not shown) and before using that option I could see the item's led was on, but not flashing (=no activity).
After use of the Eject facility, the led continuously flashed (!) & did not stop. did not stop on logout. Only stopped on shutdown.
(I had tried sync, had tried empty caches, no effect)
I repeated the experiments for eject, etc:
Note that the (nautilus) 'remove safely' was not offered, only eject, which repeatedly caused the led to endlessly flash, even though the Notification (top of display) popped up as  'item can be safely removed' etc
Finally tried using the umount command which [edit] unmounted without causing the continuous flashing!
my command:
sudo umount -t fat32 /media/myname/failedboot
(where the problem drive by now was named by me as failedboot for want of anything better)

Conclusion: Using this usb drive, something is responding incorrectly to the situation around unmount and/or eject

I have a dozen of these little devil usb drives, and I presumably need to keep the umount command handy. 
I note that I seem not to cause any damage by removing the flashing usb for ordinary files transfer (having given sufficient time) but when creating a live usb drive something is incomplete. 
I have not yet tried creating a live usb drive and trying to finally use the umount command yet, but it is a slight comfort to find something at least repeatable.

---

### Post by HermanAB on 2018-11-18
Note that copying a large ISO file to a USB thingy can take a very long time.

There are various ways to check whether the disk is still busy writing.  The dd command can be queried with kill, while the cat command will not return until it is finished.  The top command will show which processes are consuming CPU and are therefore still busy.

I prefer to make an Ubuntu live install disk with cat:
```
$ sudo cat file.iso > /dev/sdb

```
Followed by good measure with a sync.

This is the simplest method.

BTW, do use the dmesg command to see what is the real device name of the USB widget after plugging it in and for good measure do it a few times.  It will *never* be sda!  Rather be safe than sorry.

---

### Post by candtalan on 2018-11-18
Thank you! very useful.
I will use those commands. Large stuff - yes am aware, thanks. In this flashing case I left it for hours on one occasion. 
I would say though that in this particular case, after use of the only option Nautilus offered, Eject, the drive is indicated by nautilus as _not_ being mounted then, and a notification soon appears ' Its now safe to remove device' etc. Also when running gparted then, it is not possible to show the drive at all, it is not found, and a refresh devices does not show it either. I suspect it is a rogue hardware design or problem which reports itself differently to a good usb.
I note that when a CD/DVD is mounted, only the Eject option is shown in Nautilus, just like this usb. The other brand usb reports, is shown, in nautilus for  'safely remove' as one would expect, for a usb.  The two situations leading to either  Eject, or Safely Remove options presumably use differing commands. 
On this drive, normal USB actions work ok it seems, copy paste etc, and no (apparent) damage is done when removing the drive after a time, still flashing. However when the drive is used for a startup disc (live dvd action) - that is when problem is seen with a failed function in use, repeatable. It is as if the dvd emulation is not handled well or is misinterpreted etc.
Thanks again, the commands will be very useful.

---

### Post by HermanAB on 2018-11-18
The trouble with most GUI programs is that they mask the error codes, so they are only good when everything works as expected and are of little/no use when things are wobbly. So I use the GUI for simple stuff and when I need to do a low level operation (or a massive operation involving tens of thousands of files), I switch to a command shell.

---

