---
title: "Samsung Android phone can't connect Ubuntu"
date: 2021-08-19
forum: General Help
---

### Post by satimis on 2021-08-19
Hi all,

Ubunbu 20.04
Samsung Galaxy S9+
Samsung Galaxy S6

After several updates my Samsung Android phones can't connect my PC.  USB connection cables are the same.  Ubuntu 20.04 detects the phones but selecting "Allow" on phones can't connect PC.  Before it worked seamlessly.

Please help.  Thanks in advance

Regards

---

### Post by tea for one on 2021-08-19
Ubuntu 20.04 with Gnome 3.36.7
Android 10

Power on phone
Connect phone to PC with USB cable
Open settings on phone
Connected devices
USB
File transfer

Open Files (nautilus) on PC

Both internal storage and SD card (if installed) should be visible.

---

### Post by satimis on 2021-08-19
> **tea for one said:**
> Ubuntu 20.04 with Gnome 3.36.7
Android 10

Power on phone
Connect phone to PC with USB cable
Open settings on phone
Connected devices
USB
File transfer

Open Files (nautilus) on PC

Both internal storage and SD card (if installed) should be visible.
Hi,

Thanks for your advice.

I couldn't find "Connected devices" under settings of my Android phones

Regards

---

### Post by tea for one on 2021-08-19
[U]Second option after opening Settings
[/U]
Network & Internet
[COLOR="#0000FF"]Connected Devices[/COLOR]
Apps & Notifications
Battery
Display
Etc.

---

### Post by satimis on 2021-08-19
> **tea for one said:**
> [U]Second option after opening Settings
[/U]
Network & Internet
[COLOR="#0000FF"]Connected Devices[/COLOR]
Apps & Notifications
Battery
Display
Etc.
Sorry, no such an item "Network & Internet" under Settings on both phones

Regards

---

### Post by tea for one on 2021-08-19
Looks like Samsung, in their infinite wisdom, have deviated a bit from usual Android menus.

Within Settings, do you have any option with the word [COLOR="#0000FF"]Connection(s)[/COLOR] at all?

---

### Post by satimis on 2021-08-19
> **tea for one said:**
> Looks like Samsung, in their infinite wisdom, have deviated a bit from usual Android menus.

Within Settings, do you have any option with the word [COLOR="#0000FF"]Connection(s)[/COLOR] at all?
Yes.  There are 13 items under.

Now I can connect "Samsung Gallaxy S9+" on Ubuntu 20.04 Folder showing "Phone" on the right column

-> Phone```

301Gimbal
amap
Android
androrec
backups
baidu
cache
callrecorder
callrecorder
com.facebook.orca
data
DCIM
DJI
Documents
...
etc

```

Video and photos taken are retaind on DCIM
-> DCIM```

Abum_20200601
DJI MIMO
Screenshots
ZYPlay
```

clicking Abum_20200601 showing an empty folder.

On "Samsung Gallaxy S9+" phone -> Gallery -> Albums
showing all video and photos there.

Warning on PC
=======```

Unable to access "SAMSUNG Adroid"
unable to open MTP device "003,003"
```

On Terminal run;
$ apt policy mtp-tools```

mtp-tools:     
  Installed: 1.1.17-3
  Candidate: 1.1.17-3
  Version table:
 *** 1.1.17-3 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
```

mtp-tools already installed

$ apt policy mtpfs```

N: Unable to locate package mtpfs

```

mtpfs not available on repo

Any suggestion?  Thanks

Regards

---

### Post by tea for one on 2021-08-19
Samsung have an uncanny knack of making users jump through some hurdles........?

There is a package called [COLOR="#0000FF"]go-mtpfs[/COLOR] with the description
```
Go-mtpfs is a simple FUSE filesystem for mounting Android devices as
an MTP device.
```

I've no idea if this what you need because, using the Android 10 version with my phone, I didn't have to install anything to connect to Ubuntu.

I would have a look at your phone manual and/or Android forums pertaining to Samsung devices.

---

### Post by ajgreeny on 2021-08-19
I use an Android app names **WiFi File Transfer** which when started on the phone allows you to open a browser on the Linux machine, presumably any distro, and navigate to the IP shown in the phone app.
It has worked faultlessly for me, particularly for photos, but I assume will work for other files, I've just never needed nor tried that.

---

### Post by ActionParsnip on 2021-08-19
I personally use AndFTP and send the files to an from my phone use SFTP. No cable needed. You'll need openssh-server installed on the Ubuntu system. Secure and easy

---

### Post by satimis on 2021-08-19
> **tea for one said:**
> Samsung have an uncanny knack of making users jump through some hurdles........?

There is a package called [COLOR="#0000FF"]go-mtpfs[/COLOR] with the description
```
Go-mtpfs is a simple FUSE filesystem for mounting Android devices as
an MTP device.
```

I've no idea if this what you need because, using the Android 10 version with my phone, I didn't have to install anything to connect to Ubuntu.

I would have a look at your phone manual and/or Android forums pertaining to Samsung devices.
go-mtpfs already installed.

It is very strange to me.  File transfer from both S9+ and S6 to/from Ubuntu 20.04 worked before without problem.  I haven't used this function sometimes.  Just discovered that it doesn't work, same USB cable.

Regards

---

