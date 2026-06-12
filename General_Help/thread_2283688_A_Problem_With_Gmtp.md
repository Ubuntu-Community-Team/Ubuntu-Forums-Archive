---
title: "A Problem With Gmtp"
date: 2015-06-23
forum: General Help
---

### Post by wbee on 2015-06-23
((Edit. I was playing around with the phone and discovered that the Gmtp software had installed the files in the USB storage area. Thinking that the menu might have been backwards,I tried again,and instead of choosing the SD card option,I choose the USB storage area. Again,the same thing occurred. It put the file in the USB storage area.

I downloaded the newest drivers and the same thing occurred.

I went into launchpad and discovered some three year old bug reports---but that the newest stable release is a year old,so I left a question asking if they could update the Synaptic Package Manager download to the newest stable one.

That said,thank you for the two responses so far.))




Hello,

I'm running 12.04lts and attempting to download music from my desktop computer to an Android phone's MP3 section.

I have a SD card installed in the phone. The SD card is mounted and the debugging tic is unchecked. The Android version is 4.0.4.

Using the Synaptic Package Manager,I download and installed Gmpt and the associated library.

I was able to rip music from CDs using VLC with no problem,putting those into the file system on the desk top computer.

When I opened the Gmpt and hit connect,it took a long time,but it did connect and recognize the SD card,including giving the correct capacity.

I used the correct function on the Gmpt screen to access the files system and get it to the Gmpt screen,but it would not send the files to the Android phone. It kept running me around in a circle between the Gmpt screen and the file system,telling me the file was already there and asking me to either ignore it or override it.

Realizing the problem might be a driver to download to the phone,which is an Android question,I ask here first,because of the expertise of this forum's membership.

How do I solve this problem?

---------------

Thank you.

---

### Post by jamesisin on 2015-06-23
Not sure.  When I attach my Android phone to my Ubuntu system (and enable debugging) my phone's storage appears in Nautilus (Ubuntu's native file browser), I mount it using Nautilus (by selecting it in the side-bar), and add files using Nautilus (typically drag-and-drop).

---

### Post by Ty_Scheun on 2015-06-23
[COLOR=#111111][FONT=Ubuntu]I gave up trying to get MTP support on Linux for the moment.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is the solution I use now:[/FONT][/COLOR]

[LIST=1]
[*]On your Android device, install [FTP Server]("http://f-droid.org/repository/browse/?fdfilter=FTP%20Server&fdid=be.ppareit.swiftp_free") (it's free and open source)
[*]On your Ubuntu computer, install Filezilla
[*]Make sure both your computer and your Android device are connected to the same WiFi network
[*]On Android, launch FTP Server, and check "Running". It will provide you an IP and a port.
[*]In Filezilla, connect to yoru Android device using these information, and ftp/ftp as login/password (you can change this in FTP Server if you want)
[*]You can then navigate into your device from your Ubuntu computer! I usually use this to transfer music on my Android Samsung Galaxy S3 (I put it in /storage/extSdCard/ directory)
[/LIST]

---

### Post by wbee on 2015-06-24
It turns out the Gmtp software was working fine.

No place in the three hundred page Android phone owner's manual did it say how to select storage options for music.

But it did provide the way to select storage options for the camera. I set the storage option for the camera to the SD card,and volia! it worked for music files as well,sending those to the SD card.

Thanks

------------

WB

---

