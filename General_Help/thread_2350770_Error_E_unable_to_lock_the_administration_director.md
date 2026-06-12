---
title: "Error E: unable to lock the administration directory. Is another process using it?"
date: 2017-01-27
forum: General Help
---

### Post by oceanknr on 2017-01-27
While updating the system using software center I am unable to use apt-get which I think is normal but the problem is the updating takes forever. Even after I restart Ubuntu I get the same error. 

The problem doesn't end there. After trying a few solutions without any result I reboot Ubuntu again only to be met with a black screen. The OS doesn't load. I reinstalled Ubuntu many times and always I face the same problem when trying to update the software.

This is my first time using the OS and I am not happy with it at all.

---

### Post by geeksmith on 2017-01-27
Sorry you're having a difficult time with Ubuntu -- this is not a typical first experience. A few questions:
[LIST]
[*]What version are you installing?
[*]Please define "takes forever" (minutes? hours? days? weeks? months?)
[*]Did you download updates during the installation?
[*]Can you provide any helpful information about the computer hardware? (age, CPU, memory, PC, Apple, tablet, phone, netbook, chromebook, BIOS, UEFI, etc.)
[*]What's your Internet connection type and speed?
[/LIST]

Your first round of updates will definitely take longer than subsequent updates because the installation media cannot possibly have the latest software available today. This is not something unique to Ubuntu -- it is the case for MacOS, Windows, and basically any other operating system installed offline.

You're correct that updating cannot be done while using the software center. Really, the software center should be used for doing the updates.

The more precise your questions and information, the faster and better the resolution from the forum.

---

### Post by deadflowr on 2017-01-27
> **oceanknr said:**
> While updating the system using software center I am unable to use apt-get which I think is normal but the problem is the updating takes forever. Even after I restart Ubuntu I get the same error. 

The problem doesn't end there. After trying a few solutions without any result I reboot Ubuntu again only to be met with a black screen. The OS doesn't load. I reinstalled Ubuntu many times and always I face the same problem when trying to update the software.

This is my first time using the OS and I am not happy with it at all.

It's most likely because automatic updates is running.
You can turn those off by going to Software and Updates >> Updates and toggle the settings for the updates.
Change/check the setting for When there are security updates.
You can also change when it checks if you want.

hope it helps

---

### Post by oceanknr on 2017-01-27
I am using Ubuntu version 16.04.1 LTS. Didn't download the updates during installation. It is a very old computer running windows 7 so no UEFI. I waited 10 minutes and then gave up because there was no progress bar of the update. 

I will try turning off the auto updates.

Why won't Ubuntu start though. It just shows a blank screen. I will boot into recovery mode and try to fix it.

Thanks.

---

### Post by geeksmith on 2017-01-27
From the sounds of it, you rebooted it in the middle of software updates.

---

### Post by Geoffrey_Arndt on 2017-01-31
> **oceanknr said:**
> I am using Ubuntu version 16.04.1 LTS. Didn't download the updates during installation. It is a very old computer running windows 7 so no UEFI. _**I waited 10 minutes and then gave up**_ because there was no progress bar of the update. 

I will try turning off the auto updates.

Why won't Ubuntu start though. It just shows a blank screen. I will boot into recovery mode and try to fix it.

Thanks.

..............................................................................................

"Why won't Ubuntu start though" . . . . well . . . . why won't you (after being asked), provide the basic specs of your computer . . . so we can advise why???   Often it has to do with your graphics chipset and is correctable by using the "nomodeset" boot up parameter to get into into a lower resolution login screen, thus allowing you to install the proper graphics driver via the "additional drivers" functionality of Ubuntu.    

See my signature for "no-brainer" solutions to running Linux - - - making it as easy as setting up an Apple or Samsung tablet (or maybe 10 minutes to get it all done and working perfectly).

To _retrofit a computer with Ubuntu when the original hardware was designed and tested only for Windows_ . . . takes a bit of knowledge or experience.

---

### Post by oceanknr on 2017-01-31
I got it working. Thanks. I didn't use the nomodeset boot parameter. Ubuntu used to start fine the first time. That is when I installed the driver. It used to show a black screen after a reboot but now it works just fine.

---

### Post by Geoffrey_Arndt on 2017-01-31
Ok Oceanknr . . . sounds good.   So the official video driver worked.    See you around the forums.


GG

---

