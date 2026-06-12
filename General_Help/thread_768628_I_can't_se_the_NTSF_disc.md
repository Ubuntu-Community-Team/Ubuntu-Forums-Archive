---
title: "I can't se the NTSF disc"
date: 2008-04-26
forum: General Help
---

### Post by MicroBoy on 2008-04-26
**I could see what is in the D disc but since I formated the PC I couldn't . Look what it shows:**

[IMG]http://img245.imageshack.us/img245/2163/screenshotfp6.png[/IMG]

---

### Post by ryanhaigh on 2008-04-26
This error message tells you the problem and how to fix it, if you have windows boot into that and if it is a removable device use the safely remove hardware option, if it is internal simply shutdown the computer cleanly and reboot into ubuntu. The drive should then be available again. 

If you don't have windows then you will have to use the force option AT YOUR OWN RISK! Instructions for this are contained in the error message. Ubuntu/ntfs-3g puts up this error message because your disk is marked as dirty (wasn't cleanly unmounted) and doesn't want to risk corrupting the filesystem.

---

### Post by MicroBoy on 2008-04-26
> **ryanhaigh said:**
> This error message tells you the problem and how to fix it, if you have windows boot into that and if it is a removable device **use the safely remove hardware option**, if it is internal simply shutdown the computer cleanly and reboot into ubuntu. The drive should then be available again. 

If you don't have windows then you will have to use the force option AT YOUR OWN RISK! Instructions for this are contained in the error message. Ubuntu/ntfs-3g puts up this error message because your disk is marked as dirty (wasn't cleanly unmounted) and doesn't want to risk corrupting the filesystem.How to use that in the BOLD FOnt?

---

### Post by ryanhaigh on 2008-04-26
Boot into windows,  plug the device in if it is not already then just use this: [http://www.iusb.edu/~sbwrite/thumb2.shtml](http://www.iusb.edu/~sbwrite/thumb2.shtml)

If your using vista the icon in the tray is a little different, just hover over them to find it.

---

### Post by MicroBoy on 2008-04-26
> **ryanhaigh said:**
> Boot into windows,  plug the device in if it is not already then just use this: [http://www.iusb.edu/~sbwrite/thumb2.shtml](http://www.iusb.edu/~sbwrite/thumb2.shtml)

If your using vista the icon in the tray is a little different, just hover over them to find it.[B]It doesn't show like that ok. In windows vista I can view the Ubuntu disk ok.
[/B]

---

### Post by daengbo on 2008-04-26
OK Microboy,

1) Is the disk internal or external?
  a) If it's an internal disk, just reboot into Windows, then shut down normally. That will fix the disk error.
  b) If it's an external disk, just reboot into Windows, insert the drive, then safely remove just like you would any other USB device. You can then use it in Ubuntu with no problem.

2) Did that work?
  a) "No, because I didn't want to reboot into Windows." Type "sudo mount -t ntfs-3g /dev/sda5 /media/Shenime -o force" and it will mount your drive, but you may lose some journalled information.
  b) "No, but I followed the directions and booted into Windows like you said." Type "sudo mount -t ntfs-3g /dev/sda5 /media/Shenime -o force" and it will mount your drive, but you may lose some journalled information.

I hope that works for you. Please read error messages (and friendly people's posts) carefully. Computers are technical pieces of equipment which can be easily damaged.

Daeng

p.s. It's too late, and Ican't handle any more of this.

---

### Post by MicroBoy on 2008-04-26
> **daengbo said:**
> OK Microboy,

**1) Is the disk internal or external?**
  a) If it's an internal disk, just reboot into Windows, then shut down normally. That will fix the disk error.
**  b) If it's an external disk, just reboot into Windows, insert the drive, then safely remove just like you would any other USB device. You can then use it in Ubuntu with no problem.**[B]I have to safely remove the Ubuntu disk ?
[I]
p.s. thnx for the reply[/I]
[/B]

---

### Post by daengbo on 2008-04-26
I think that I've been trolled.

---

### Post by ryanhaigh on 2008-04-26
If the disk Shenime is external, plug it in, note the drive letter that is assigned to the disk and then find the safely remove hardware icon in the system tray, left click on the safely remove hardware icon and then in the popup left click on the drive with the letter currenty used by the Shenime partition.

---

### Post by MicroBoy on 2008-04-27
**I upgraded from "Ubuntu 7.10" to "Ubuntu 8.04" now everything it's ok.**

---

