---
title: "trouble after upgrading to 12.10"
date: 2012-10-29
forum: General Help
---

### Post by Darth Poder on 2012-10-29
I upgraded from 12.04 to 12.10 and now I can't access my stuff. My normal screen resolution is 1600X900 but in 12.10 I can't get above 1440X600. Also my task bar is not there, and when i open a window the window options don't appear either. so i cannot minimize, maximize, or close windows. I have some important files on my Ubuntu that I need to get off. So just killing Ubuntu isn't going to work for me. Is there any easy solution to the problem such as downgrade or patch or something?

---

### Post by twipley on 2012-10-29
One thing you might try to get your files off is backup them through the LiveCD.

Extraneous file systems are not automatically mounted. An intuitive, graphical-interface method of mounting one is simply to press the folder icon in the launcher at the left, then left-click once on the device (e.g., 128 GB Volume).

Then, you can see it has been mounted by navigating to / (click on "file system" on the left bar of the file browser, which in fact is the LiveCD file system), then to /media. An "ubuntu" folder should now be present, which contains the mounted volume. This (/media/ubuntu) is the folder you might want to chown, chmod, or, for good measure, both.

```
chmod -R 777 /media/volume
```

Then, backup to desired device, and reinstall 12.10 afresh. The problem you are experiencing is of unknown cause to me, although that will fix it.

---

### Post by Darth Poder on 2012-10-29
yeah its pretty wired to me too. I know this much I won't be upgrading from inside Ubuntu using the update manager again.

---

### Post by twipley on 2012-10-29
The norm is internal updates to work better than that, though. :)

Although just to feel it all fresh in and around I prefer doing it in an external manner. (l33t USB flash drives.)

---

### Post by Darth Poder on 2012-10-29
I just used the update manager because it looked pretty easy and effective, but when it was finished well you know the rest.

---

### Post by TheMTtakeover on 2012-10-29
I always recommend fresh installs to anybody regardless if it is Linux, Win, Mac, or whatever OS they are on.

---

### Post by Ambushed on 2012-10-29
> **TheMTtakeover said:**
> I always recommend fresh installs to anybody regardless if it is Linux, Win, Mac, or whatever OS they are on.

I am going to back-up everyone on my 12.04 and upgrade to 12.10 with a fresh image on my USB :D :guitar:

This is likely why the upgrade screwed up

---

### Post by Darth Poder on 2012-10-30
> **Ambushed said:**
> I am going to back-up everyone on my 12.04 and upgrade to 12.10 with a fresh image on my USB :D :guitar:

This is likely why the upgrade screwed up

yeah i would suggest you do that I would hate to see someone else have the same issue. also can you tell me a good method for making a good bootable image on usb? most of the ones I've tried don't work all that good.

---

### Post by Mark Phelps on 2012-10-30
> **Darth Poder said:**
> yeah i would suggest you do that I would hate to see someone else have the same issue. also can you tell me a good method for making a good bootable image on usb? most of the ones I've tried don't work all that good.

YES -- use the Universal USB Installer from pendrivelinux.com.  Be sure to select the bottom generic option when you do this, as 12.10 hasn't been integrated into the selection list yet.

I did this a few days ago using a 12.10 ISO file I downloaded -- and it worked great!

---

