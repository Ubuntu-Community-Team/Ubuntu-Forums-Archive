---
title: "how do I mount an ntfs partitions automatically on bootup"
date: 2007-12-02
forum: General Help
---

### Post by adohall on 2007-12-02
I have 2 ntfs partitions. One is displayed automatically on my desktop at bootup and the other isn't. That's probably because I reformatted and renamed the second drive after installing ubuntu. When I double click on the second drive in Places/Computer, an icon does appear on the desktop. And I have no trouble saving to that drive. I notice there is a difference in mount options when I right click each and look at their properties.

How can I get the second drive to display an icon automatically on my desktop, like the first drive, on bootup?

---

### Post by forestpixie on 2007-12-02
I think you need to edit fstab to match the reformatted and renamed partition.

probably easiest to use uuid - you can check it out with 

```
blkid
```

I expect that the drive that's missing will have a different uuid in your fstab, check it out and change it - maybe backup before you do

```
sudo cp  /etc/fstab /etc/fstab.bak
```
```
gksudo gedit /etc/fstab
```

---

### Post by noremac on 2007-12-02
I have the same problem. The partition that does not show up on boot is not even in the fstab. Would I just add it, it's UUID, then any other "variables" to match another ntfs partition that DOES appear on boot up?

---

### Post by forestpixie on 2007-12-02
I'm not the best person to be asking to be honest - only done it the once - have a look at [this]("http://ubuntuforums.org/showthread.php?t=283131") and come back if you've got problems.

You could try to do what you say as long as you make a backup that you can get back to, if you're not sure about that -

to make backup

```
sudo cp /etc/fstab /etc/fstab.bak
```
to overwrite fstab with the backup
```
sudo mv /etc/fstab.bak /etc/fstab
```

---

### Post by adohall on 2007-12-02
Thank you so much. Your first suggestion - blkid, was the key. I just changed the UUID and now an icon shows up automatically. You made my day :)

---

### Post by forestpixie on 2007-12-02
great - glad I could help - can you mark thread solved for those who follow :)

---

