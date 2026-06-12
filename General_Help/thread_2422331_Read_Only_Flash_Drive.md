---
title: "Read Only Flash Drive"
date: 2019-07-05
forum: General Help
---

### Post by daniell59 on 2019-07-05
For some reason all of my flash drives became read only. When I try to write to them, I get the following error message.

Error while copying to "8.0 GB volume

The destination is read-only

I get a similar message on all 5 of my flash drives.

Ubuntu 16.04 64

Any insight into this problem will be appreciated.

---

### Post by Frogs Hair on 2019-07-05
There are various threads related to this problem which I experienced a few release cycles ago.

[https://askubuntu.com/questions/563764/usb-devices-showing-as-read-only](https://askubuntu.com/questions/563764/usb-devices-showing-as-read-only)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375)

---

### Post by daniell59 on 2019-07-05
> **Frogs Hair said:**
> There are various threads related to this problem which I experienced a few release cycles ago.

[https://askubuntu.com/questions/563764/usb-devices-showing-as-read-only](https://askubuntu.com/questions/563764/usb-devices-showing-as-read-only)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375)

I am trying to digest the information that you sent me. So far I have not been able to do so.

---

### Post by Frogs Hair on 2019-07-05
Try this command from the ask Ubuntu post. In my case I could drag files from the USB to Nautilus, but not the reverse. I would get read only notification.  
```
killall nautilus
```

---

### Post by daniell59 on 2019-07-06
> **Frogs Hair said:**
> Try this command from the ask Ubuntu post. In my case I could drag files from the USB to Nautilus, but not the reverse. I would get read only notification.  
```
killall nautilus
```

Thanks, but I am sorry to say that it did not work.

---

### Post by daniell59 on 2019-07-06
It turned out that the problem was with the flash drives. Once I formatted them, they were  no longer read only.

---

### Post by TheFu on 2019-07-06
> **daniell59 said:**
> It turned out that the problem was with the flash drives. Once I formatted them, they were  no longer read only.

I see a similar issue with vFAT and NTFS drives written by Linux systems about every 20-40 days. In short, I use them for unimportant data and not for backups.  Doesn't matter if it is flash or spinning disks.  However if they are formatted with ext4 (spinning disks only), then there isn't corruption that I've seen.

---

### Post by daniell59 on 2019-07-06
However if they are formatted with ext4 (spinning disks only), then there isn't corruption that I've seen.

Can I format flash drives with ext4?

---

### Post by TheFu on 2019-07-06
yes, but it would be terrible for the flash livespan.  That's why I said "spinning disks only".

---

### Post by daniell59 on 2019-07-06
yes, but it would be terrible for the flash livespan.  That's why I said "spinning disks only"

If I ever build another computer and utilize a solid state drive, would there be a problem formatting it with ext4?

---

