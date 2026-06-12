---
title: "enable hard drive."
date: 2007-06-30
forum: General Help
---

### Post by bilbobagins on 2007-06-30
After some recent help from 	
dreadlord_chris I have now got my second hard drive recognized by the system. My final question is how do i change permissions on this drive.file:///home/jonathan/Desktop/Screenshot-STORE%20Properties.png
file:///home/jonathan/Desktop/Screenshot-STORE%20Properties-1.png
 any suggestions from  more enlightened folk?

                                            regards jon
ps  hope screen shots come out ok

---

### Post by bilbobagins on 2007-06-30
Update screen shots haven't come out as hoped basically i want read write permissions for my second drive so that my photos and music can be stored on that drive. at the moment it is read only and i cant change permissions, via the permission tag on properties menu.

---

### Post by smo0th on 2007-06-30
use  sudo chown -R user:user /path/disk/ to change the ownership of your entire disk

and use sudo chmod -R 755 /path/disk/ to change the entire disk permissions

:popcorn:

---

### Post by bilbobagins on 2007-07-01
Thanks will give it a go. ta

---

### Post by DWirickSantaCruz on 2007-07-02
I am new to Linux/Ubuntu so please forgive any seamingly simplistic questions.  I know absolutely **nothing** about any of this (trying to become "windows"less).

Assuming the drive is mounted under /media as is the primary hard drive and we are talking about sdb1 (mount name "AltStorage") and the new drive is displayed on the desktop of the current user, then would the entry be something like...

[LIST=1]
[*]sudo chmod -R XXX /media/sdb1
[*]sudo chmod -R XXX /media/AltStorage
[*]sudo chmod -R XXX /[home directory]/media/sdb1
[*]sudo chmod -R XXX /[home directory]/media/AltStorage
[*]sudo chmod -R XXX /[home directory]/sdb1
[*]sudo chmod -R XXX /[home directory]/AltStorage
[/LIST]

...or something altogether different?

---

### Post by smo0th on 2007-07-03
OMG a multiple option quiz....

let's seee....

I vote for option 2!!!

my fault for not being clear the first time, when mounting a device, no matter what the label is, you use the device name which in this case is sdb1, device names are on the /dev dir (type ls /dev and there's the big list).

once mounted you change permissions by referring to the label so it would be like:

sudo chmod -R XXX /media/AltStorage/

:D

---

