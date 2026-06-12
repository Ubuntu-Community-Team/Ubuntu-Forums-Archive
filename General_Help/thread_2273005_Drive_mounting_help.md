---
title: "Drive mounting help"
date: 2015-04-10
forum: General Help
---

### Post by scano.ie on 2015-04-10
hey guys I am having problem mounting 3 HDD's when my machine boots I have placed the following code into the rc.local folder and it will show that the drives over the network but I can’t see any of the contents of the drives

```
sudo mount -t ntfs-3g /dev/sda1 /media/Data
sudo mount -t ntfs-3g /dev/sdb1 /media/Movies
sudo mount -t ntfs-3g /dev/sdc1 /media/TV
```

But when I run putty and input the same code it works perfectly. Any help would be great

---

### Post by Holger_Gehrke on 2015-04-10
Is there a reason you're doing it this way instead of setting up entries in fstab ?

---

### Post by scano.ie on 2015-04-10
> **Holger_Gehrke said:**
> Is there a reason you're doing it this way instead of setting up entries in fstab ?

Hey thanks for the reply I’m not familiar with fstab. Would you have a link to good instructions for it?

---

### Post by coffeecat on 2015-04-10
Here's a community wiki page which concentrates on mounting NTFS partitions and which includes a basic ntfs fstab line which you can modify with your particular mount points and partitions:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

And this is the Introduction to Fstab community wiki page:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Both are overdue for some updating, but there is usable information there.

---

### Post by Morbius1 on 2015-04-10
fstab is the way to go but as an FYI putting something like this in rc.local will not work:
> sudo mount -t ntfs-3g /dev/sda1 /media/Data
"sudo" will invoke a prompt for the sudo password. There's no one to answer the question. Besides, root runs rc.local anyway.

---

### Post by Holger_Gehrke on 2015-04-10
Another source for information about everything and anything on your Ubuntu system are the manual pages that get installed with most programs. To read them, enter 'man "replace_this_with_a_command_or_topic"'. In your case it would be 'man fstab'. Of course 'man' has a manual page itself ...

---

### Post by scano.ie on 2015-04-10
thanks guys for the help worked a treat.

---

