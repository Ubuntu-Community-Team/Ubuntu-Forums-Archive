---
title: "Remove Ubantu Clutter"
date: 2008-05-03
forum: General Help
---

### Post by dokebi on 2008-05-03
Hello. 

I first installed Gutsy (i think), and then I updated.  Now in my boot page, I have the following ...

= = = 
Ubuntu 8.04, kernal 2.6.24 - 16 - generic
Ubuntu 8.04, kernal 2.6.24 - 16 - generic (recovery mode)
Ubuntu 8.04, kernal 2.6.22 - 14 - generic
Ubuntu 8.04, kernal 2.6.22 - 14 - generic (recovery mode)
Ubuntu 8.04, memtest 86+
Other Operating Systems:
Windows Vista/Longhorn (loader)
= = = 

Question:
How do I delete the "unnecessary" Ubuntu boot?
Which are the "unnecessary" ubuntu?

Thanks in advance.

---

### Post by damis648 on 2008-05-03
Ok, the "unnecessary" ones are the ```
Ubuntu 8.04, kernel 2.6.22 - 14 - generic
```
 and the ```
Ubuntu 8.04, kernel 2.6.22 - 14 - generic (recovery mode)
```, however they are there because, upon the upgrade, you upgraded your kernel. The old kernel is still there, for emergency use and it is the one I have listed above (2.6.22 - 14) and the now one is 2.6.24 - 16. If you are confident that nothing has gone wrong during the kernel upgrade, then to remove them simply enter terminal and
```
cd /boot/grub/
sudo cp menu.lst menu.lst.backup
sudo gedit menu.lst
```
and scroll to the bottom of the document. At the bottom, you will find the entries for the grub. Remove
```
title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=92345252-a232-42fa-80cb-373f4234eef4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
(or something like that) and also
```
title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=92345252-a232-42fa-80cb-373f4234eef4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```
(or something like that)...

---

### Post by forestpixie on 2008-05-03
when you get updates to the kernel it adds them to boot - 16 is the newest - it's probably best to leave it there because if you get a problem with one kernel you can still boot with the old one.

Once you've got more than 2 you can remove the old kernels with synaptic easily.

Edit - removing them from grub - does only that. To remove the kernel use synaptic to remove it, doing that will update the boot list and remove the lines from menu.lst.

---

### Post by damis648 on 2008-05-03
sry look at the next post

EDIT: and yes, this is true. My method proposed above only deletes them from the grub menu, however this is probably all you need / want to do, yes?

---

### Post by damis648 on 2008-05-03
Also, if something were to go wrong and you cannot boot but you can get into recovery console, choose the root prompt option and type
```
cd /boot/grub/
sudo cp menu.lst.backup menu.lst
sudo reboot
```
and that is all you can do. If grub will not load at all, load the liveCD and go into nautilus and mount you main Ex3 partition onto which ubuntu is on (by clicking on it) and then in terminal type
```
cd /media/disk/boot/grub/
sudo cp menu.lst.backup menu.lst
```
and close it and restart back without the LiveCD.
NOTE: this assumes the partition is mounted at /media/disk... if is not, change it.

---

### Post by dokebi on 2008-05-03
damis648 and forestpixie.

Thank you both for the rapid responses.  You are right, I don't mind having the kernals, I'm just a neat freak who wishes to have a tidy menu.

Thanks again.  

Note:  This is my first day with Ubuntu and I'm enjoying my experience.:guitar:

---

### Post by damis648 on 2008-05-03
Glad to be of help.:popcorn:

---

### Post by jocko on 2008-05-03
Remember that if you don't uninstall the old kernels they will reappear in your grub menu when you get a kernel upgrade.
If the new kernel works, there's no real point in keeping the old.

---

### Post by madtom1999 on 2008-11-16
Is there an ncurses or gui editor for Grubs menu.lst?
I can be a pain to edit and an aware editor  would be nice.




cancel that! found [http://ubuntuforums.org/showthread.php?t=228104]("http://ubuntuforums.org/showthread.php?t=228104")

---

