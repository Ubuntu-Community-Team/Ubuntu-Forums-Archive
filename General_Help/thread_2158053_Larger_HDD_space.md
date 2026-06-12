---
title: "Larger HDD space?"
date: 2013-06-27
forum: General Help
---

### Post by EricGraham1987 on 2013-06-27
So when I installed Ubuntu I chose to partition 18gb for linux. Now I cant install any games. Can I increase the size without having to start my linux over? Gaming has gotten a lot better.

---

### Post by Cheesemill on 2013-06-27
Is this a Wubi installation or a proper dual boot?

Can you run gparted (you may need to install it first) and post a screenshot here so we can see exactly how your HD is arranged.

---

### Post by EricGraham1987 on 2013-06-27
I used Wubi to dual boot. I have windows 8.1 and Ubuntu 13.04 installed. I noticed my SSD isn't showing up either. Here is the screen shot attached.

---

### Post by Cheesemill on 2013-06-27
As this is a Wubi installation then these instructions should be what you're after...

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---

### Post by Cheesemill on 2013-06-27
As this is a Wubi installation then these instructions should be what you're after...

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---

### Post by EricGraham1987 on 2013-06-27
It said I cant resize it to more than 32gb. How do I resize it to 100gb? I did this command sudo bash wubi-resize.sh 100 and it said I need to use some override command.


EDIT: This command doesn't seem to work. sudo bash wubi-max-override

What am I doing wrong?

---

### Post by Cheesemill on 2013-06-27
The README file that you downloaded contains the answer you need...
```
sudo bash wubi-resize.sh --max-override 100
```

Please bear in mind that wubi is only intended for testing purposes, not for full-time installations (hence the 30GB limitation). If you are going to continue using Ubuntu I highly recommend doing a proper dual-boot installation instead as even small error on the underlying NTFS drive could wipe out your wubi installation at any time.

---

