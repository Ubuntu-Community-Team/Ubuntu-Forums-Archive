---
title: "transfer photo from android"
date: 2017-10-15
forum: General Help
---

### Post by Matrix01 on 2017-10-15
File, "My favorite" in  Android does not show in PCManFM.
Like to transfer photo,
what to do?

---

### Post by Autodave on 2017-10-15
Cl,ick on VIEW and make sure that HIDDEN files are shown. If you don't see it then, you need to go into the phone itself and into SETTINGS. Somewhere in there you will find something referring to allowing sharing with a PC. You need to enable that.

---

### Post by Cavsfan on 2017-10-16
You can also use Airdroid which uses Wi-Fi to transfer files to and from your android phone/PC.
[https://play.google.com/store/apps/details?id=com.sand.airdroid&hl=en](https://play.google.com/store/apps/details?id=com.sand.airdroid&hl=en)

I've been using it for a couple of years.

---

### Post by vasa1 on 2017-10-16
There's KDE Connect as well: [http://www.omgubuntu.co.uk/2017/02/easy-way-connect-android-to-ubuntu-pc](http://www.omgubuntu.co.uk/2017/02/easy-way-connect-android-to-ubuntu-pc)

---

### Post by efflandt on 2017-10-18
I am not familiar with PCManFM, but what happens if you view directories/files on the phone instead of using gphoto?

I was using **AndFTP** Android app to sftp files to or from my phone back when Ubuntu 12.04 did not support MTP yet, and still use it even though 14.04 and newer support MTP. For AndFTP you would need to install **openssh-server** in Ubuntu, which should also install **openssh-sftp-server**. I also have ssh client and server apps on my phone. Android ssh apps can use Linux ssh keys if you use those for better security.

Note that newer Android versions block write permission from internal storage to added storage (SD/microSD) for many apps. So I have 1 AndFTP connection configured for local "internal" storage and another connection configured for local "external" storage (microSD). And /sdcard in internal storage is not really your SD card, that loops back to internal storage. The path to SD or microSD is actually /storage/0000-0000, which if you formatted the card yourself would be UUID of the card instead of 0000-0000. But when connected to internal storage you can only read from the card, not write to it.

---

### Post by Matrix01 on 2017-10-30
"hidden file" is always checked.

---

