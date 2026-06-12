---
title: "target-filesystem-doesnt-have-requested-sbin-init-bin-sh-0-cant-open-splash"
date: 2016-12-15
forum: General Help
---

### Post by codfishcatfish on 2016-12-15
Before I start, I have tried every method on the new to fix this error but still I can't boot into my Xbuntu installation.   I keep getting target-filesystem-doesnt-have-requested-sbin-init-bin-sh-0-cant-open-splash. I tried fsck -y -v -f /dev/sdc5 (my system) and e2fsck -f -y -v /dev/sdc5and all other methods but still this error comes up. Even resorting to a Live CD but still can't get my OS to boot.

Any help greatly appreciated and can skype with messages as a talk me in. I want to change the Sketch on my Arduino Mega but all my files are on my Xbuntu OS.

Many thanks, kind regards


Spence

PS: A little noobie going on but fast learner.

---

### Post by #&amp;thj^% on 2016-12-15
This is just a method I used once back a few years ago with 15.10...and it worked then for me...but your mileage may vary.
To be clear here if this breaks your system even more **I bear No responsibility here**.
I Booted to a live install USB device then moved my /sbin from the live media device "AS ROOT" to the proper "Disk Partition" (The broken XFCE in your case)
Then rebooted and Bobs your uncle worked and was able to boot to my once broken OS.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
I left the above instructions vague for a reason...as to make you read it carefuly.
My method went like this:
Booted the computer to Live CD or USB (this is better with the same media used for your Original install)
After booting...I then went to the terminal:
```
su
```
In that same Terminal I then called my file manager...in your case it will be thunar.
```
thunar
```
I then navigated to the broken Partition (The one that won't boot) and found /sbin.
I then deleted that folder and copied the /sbin from the live media to the one I just deleted.
and rebooted to a working login.
Again this is a last resort type of fix...and I again warn you are on your own here if this is the route you take.

Best of Luck and Kind Regards

---

### Post by codfishcatfish on 2016-12-15
Thanks for information and t has been something I tried however the system partition is locked and every time I try to access it it even as a Root user it says Partition mounted, then I unmount it and it says drive in use. I think my version of Xubuntu is like 13.03.96 or something and I was getting warnings before I upgraded and this was the result after a reboot. I don't think I can break ti anymore.  just need my ino files back.

Thanks I will give your method another go.

Regards

Spence

---

### Post by #&amp;thj^% on 2016-12-15
Just another thought here try this "**as root"** from the terminal:
```
dbus-launch thunar
```

---

### Post by codfishcatfish on 2016-12-16
Thanks 1 Fallen,  had an ultra busy day to day so only just got home but will try out your fix right away and post back the results. Many thanks for the continued support.   Regards  Spence

---

### Post by codfishcatfish on 2016-12-16
Thanks 1 Fallen,  had an ultra busy day to day so only just got home but will try out your fix right away and post back the results. Many thanks for the continued support.   Regards  Spence

---

### Post by codfishcatfish on 2016-12-16
Hi,
  wow, what a chore. I had major problems trying to get permission to the drive however in the end I just set read write permissions to everyone, and renamed Sbin to old_sbin using Nautilus (quite a controversial program apparently) and then used Xubuntu 14.04 LTE Live disk to copy a clean copy of sbin to that drive and after a reboot it worked. Relieved to say the least.

  Can't that you enough 1Fallen, advice was spot on.

Kudos points I think.

Kind regards

Spence

---

### Post by #&amp;thj^% on 2016-12-17
> **codfishcatfish said:**
> Hi,
  wow, what a chore. I had major problems trying to get permission to the drive however in the end I just set read write permissions to everyone, and renamed Sbin to old_sbin using Nautilus (quite a controversial program apparently) and then used Xubuntu 14.04 LTE Live disk to copy a clean copy of sbin to that drive and after a reboot it worked. Relieved to say the least.

  Can't thank you enough 1Fallen, advice was spot on.

Kudos points I think.

Kind regards

Spence
That is Great News..:)
Good Job in figuring out to change permissions. 
Kind Regards

---

