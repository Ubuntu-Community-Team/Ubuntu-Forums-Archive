---
title: "Unexplained folders in /media"
date: 2013-09-08
forum: General Help
---

### Post by newbieBC on 2013-09-08
can someone help me and explain what all this garbage is in my /media folder?
---
drwx------ 2 root root  4096 Aug 25 18:41 6265-3132
drwx------ 2 root root  4096 Aug 25 18:47 6265-3132_
drwx------ 2 root root  4096 Aug 25 18:48 6265-3132__
drwx------ 2 root root  4096 Aug 25 18:41 898D-12FB
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB__
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB___
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB____
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_____
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB______
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_______
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB__________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB___________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB____________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_____________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB______________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_______________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB________________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB_________________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB__________________
drwx------ 2 root root  4096 Aug 25 18:47 898D-12FB___________________
drwx------ 2 root root  4096 Aug 25 18:48 898D-12FB____________________
drwx------ 2 root root  4096 Aug 25 19:04 898D-12FB_____________________
drwx------ 2 root root  4096 Aug 25 19:04 898D-12FB______________________
drwx------ 2 root root  4096 Aug 25 19:04 898D-12FB_______________________
drwx------ 1 ink  ink  16384 Aug  5 01:03 CC3256CA3256B8E2

---

### Post by coffeecat on 2013-09-08
I've moved your post from the ancient one you posted to into its own thread. You are more likely to get help that way.

Welcome to the forum.

---

### Post by carl4926 on 2013-09-08
Can we assume you have a USB Flash drive and it's id is: [COLOR=#000000] 898D-12FB[/COLOR]

---

### Post by newbieBC on 2013-09-08
> **carl4926 said:**
> Can we assume you have a USB Flash drive and it's id is: [COLOR=#000000] 898D-12FB[/COLOR]

ah! interesting. that might be possible, however, it is not attached! And these are god knows how many instances? Can I just remove all these then?

---

### Post by newbieBC on 2013-09-08
...just adding subscription to this thread so I know when something gets posted...

---

### Post by carl4926 on 2013-09-08
You can delete them

What version of Ubuntu is it?

---

### Post by newbieBC on 2013-09-08
12.04 lts

---

### Post by carl4926 on 2013-09-08
Figures.
Removable device mounting changed, not sure which version. But that matters not.
But IIRC the device will create a folder based on it's ID or Label and I thought it reused the existing one, next time you used it.
The folders you have will be empty I'm sure. But if you connect the device it should display the content of your flash drive.
I can't explain the multiple instances and I wonder now, if you connect the device which folder will show your flash drive content, one of them or all of them with the same ID ?

---

### Post by newbieBC on 2013-09-08
is there a quick way of doing that? such as maybe:
sudo rm -r /media/898*

---

### Post by carl4926 on 2013-09-08
If you reboot, are they still there?

---

### Post by newbieBC on 2013-09-08
> **carl4926 said:**
> If you reboot, are they still there?

very interesting.

well, the thing is, that I assume the were not being removed prior.
reason I stumbled upon this in the first place was, that I needed to make disc space for the most recent updates to be installed -> that lead to disc utility -> /media folder

I just rebooted, as the updates were also demanding for a reboot as well.

I then checked ls - l /media
and it was empty
Then I went to the folder of my Windows Partition.
After that I checked it again and it showed only that Partition mounted (but with a "total 16"?)

So I guess it is a no (which means Yay!)....

---

### Post by carl4926 on 2013-09-08
YW enjoy and relax

---

### Post by HereInOz on 2013-09-08
They look like old mount points for USB drives which have perhaps been improperly removed.  Could be wrong but I think that they should have been deleted when the USB device was removed, and the only reason I can come up with as to why they have not been is that the device has been just pulled out rather than properly removed.

---

### Post by newbieBC on 2013-09-08
> **HereInOz said:**
> ... is that the device has been just pulled out rather than properly removed.

ah! Ubuntu is not Plug&Play?! :-P

---

### Post by coffeecat on 2013-09-08
> **newbieBC said:**
> ah! Ubuntu is not Plug&Play?! :-P

Plug and play has nothing to do with it. With any operating system you need to properly unmount a mounted filesystem in order to avoid filesystem corruption. The 898D-12FB format of one of your device IDs suggests a FAT32 filesystem which is probably more vulnerable to corruption than newer filesystems if improperly unmounted. 

So - were you simply pulling the device out without an "eject" or "safely remove" or whatever it says in 12.04?

---

### Post by newbieBC on 2013-09-08
affirmative. did so under windows, too.

Plug&Play does have something to do with it:
When I plug the USB-stick in, I don't have to "mount" the thing manually either.

Of course I do not pull it out during any obvious file-transfers!

---

### Post by Nil_Pointer on 2013-09-08
Actually, you can configure removable devices to use write-through cache, so that it would be safer to just pull it out. Otherwise data, which appears to be transferred or saved might actually be waiting in cache to be written to stick. In write-through cache mode, if copying dialog disappeared - that means that data is certainly written to stick and not hanging in cache. But graceful unmount is better approach anyway.

---

### Post by bewareofthephog on 2013-09-08
fwiw my system has done the same thing in the past if I don't "eject" the media.  It hasn't since a fresh install of 13.04 though.

---

### Post by VMC on 2013-09-08
I have Ubuntu 12.04 also, If I plug in a USB anything, it gets mounted in "*/media/<device name>*".
It stays there unless I remove it. I have some scripts that I need for the device name to stay put. On occasion that has changed. I needed to just remove the new mount name.

If you plug in your USB device , what does the mount command show it being mounted?

On my Saucy install, then "*/media*" becomes "*/media/user/<device name>*""

---

