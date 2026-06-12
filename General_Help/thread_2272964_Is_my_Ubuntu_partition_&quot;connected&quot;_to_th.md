---
title: "Is my Ubuntu partition &quot;connected&quot; to the swap?"
date: 2015-04-09
forum: General Help
---

### Post by holograus on 2015-04-09
Hi all, I'm having a strange issue after formatting my hard drive, or rather, I don't even know whether this is an issue, I'm somewhat confused. 

So, I have erased a Windows 7 (32 bit) partition on my hard drive with Gparted, then installed a fresh Windows 7 (64 bit) on the free space. Naturally, it has erased GRUB and I booted from a Live CD in order to restore it, but then I saw in Gparted that my Ubuntu partition (which I didn't format at all) turned into "unallocated space". Luckily, I could restore it using testdisk and I've successfully reinstalled GRUB, too, so that's not the issue. However, after restoring my Ubuntu partition and opening Gparted again, I found that there was a weird unallocated 1 Mib blob between the Windows and the Ubuntu partition (screenshot in the link below). Funnily, I remember that it was allocated and called /sda5/ before I used testdisk on my Ubuntu partition, but now it is unallocated. 

My assumption is that it was sort of header which linked my Ubuntu partition with the Linux Swap partition, otherwise I can't make much sense of it. Please, if someone could have a look at the screenshot below and give some useful advice, I would be very thankful. 

Screenshot:
[http://fs2.directupload.net/images/150409/fx6sczni.png](http://fs2.directupload.net/images/150409/fx6sczni.png)

Edit: Otherwise, if this is just some random blob I don't need to care about, is there a way to test whether my Swap is "active"? That's the only thing I'm afraid about, I don't know how the main partition connects to the Swap.

---

### Post by sammiev on 2015-04-09
When you click on the swap, does it say active?

---

### Post by holograus on 2015-04-09
Where can I see this in Gparted? Is there a toolbar? Sorry, I'm not very experienced with this sort of things.

Edit: Oh, I see, right click gave an option to "activate swap space" (I'm translating from the German tooltip), but when I tried it, I got an error. So I guess the swap indeed isn't linked to my main partition.

Edit2: [http://fs1.directupload.net/images/150409/pb6uj2kn.png](http://fs1.directupload.net/images/150409/pb6uj2kn.png)

---

### Post by sammiev on 2015-04-09
In gparted double click on the swap and a new window will come up. Using the "disk" from the menu you see a window like this if not using gparted.

---

### Post by holograus on 2015-04-09
Okay thank you. Yes, it is marked as "inactive", just as I assumed. Any way to fix it and to restore the 1 Mib blob as a "header"?

---

### Post by sammiev on 2015-04-09
If using gparted highlight swap and then right click and select swap on. It should switch to active.

---

### Post by sammiev on 2015-04-09
Here is a little more info if needed. 

[http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation](http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation)

---

### Post by holograus on 2015-04-09
Doesn't work for some reason, see my second post, I've already tried. There is a screenshot attached with the error message. Half of it is in English, here is what the German parts say:

swapon: /dev/sda3/: swapon failed: the argument is invalid
swapon: &&: "stat" failed: file or directory not found

---

### Post by holograus on 2015-04-09
After editing the /etc/fstab/ document as suggested in the guide above and running "sudo swapon -a" I'm getting the following output:

swapon: /dev/sda3: swapon failed: the argument is invalid

---

### Post by holograus on 2015-04-09
Update:
This [http://askubuntu.com/questions/396832/swapon-dev-sdb1-swapon-failed-invalid-argument](http://askubuntu.com/questions/396832/swapon-dev-sdb1-swapon-failed-invalid-argument) did the trick, now my swap is active. Issue can be marked as solved.

---

### Post by sammiev on 2015-04-09
> **holograus said:**
> Update:
This [http://askubuntu.com/questions/396832/swapon-dev-sdb1-swapon-failed-invalid-argument](http://askubuntu.com/questions/396832/swapon-dev-sdb1-swapon-failed-invalid-argument) did the trick, now my swap is active. Issue can be marked as solved.

Great, I was just checking out the error you were working on. :)

---