### Post by satimis on 2021-08-19
> **ajgreeny said:**
> I use an Android app names **WiFi File Transfer** which when started on the phone allows you to open a browser on the Linux machine, presumably any distro, and navigate to the IP shown in the phone app.
It has worked faultlessly for me, particularly for photos, but I assume will work for other files, I've just never needed nor tried that.
Install WiFi File Transfer on S9+ and start it

Enter the IP address on Firefox of Ubuntu 20.04.  It is very strange the Album folder empty

Regards

---

### Post by ajgreeny on 2021-08-20
Look in the other folders, pictures, images and camera.
I don't use albums so can't help with that.

---

### Post by satimis on 2021-08-20
> **ajgreeny said:**
> Look in the other folders, pictures, images and camera.
I don't use albums so can't help with that.
Phone ->```

302Gimbal
amap
Android
andrprec
.....
DCIM
DJI
....
....
ZYPlay
...
...

```

Under DCIM
=======```

Album_20200601
DJI MIMO
Screenshots
ZYPlay

```

Only these 4 folders.  All of them are empty folders.  It is very strange to me.

On Phone -> ZYPlay (another folder with same name)```

album
Camera

```

-> album
also an empty folder
-> Camera
also an empty folder

Regards

---

### Post by satimis on 2021-08-20
Hi ajgreeny,

I found out the trick.  I need to capture new video.  Then a new folder named "Camera" will be automatically created under DCIM and the new video will be saved in the new folder.

Start WiFi File Transfer on S9+ phone and browse the URL on Ubuntu 20.04.  Then download the new video mp4 files on PC.

Where are those old video mp4 files?  I can't find them on browser.  But they are still on S9+ phone.  I suppose needing to download them on a SIM card.

Regards

---

### Post by ajgreeny on 2021-08-20
I have no idea where those files will be in the Android filesystem, I'm afraid, as the Android filesystem is a complete mystery to me, and I use it as a phone only, and almost never download any files except the occasional attachment in an email.

---

### Post by satimis on 2021-08-22
> **ajgreeny said:**
> I have no idea where those files will be in the Android filesystem, I'm afraid, as the Android filesystem is a complete mystery to me, and I use it as a phone only, and almost never download any files except the occasional attachment in an email.
I have been using Samsung Galaxy S6 and S9+ as camera, taking video and photos for prolonged time.  All video and photos are stored on DCIM.  I can download them to my PC without problem.  

I just discovered that all video and photos taken in the past disappear.  It is very strange to me.  I found them on Photos NOT on Gallery on desktop but I have not idea to download them to my PC.

---

### Post by him610 on 2021-08-22
++Wifi file transfer Pro
> Where are those old video mp4 files? I can't find them on browser. But they are still on S9+ phone. I suppose needing to download them on a SIM card.
This is a pretty interesting thread. Can't recall ever using Wifi file transfer Pro (WFTP), but it's on my phone so I figured I would see what I could do with it.

Your jpg and mp4 files should be found under the WFTP File Browser tab in Current Directory: /storage/emulated/0/DCIM/Camera/
Click the checkbox for the file you wish to save to your computer then click download.
[COLOR="#FF0000"]Important!![/COLOR] It should bring up a window with heading, 'Save File' - you need to remember which directory the file gets written to, or you can specify which directory it gets written to. I have mine going into Pictures/scratch. It may take a little while to transfer a video file depending on its size. The one I downloaded was 268 MB and it took a few seconds.

I found videos that I had forgotten about.

---

### Post by satimis on 2021-08-23
> **him610 said:**
> ++Wifi file transfer Pro

This is a pretty interesting thread. Can't recall ever using Wifi file transfer Pro (WFTP), but it's on my phone so I figured I would see what I could do with it.

Your jpg and mp4 files should be found under the WFTP File Browser tab in Current Directory: /storage/emulated/0/DCIM/Camera/
Click the checkbox for the file you wish to save to your computer then click download.
[COLOR="#FF0000"]Important!![/COLOR] It should bring up a window with heading, 'Save File' - you need to remember which directory the file gets written to, or you can specify which directory it gets written to. I have mine going into Pictures/scratch. It may take a little while to transfer a video file depending on its size. The one I downloaded was 268 MB and it took a few seconds.

I found videos that I had forgotten about.
Hi,

Thanks for your advice.

It is very strange to me.  I couldn't find "Storage" folder on browser

The recently taken video;
-> DCIM -> Camera
20210821_105537.mp4
20210821_110456.mp4

-> Samsung
400 Bad Request

I found all old video and photos are on "Google Photos" on my Samsung Galaxy S9+

I have no idea how to download them to PC.  "Share" doesn't work because file size exceeding the limit allowed.

Regards

---

### Post by Paulgirardin on 2021-08-30
Hi 
May I suggest the GSConnect Gnome Shell extension and Android app?

"GSConnect is a complete implementation of KDE Connect especially for GNOME Shell with Nautilus, Chrome and Firefox integration. It does not rely on the KDE Connect desktop application and will not work with it installed.

KDE Connect allows devices to securely share content like notifications or files and other features like SMS messaging and remote control. The KDE Connect team has applications for Linux, BSD, Android, Sailfish and Windows."

[https://extensions.gnome.org/extension/1319/gsconnect/](https://extensions.gnome.org/extension/1319/gsconnect/)

---

