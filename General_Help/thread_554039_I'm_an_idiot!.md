---
title: "I'm an idiot!"
date: 2007-09-18
forum: General Help
---

### Post by matty_b_1000 on 2007-09-18
Grr... I was trying to make myself the owner of a hard disk, so I decided to mount it to /home. Trouble was, I forgot to backup my Home folder first, so now I've lost most of my application settings, Wine and all my windows programs, and certain Ubuntu programs, such as the Root Terminal, Add/Remove programs, etc. Is there any way to restore any of this?

---

### Post by bodhi.zazen on 2007-09-18
sudo umount /home or reboot

---

### Post by McNils on 2007-09-18
Have you tried to unmount the drive from /home?

---

### Post by olieviya on 2007-09-18
I'd say do a clean install of Ubuntu to fix everything... it's not like you have anything to loose, right?

---

### Post by Wim Sturkenboom on 2007-09-18
@olieviya:
If you mount a drive on an existing directory, you don't loose anything. The existing content is only obscured (hidden) by the mounted drive. So no need to install again, just unmount as suggested by the others.

---

### Post by matty_b_1000 on 2007-09-19
I mounted it by editing my fstab... will undoing this restore it? By the way, is there any way to edit the system settings from the live CD? Because I enable autologin and now it just gives me an input out of range.

---

### Post by Wim Sturkenboom on 2007-09-20
Why don't you try it? And yes, you should get the original contents of /home back.

No answer on the second question; wait for someone else to come along who has experience with liveCDs

---

### Post by matty_b_1000 on 2007-09-20
Thanks for the help. My problem is solved.

[edit] No, apparently not. I created a separate partition to be my /home, formatted it to ext3, but now only root can do anything with it, but root can't even create or delete files. All there is there is a folder called "lost+found" with a red X on it. What is going on?

[edit] Never mind, root could edit stuff.

---

