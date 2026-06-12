---
title: "remove a stubborn file"
date: 2016-12-11
forum: General Help
---

### Post by mvelte542 on 2016-12-11
Hello guys, It's been a long time since I've been here but that is only because I have learned so much from you guys and I thank you. I have a weird problem I just can't solve. I am running Ubuntu 14.04 Gnome desktop. I have a USB drive that when I plug it in it sees it and mounts it. But when I try to safely unmount it I get this error:

Error unmounting /dev/sdb1: Command-line `umount  "/media/mikey/C3P0_JR"' exited with non-zero exit status 1: umount: /media/mikey/C3P0_JR: not mounted

I have several USB drives all have different names, but when I want to remove them they all show the same message.

Error unmounting /dev/sdb1: Command-line `umount  "/media/mikey/C3P0_JR"' exited with non-zero exit status 1: umount: /media/mikey/C3P0_JR: not mounted

So I did some digging and found this: 

home/mikey/media/C3P0_Jr

Which is the name of my USB drive, which is not plugged in by the way. I have tried to select the file and then hold shift and press delete, nothing. I have tried: rm home/mikey/media/C3P0_Jr, terminal says file doesn't exist. I have tried to drag and drop into the trash bin, cannot be deleted. I can access all my USB drives and add and remove files from them but I can't safely unmount them. 
How do I remove this file and or change permissions so I can delete it? Nothing I've tried so far has worked for me. Thanks in advance.

---

### Post by howefield on 2016-12-11
So what is the output of the terminal command..

```
ls -al ~/media/C3P0_Jr
```

---

### Post by mvelte542 on 2016-12-11
ls: cannot access /home/mikey/media/C3P0_Jr: No such file or directory

---

### Post by mvelte542 on 2016-12-11
I have also tried /home/mikey/media/C3P0_JR. I get: ls: cannot access /home/mikey/media/C3P0_JR: No such file or directory
It is clearly there. Do I need to change permissions to delete it?

---

### Post by mvelte542 on 2016-12-13
Okay I want to thank all who have looked at this thread and have pondering an answer to my problem. After doing an exhaustive Google search I stumbled across this video on Youtube.
[https://www.youtube.com/watch?v=VOSsAf4ZCWk](https://www.youtube.com/watch?v=VOSsAf4ZCWk)
I tried it and it worked.
Thank you all and happy holidays.
This I'm marking as solved. :P

---

