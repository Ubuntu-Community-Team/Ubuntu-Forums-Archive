---
title: "Gnome Disks"
date: 2013-04-15
forum: General Help
---

### Post by un-original on 2013-04-15
Hey everbody, big problem here and I would be glad if someone could help!  I was in a middle of an ATA secure erase through the disks utility when  my laptop froze and had to do a hard reboot. When I turned the computer  on it asks for a password to unlock the hdd. However, I did not set a  password in the process, so now I can't turn my computer on while the  hard drive is in the computer! Thank goodness for live discs lol!

Does anybody know how to rectify this?

P.S Not sure where to post this so I will put it in a few different catagories.

---

### Post by grahammechanical on 2013-04-15
As you sure it is not asking for your normal user password? I hope you do not intend to post this same question in more than one section. That is bad manners, at the least.

How many hard disks in this laptop? If there is only one and your are erasing the disk, then you do not have an OS to boot into. Where were you running this erase program from? Start again.

Regards.

---

### Post by un-original on 2013-04-15
Thanks for your response! I ran the program from a live usb with only one hard drrive. At start up, if I have the hard drive in, it asks for a password to unclock the hdd/sdd (sorry cant remember the exact phrase). I cant even enter the bios if I have a hard drive in. 

Sorry for posting in multiple sections, pretty inexperianced at this. Thanks for letting me know though, I will not do this again.

Also, I tried putting the hard drive back into the bay once I had booted into a live cd but it was not reconised. Not sure if this is to do with it being locked or rather you just cant do thus though. I was going to try and use hdparm to see if I get anything usefull, that doesn't seem to be possile though.

---

### Post by grahammechanical on 2013-04-15
I think, but I am not sure, that the Ubuntu live USB has a user name of ubuntu and for the password just press enter. I have found this

> [COLOR=#333333][FONT=Ubuntu]Sometimes a LiveCD might ask you for a user-name or password. Just leave these blank and press enter (or allow it to time-out).[/FONT][/COLOR]

Scroll down to the heading Troubles with the Live CD logging in

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

That may be old information. Later information seems to say username: ubuntu and the password is left blank.

regards.

---

### Post by tgalati4 on 2013-04-15
It's possible that the hard disk stored the password on the 2nd or 3rd sector of the disk.  The first sector being the Master Boot Record.  Since you did a low-level wipe, then you wiped out that password (even if it was blank) and the disk's firmware is now looking for it.  You might have to resort to finding a Windows machine and go through the manufacturer's installation disk and reinstall the disk and set the password so that it gets rewritten.  It's also possible that your laptop's BIOS has the disk password set.  If that is the case, then disable all passwords in the BIOS.

---

### Post by Cheesemill on 2013-04-16
Try xxxx as the password :)

---

### Post by un-original on 2013-04-16
Hey guys, tried all the suggestions, though nothing seems to be working. I did find a program called mhdd which should allow low levell operations on a hardisk even when the bios has not detected it though. However, my propblem is now that I can not write the cd while using a live usb. Could someone tell me a potential way of doing this. Thanks in advance.

---

