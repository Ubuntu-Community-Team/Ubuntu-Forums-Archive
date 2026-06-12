---
title: "Why is the Startup Disk Creator not in Xubuntu?"
date: 2015-01-24
forum: General Help
---

### Post by Tar_Ni on 2015-01-24
Hi,

This is something that is bothering me, why the Xubuntu devs do not include the Startup Disk Creator as a default app in Xubuntu? This is **very** useful to convert a USB key to a bootable Linux volume.. I mean this is included in Ubuntu, Lubuntu ect and should be considered basic.

I am not the first to complain about this: [http://mylinuxexplore.blogspot.ca/2014/04/xubuntu-1404-lts-trusty-tahr-review.html](http://mylinuxexplore.blogspot.ca/2014/04/xubuntu-1404-lts-trusty-tahr-review.html)

How can the Xubuntu team be notified? At least I would like to understand the logic for not including this app out of the box.


Thanks.

---

### Post by Dennis N on 2015-01-24
My guess would be that because of the recent critical bug in that package, they decided not to include it. You could inquire further on the xubuntu-users mailing list and perhaps learn more.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

---

### Post by sudodus on 2015-01-24
The Startup Disk Creator has suffered from several bugs during several years. At least one of the bugs is/was critical, and many of them are/were annoying, but you could live with them. Many bugs are squashed now, but some remain. For example, I think it can still not remove all the files for a pendrive, 'Erase Disk', but you can do that with other tools.

The Startup Disk Creator alias usb-creator-gtk is easy enough to install, as are several other tools to make USB boot drives. It is similar to Unetbootin, and both of these tools can help you create persistence. There are also many other tools, some of them more reliable, some of them easy to use, some of them more difficult to use, some of them do not offer persistence, but often you don't want it anyway ... Please refer to the following link and links from it to get an overview.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mc4man on 2015-01-24
The removal was done in quantal, likely no one bothered to return by now as things have changed.., ie. s-d-c uses udisks2 as does xubuntu- 
from the quantal seed - 
> Committer: Micah Gersten
    Date: 2012-09-10 13:52:27 UTC
    Revision ID: [email]micahg@ubuntu.com[/email]-20120910135227-5fzgqst8u2kdzcqo

* Drop usb-creator-gtk, uses udisks instead of udisks2, doesn't seem needed in a default install

---

### Post by The Cog on 2015-01-24
I always just use dd to copy the image to the stick, like this:
```
sudo dd if=Downloads/xubuntu-whatever.iso of=/dev/sdb bs=1M
```
but you have to be really **really** sure you are writing to the right output device and not your all important drive full of photos etc.
I normally use ```
sudo fdisk -l
``` to list the drives. Sometimes my stick is /dev/sdf rather than sdb.

---

### Post by sudodus on 2015-01-24
I wrap [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") around dd to make it safer :-)

---

### Post by The Cog on 2015-01-24
> **sudodus said:**
> I wrap [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") around dd to make it safer :-)

That looks interesting. I will give it a try.

---

### Post by Tar_Ni on 2015-01-24
Thank you very for your replies.

In the last 2 months I received 2 updates for Startup Disks Creator in Lubuntu and though I've had issue with it in the past, now it works pretty well for me. I always format the drive with the ''Disk'' tool beforehand anyway.

I know that there are other options available for download such as Unetbootin but it just seems to me that a distro should provide such a tool out of the box. I mean the Xubuntu team does provide Xfburn for Cd, DVD, Blue Ray but nothing as far as USB goes.

I guess I am complaining here but it seems to me that would be a valuable addition. I am also thinking for the inexperienced users who should have at least all the basics apps they need close at hand.

---

### Post by mikodo on 2015-01-24
> **Tar_Ni said:**
> How can the Xubuntu team be notified? At least I would like to understand the logic for not including this app out of the box. I find the developers at irc #xubuntu-devel always happy to respond to questions.

[InternetRelayChat  Community Help Wiki]("https://help.ubuntu.com/community/InternetRelayChat")

---

### Post by ian-weisser on 2015-01-24
> **Tar_Ni said:**
> I guess I am complaining here but it seems to me that would be a valuable addition. I am also thinking for the inexperienced users who should have at least all the basics apps they need close at hand.

It does not seem like a valuable addition for new users to me.

Why would a new user need a LiveUSB creator? They already have a LiveUSB...that's presumably how they installed.

If they are new, then the next time they want to create a LiveUSB, they will presumably return to the same Ubuntu website for the new image and the instructions to follow.



Intermediate users, however, are a different story. But intermediate and experimenting users already know how to trivially obtain usb-creator-gtk

---

### Post by C.S.Cameron on 2015-01-25
Back around 11.04, usb-creator.exe came on the iso, great for Windows users that wanted to give *buntu a try.

---

