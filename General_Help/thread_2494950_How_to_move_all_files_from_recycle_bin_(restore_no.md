---
title: "How to move all files from recycle bin (restore not working)"
date: 2024-02-01
forum: General Help
---

### Post by alexvb on 2024-02-01
I recent had a mishap on Ubuntu 22.04. It seems like a partial reinitialisation happened.
For unknown reason all files ended up in recycle bin (happened real fast)
I can see all my files in recycle bin but I cannot bring them back to their regular position on hard disk using restore.
Is there a method using a terminal command line (or lines) to bring all files in trash back to their position on the hard disk
At this moment I can open individual files in the recycle bin and then use save as, but that is only one file at a time.

Thanks in advance for any help and insight.
P.S. I use Ubuntu through the GUI. I can use command line only by copying as I don't quite know what I do when using command line :-(

---

### Post by yancek on 2024-02-01
>  partial reinitialisation happened.

What does that mean?  I've never seen that term used before.  What 'mishap' are you referring to?  What had you been doing just prior to this happening?  What files are you referring to?  Are they just files you had in your /home/user directory?  Are they also system files?  If you have only files from your /home/user directory you should be able to move them back to the proper directory with the mv (move) command.  Doesn't seem like the kind of event that would happen without user intervention so more details would be needed to help.

---

### Post by Rubi1200 on 2024-02-01
Is this Ubuntu in a virtual machine?

---

### Post by ajgreeny on 2024-02-01
> **yancek said:**
> What does that mean?  I've never seen that term used before.  What 'mishap' are you referring to?  What had you been doing just prior to this happening?  What files are you referring to?  Are they just files you had in your /home/user directory?  Are they also system files?  If you have only files from your /home/user directory you should be able to move them back to the proper directory with the mv (move) command.  Doesn't seem like the kind of event that would happen without user intervention so more details would be needed to help.
Unfortunately using terminal commands to move from the bin back to home does not work; it just throws an error** "cannot stat <filename>.  No such file or directory"** whether you use the** trash:///** naming or the full **.local/share/Trash/files** pathway.

---

