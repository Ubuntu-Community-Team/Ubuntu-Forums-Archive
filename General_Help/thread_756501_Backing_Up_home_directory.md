---
title: "Backing Up home directory"
date: 2008-04-15
forum: General Help
---

### Post by tommyhakinen on 2008-04-15
Hi,

I am using Ubuntu Gutsy for about a month and I LOVE it. Since the first time I installed and exploring it, trying new software, and screwing things up, I have reinstalled it for several times. I was having difficulties in backing up my home directory. I tried to copy it to my thumb drive, but I had an error message saying I don't have permissions. I would like to know, is there any way to back up my home directory?

Thank you.

Regards,

tommy

---

### Post by sekinto on 2008-04-15
Try this:

```
sudo cp -fpr /home/<YOU> /directory/on/your/usb/drive
```

Although I'm not sure if that will copy hidden folders/files...

You could always put it all in a .tar.gz archive to.


In the future I recomend making a separate /home partition to make things like this easier.

---

### Post by tommyhakinen on 2008-04-15
thank you for the reply. Is it possible for me to create a separate partition for my home directory after I have my Ubuntu installed?

---

### Post by sekinto on 2008-04-15
Yeah, it would require editing your /etc/fstab file, doing some things with gParted, and copying some data over. The nice thing about having a separate /home partition is that if you decide to reinstall or even switch distributions you can keep your settings and personal files.

But if you are reinstalling Ubuntu I would just wait till then to make a separate /home partition.

---

