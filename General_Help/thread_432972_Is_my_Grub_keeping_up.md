---
title: "Is my Grub keeping up?"
date: 2007-05-04
forum: General Help
---

### Post by Jimpdx on 2007-05-04
When my Grub screen appears during the boot-up, it lists the kernal as 2.6.15, even though I have the current kernal 2.6.20 installed on 7.04.  So which kernal is actually booting?  Do I need to be manually updating or editing something to get the newest kernal running?

Thanks, as always!

---

### Post by Steven_B on 2007-05-04
If you haven't uninstalled the 2.6.15 kernel, you're probably still running it.  Type "uname -r" in  a terminal to see what kernel you are running.
EDIT:
To update the list list of kernels to boot, you should be able to type "sudo update-grub".

You can also manually edit your /boot/grub/menu.lst file.  Scroll down to the list of kernels, make a copy of the two 2.6.15 sections (normal and recovery), and then change the copies to say 2.6.20.

---

### Post by tgm4883 on 2007-05-04
do 
```
uname -r
```

in a terminal and that will tell you your kernel

---

### Post by Jimpdx on 2007-05-04
Thank you for the responses.  I am indeed running 2.6.15.  If I do uninstall this old kernal, will Grub automatically seek and find a newer kernal, or do I need to to instruct it to do so?  I've looked at the Grub file in gedit, but I haven't been brave enough to change anything!  Any advice is greatly appreciated.

---

### Post by Steven_B on 2007-05-05
Try ```
sudo update-grub
```
Normally, Synaptic/apt-get automatically calls this after installing new kernels, but somehow it didn't do it for you.
Uninstalling the kernel you're running is probably a bad idea, since if GRUB doesn't update, you won't be able to boot Ubuntu.

Don't be too afraid to edit .conf files.  I used to feel the same, but as long as you make a backup, you can almost always use recovery mode or a Live CD to put it back.

---

