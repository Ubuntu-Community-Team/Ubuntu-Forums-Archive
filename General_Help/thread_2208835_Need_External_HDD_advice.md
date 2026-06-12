---
title: "Need External HDD advice"
date: 2014-03-02
forum: General Help
---

### Post by javajeff1 on 2014-03-02
I am thinking of keeping a backup of my stuff on an EXT4 formatted external drive.  It is an enclosure that has USB2 and eSata ports.  It is currently formatted as NTFS and was wondering if this would benefit me having EXT4 on it.  I only use Windows for some games and managing my iphone.  Any insight is appreciated.  I plan to use rsync.  I will connect the usb to my Linux laptop and the esata to my desktop that has both Linux and Windows.

---

### Post by CLCressman on 2014-03-02
I think that EXT4 has better Linux support if there ever is a problem. EXT4 will also keep your file ownerships and permissions.

---

### Post by javajeff1 on 2014-03-03
Thanks for the response.  I actually ended up converting it to ext 4, copied my home there, then swapped the drive with the one in my computer.  I now have a 1TB as my home, and my backup is a 500GB that mirrors my home.  I want to use rsync more often as I find it to be powerful, so Linux is the natural choice.  I actually have ext2explore on my Windows drive, so I can still copy stuff over.

---

### Post by mastablasta on 2014-03-04
how well does ext2explore work?

i used external data disk and decided to go with NTFS as i also have some Windows maschines at home. i probabyl wont' delte much form it so i don't expect any high fragmentation rate usually present in NTFS and other MS file systems.

---

### Post by javajeff1 on 2014-03-08
It does not install.  You have to right click on the executable file and run as administrator for it to see the ext4 partitions.  You can then save files to your Windows Partition.  It does not integrate into Windows and you cannot save anything to the ext4 partitions.  If you are fine with read only access using it's own explorer window, it does the trick.

---

