---
title: "Command to format vfat32"
date: 2023-04-17
forum: General Help
---

### Post by satimis on 2023-04-17
Hi all.

Just purchased a SanDisk Extreme portable USB 3.2 SSD V2 1TB capacity.

Please advise how to format it as fat32 so that it can be detected by Android device such as phone?

Thanks

Regards

---

### Post by satimis on 2023-04-17
**Problem solved.**

I found out the trick.  Format the SanDisk USB Portable SSD on Andriod phone, not on Ubuntu 22.04 PC.

Following YouTube video gives me a hint;
Connect SanDisk SSD to Samsung Galaxy Phone | Transfer Files, Videos and Images, Format and Eject
[https://www.youtube.com/watch?v=f4tRx976weM](https://www.youtube.com/watch?v=f4tRx976weM)

After connecting SanDisk USB Portable SSD to the Android phone (in my case Galaxy S22 Ultra), scroll the menu down at the left top corner of the phone.  A warning displayed there saying - an unsupported device found
Format it ?

Click "Yes".  Afterwards the SanDisk USB Portable SSD can be connected and displayed on my Samsung Galaxy Phone.  Files copied on Ubuntu 22.04 PC to SanDisk USB Portable SSD can be displayed on my Samsung Galaxy Phone.
[B][COLOR="#FF0000"]
It took me several hours to find this solution[/COLOR][/B]

Regards

---

### Post by yancek on 2023-04-19
There are numerous sites explaining how to format as vfat from Linux such as the one below.

[https://phoenixnap.com/kb/linux-format-disk](https://phoenixnap.com/kb/linux-format-disk)

---

### Post by HermanAB on 2023-04-19
Gparted???

---

### Post by satimis on 2023-04-19
deleted because of duplication

Sorry

---

### Post by satimis on 2023-04-19
Hi all,

I have no problem to format a new External SSD device as vfat, vfat32, ext4 file systems etc.  The device with those formats works without problem on Linux computers except Android phones.

Android Phone
**[COLOR="#FF0000"]Filesystem type = exfat[/COLOR]**

The device must be formatted on Android phone. exfat also works on Liunx.

Just found following link;
how to install exfat-utils and hddtemp on ubuntu 22.04
[https://askubuntu.com/questions/1403900/how-to-install-exfat-utils-and-hddtemp-on-ubuntu-22-04](https://askubuntu.com/questions/1403900/how-to-install-exfat-utils-and-hddtemp-on-ubuntu-22-04)

I'll try it when I purchase another SanDisk USB Portable SSD 

Remark:
**[COLOR="#FF0000"]SanDisk Extreme portable USB 3.2 SSD V2 [/COLOR]**
is a wonderful device for sharing large data amongst Linux computers and Android phones

Rapid moving/duplicating files around.

Regards

---

