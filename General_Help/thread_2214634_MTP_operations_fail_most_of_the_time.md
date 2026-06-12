---
title: "MTP operations fail most of the time"
date: 2014-04-02
forum: General Help
---

### Post by halfbeing on 2014-04-02
I am using UbuntuStudio (XFCE) but I believe that this problem is relevant to all variants.

When I try to transfer photos from my Android phone I usually find that the transfer hangs on one particular photo for no obvious reason. No matter how much I plug/unplug or reboot my phone, it will hang on the same photo. I also find that when I unplug the phone and reconnect it it fails to mount properly and appear in Thunar. Either it appears in the left hand panel with the list of short cuts, but no folders show up, or it simply does not appear in the left hand panel. I have just spent an hour trying to copy 150 or so photos from my phone, but I still have not succeeded. Everything I read on the web tells me that MTP support in Ubuntu used to be very bad, but that everything works brilliantly with the most recent versions. Yet I have 13.10 and am finding it all but unusable. Is there a way to get MTP support into some kind of usable state?

EDIT: I have copied the photo that was causing the operations to stall [here]("https://drive.google.com/file/d/0B4gbytYYRJ-BUXpWWEJ4d0dqT28/edit?usp=sharing"). It turns out that this time round it was the only one of nearly 200 photos, all taken with the same device, that Ubuntu wasn't happy with. The device in question is a Sony Xperia P.

---

### Post by SeijiSensei on 2014-04-02
MTP support seems even more stable in the forthcoming 14.04 release than it did in 13.10.

There are methods for transferring files using wifi like the [Wifi File Transfer Pro](https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en) app or something like [Acrosync]("https://play.google.com/store/apps/details?id=com.acrosync.android.plus").

---

### Post by halfbeing on 2014-04-02
if you are right about MTP support being improved, that is good news. I got by today with a mixture of MTP plus the free version of File Transfer Pro for the file that wouldn't move. Thanks for giving me some hope!

---

### Post by efflandt on 2014-04-02
I had no trouble with MTP in Ubuntu 13.10 USB connected to Samsung S3. Except that I could not open files (image files, etc.) on the phone, I first had to copy them to Linux.

But because I could never could get MTP working properly in 12.04, useful Android apps I have on the phone are **AndFTP** (gui sftp client), **SSHServer** (to ssh or sftp to the phone from Linux client), and **ConnectBot** (ssh client), all using my Linux ssh key either direction. So those can transfer files either way through WiFi.

---

