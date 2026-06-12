---
title: "Computer unusable with Hardy: any suggestions?"
date: 2008-05-06
forum: General Help
---

### Post by acl123 on 2008-05-06
Well I've waited a week for updates to come through after upgrading to Hardy, but my computer is still basically unusable. Eventually everything just locks up and I have to hard reset. This can't be good for my hard drive - I don't want to ruin it. Its no good having a free operating system if it ruins your hardware and you have to pay for a new one.

I need to backup my computer somehow, but I can't keep Ubuntu alive long enough to copy files on to an external hard drive or over the network to my laptop.

What do you guys think I should do?

---

### Post by shakabra on 2008-05-06
You should use the Ubuntu Live CD to access your files for backup.  What exactly are you doing when the computer locks up?  Do you use any restricted drivers?  Also you should never use the power button to hard reset.  Try CTRL+ALT+BCKSPC first to log out of the current   
session.  If that doesn't work open a virtual terminal with CTRL+ALT+Fn (n being any Fkey 1-6) once inside the virt. terminal type "shutdown now -r" to reboot the system.  If neither of those work hold CTRL+ALT+PrtSc and slowly type REISUB, this will reboot your system.

---

### Post by acl123 on 2008-05-06
Whilst I can sometimes hit Ctrl-Alt-Backspace and drop into a new session, once there, everything is still locked up. If I try and login, it allows me to type my username but it hangs before it even asks for my password. Sometimes I can hit Ctrl-Alt-Delete at this point and reset the computer, but usually not.

Whilst I'm stuck in the non-graphical session, error messages gradually start being displayed. Things like this:
> 
EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal<6>sd 1:0:0:0 [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK, SUGGEST_OK
.
.
.
EXT3-fs error (device sda1): ext3_find_entry: reading directory #590954 offset 0
.
.
.
[124.058330] ata 2.00: revalidation failed (errno=-5)
.
.
.
EXT3=fs error (device sda1):ext3_get_inode_loc: unable to read inode block - inode=8618454, block = 17235984
.
.
.
[224.871822] Buffer I/O Error on device sda1, logical block 46953927
.
.
.
ata 2.00:Status {DRDY}
ata 2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen


I'm not sure whether I have restricted devices - where has this option gone in the menus? I have an Nvidia graphics card which I had a hell of a time getting to work in Gutsy, but eventually got it working. When I started using Hardy I couldn't get the resolution right so I overwrote the new /etc/X11/xorg.conf with my old Gutsy one.

I'm very worried about the health of my computer. I can't keep cutting the power on it like this. The computer has even started freezing on the manufacturer's initial screen which makes me think that I'm completely frying the thing.

I will try using the Ubuntu Live CD to retrieve my files. Thanks.

---

