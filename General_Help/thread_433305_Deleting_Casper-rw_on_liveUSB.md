---
title: "Deleting Casper-rw on liveUSB"
date: 2007-05-04
forum: General Help
---

### Post by dfarce on 2007-05-04
I have severily screwed up my persistent usb installation and was wondering if reformatting the casper-rw partition ONLY would allow me to start from scratch. It was a huge hassle getting the boot partition to work so I would not reformat it only the -rw one. I am using a 6.10 installation for the "basis" for the liveUSB. Would reformatting the casper-rw partition allow me to starty from scratch without having to redo the installation (if thats what you would call it)?

---

### Post by jerrylamos on 2007-05-04
For CD Live, if you want to start over, easiest thing is to re-format casper-rw.  Careful not to reformat your hard drive!

Boot without specifying "persistent".   Do

df -h 

to make sure where your USB drive is.

sudu umount /dev/sdb1

or whereever it is.

sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sdb1

(make certain about the /dev/sdb1 or sdba1 or whatever is your USB and not your hard drive!!)

Note CD Live works on Edgy 6.10 and Dapper 6.06 but not Feisty 7.04 yet.  Don't hold your breath.

Now you could just erase all the files on casper-rw except lost+found however deleting directories on Linux can be tedious.

Cheers, Jerry

p.s. Other Linux's have menus to set up the USB.  I really wish Ubuntu did also.

---

### Post by dcstar on 2007-05-04
> **dfarce said:**
> I have severily screwed up my persistent usb installation and was wondering if reformatting the casper-rw partition ONLY would allow me to start from scratch. It was a huge hassle getting the boot partition to work so I would not reformat it only the -rw one. I am using a 6.10 installation for the "basis" for the liveUSB. Would reformatting the casper-rw partition allow me to starty from scratch without having to redo the installation (if thats what you would call it)?

Yep - just delete the contents and reboot (did the same thing myself a couple of weeks ago after mucking up the permissions).

---

### Post by dfarce on 2007-05-06
Reformatted, it all works now. All I need to do is set up the modem...

---

### Post by EagleRock on 2007-06-19
Never mind...I missed the last post...

---

