---
title: "[SOLVED] Ubuntu and XP on same computer?"
date: 2008-02-27
forum: General Help
---

### Post by BillyMax on 2008-02-27
Can you install xp and ubuntu on the same computer and they both are happy about it?

---

### Post by Joeb454 on 2008-02-27
As long as there is free space somewhere on your drive (you should make some in XP first) then the Ubuntu installer should sort it out for you :)

Check out [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by fedex1993 on 2008-02-27
Yes you can it is called a dual boot. here is a link to a guide [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by Nameless_one on 2008-02-27
Yes, but on different partitions. Also, you have to install a bootloader like grub, and configure it to point at both OSes. Then, everytime you start your PC, there will be a menu with the different OSes, and you will be able to choose which to load every time. 

These might prove helpful:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Also, try searching the Tutorials & Tips subforum for 'dual boot windows ubuntu' or something similar.

EDIT: psychocats is popular :D an damn, I'm too slow! I need to write less and more compactly :P

---

### Post by stchman on 2008-02-27
> **BillyMax said:**
> Can you install xp and ubuntu on the same computer and they both are happy about it?

I have 2 PCs dual booting XP and Ubuntu.

---

### Post by Gannon8 on 2008-02-27
Yes, you can. Doing it involves resizing the partition on the hard drive. A partition is what the OS looks for in storage devices, so you can assign two drive letters for one USB jump drive, for example.
If you don't understand what I'm saying, check your library for a book called Ubuntu Linux for Dummies. It tells you how. :)

'Kay, so first you might want to back up your drive, as well as run the dist defragmenter and cleaner. After that, boot up Ubuntu from the cd and select Administration -> Gnome Partition Editor. Select the NTFS (or FAT, if you have 95, 98, or maybe 2000) partition, and click on the Resize/Move button. Drag the little black arrow to resize the windows partition to make room for the Ubuntu partition. The blank space needs to be at least 3GB. Now you need to format the new partition. Click on the space you just made on the list on the bottom. Now on the toolbar, click Partition -> New. Make sure there is no bytes preceding and following, then click the Add button. Click the apply button twice. Now you have another section of your hard drive just for your Ubuntu OS!

Ok, so did you understand me? :mrgreen:

---

