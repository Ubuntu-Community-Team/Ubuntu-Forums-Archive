---
title: "Flash drive not acknowledged by PC?"
date: 2016-07-17
forum: General Help
---

### Post by Camilia on 2016-07-17
I have a flashdrive which is not acknowledged by PC with ubuntu os. It is acknowledged by PC with windows os. The port I put it in I have put another flashdrive in and had no problems. 

Any suggestions.

---

### Post by yancek on 2016-07-17
And the flash drive has what on it?  What filesystem type for starters.  What exactly does "acknowledge" mean in this case?  How do you try to access/read it and what happens?

---

### Post by sudodus on 2016-07-18
In addition to replying to *yancek*'s questions, please run the following commands in a terminal window of Ubuntu, when the flashdrive is connected, and post the output within CODE tags in a reply:

```
lsusb
df
sudo parted -ls
sudo lsblk -fm  # run this command in a wide window, for example after maximizing it
```

It will help us help you :-)

---

### Post by Camilia on 2016-07-18
> **yancek said:**
> And the flash drive has what on it?  What filesystem type for starters.  What exactly does "acknowledge" mean in this case?  How do you try to access/read it and what happens?
I plug it in and it does not show as being plugged in. Today is working with no problem. I think it has something to do with the keys on the key ring with the flash drive. For some how, in the past, when the usb connector with key ring fell off the tower usb connector stopped working.

---

