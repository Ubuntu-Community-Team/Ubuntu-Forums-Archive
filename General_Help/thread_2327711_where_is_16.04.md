---
title: "where is 16.04?"
date: 2016-06-13
forum: General Help
---

### Post by hmiersch on 2016-06-13
i thought 16.04 was supposed to be released in april. but now it's june and the software updater still offers me 15.10. what's going on?

---

### Post by Dennis N on 2016-06-13
I believe you have to wait for the first point release before you can upgrade from 15.10 though Software Updater.

---

### Post by QDR06VV9 on 2016-06-13
Yes as Dennis N tells 14.04 wont receive a upgrade notification until the first point release.
> [h=2][SIZE=2]Upgrading from Ubuntu 14.04 LTS or 15.10[/SIZE][/h] 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

---

### Post by Impavidus on 2016-06-13
If you set the updater to inform you of release upgrades to any release, it will (on 14.04) offer an upgrade to 15.10. Which is a bad idea, and in my opinion that upgrade shouldn't have been offered. If you set the updater to inform you of release upgrades to LTS releases only, it will offer the upgrade to 16.04 once 16.04.1 is released.

The upgrade from 15.10 to 16.04 has been offered since the release of 16.04, but doing a two-step upgrade 14.04&#8594;15.10&#8594;16.04 is not recommended. Better wait 5 more weeks.

---

### Post by hmiersch on 2016-06-13
anyone got an ETA for 16.04.1?

---

### Post by QDR06VV9 on 2016-06-13
Well it is scheduled for July 21st 2016. [https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

---

### Post by hmiersch on 2016-06-14
I'll call it 16.07 then :-)

---

### Post by hmiersch on 2016-07-22
> **runrickus said:**
> Well it is scheduled for July 21st 2016. [https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

Today is he 22nd and the software updater still offers me 15.10. So much for that then. What's going on?

Id be willing to download and install 16.04 manually if that gives me some benefit. For example, it bothers me that I can't access the Ubuntu disk from OSX. Is here a disk format that Ubuntu can boot from and that OSX can access? Alternatively, is here some kind of driver that enables OSX to access Ubuntu disks?

---

### Post by QDR06VV9 on 2016-07-22
> **hmiersch said:**
> Today is he 22nd and the software updater still offers me 15.10. So much for that then. What's going on?


As I said scheduled for July 21st 2016...I am just staff not a Canonical Empolyee.
> **hmiersch said:**
> 
Id be willing to download and install 16.04 manually if that gives me some benefit. For example, it bothers me that I can't access the Ubuntu disk from OSX. Is here a disk format that Ubuntu can boot from and that OSX can access? Alternatively, is here some kind of driver that enables OSX to access Ubuntu disks? 
This worked for 15.04 but I don't run any OSX systems, but have a look here [http://askubuntu.com/questions/3815/how-to-share-files-between-ubuntu-and-osx](http://askubuntu.com/questions/3815/how-to-share-files-between-ubuntu-and-osx)

[B]Note: that I would not recommend disabling journaling, and I do not recommend writing to the OSX system partition from a different OS. If you want to read and write to some files from both OSs, you should create a separate partition for this purpose. Non-journaled HFS+ would work as a file system, FAT 32 should also work. 
[/B]Kind Regards

---

### Post by grahammechanical on 2016-07-22
> graham@Ub1604:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


For those like me who are already on 16.04 the upgrade takes place during a normal system update/upgrade. For those on 14.04 or 15.10 the answer is, it is on its way.

Regards

---

### Post by cariboo on 2016-07-22
16.04.1 is here, just updated yesterday:

```

cariboo@willy:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
```

---

### Post by howefield on 2016-07-23
> **hmiersch said:**
> Today is he 22nd and the software updater still offers me 15.10. So much for that then. What's going on?.....

Release team are working through some bugs, looking like early part of next week before you'll get automatic upgrade notification. Apparently.

---

### Post by Darth Trix on 2016-07-26
Any news? Still don get the option to upgrade from 14.04 to 16.04.1

---

### Post by PaulW2U on 2016-07-26
> **Darth Trix said:**
> Any news? Still don get the option to upgrade from 14.04 to 16.04.1
I've not seen or heard anything definite that I can quote or link to. All I've seen are vague references on IRC by those "in the know" mentioning upgrade testing.

---

