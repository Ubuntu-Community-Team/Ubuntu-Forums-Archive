---
title: "connect Android MTP to ubuntu"
date: 2013-07-10
forum: General Help
---

### Post by hnf a on 2013-07-10
hi all, i want to ask why my mtp android phone cannot connect to ubuntu? i've try gmtp and qlix and few tutorial like [http://www.mysolutions.it/mounting-your-mtp-androids-sd-card-on-ubuntu/](http://www.mysolutions.it/mounting-your-mtp-androids-sd-card-on-ubuntu/) and [http://askubuntu.com/questions/177555/managing-kindle-fire-with-on-12-04-via-micro-usb](http://askubuntu.com/questions/177555/managing-kindle-fire-with-on-12-04-via-micro-usb) >this one give me "Transport endpoint is not connected Please select another viewer and try again". so is in here have similiar problem like  me?

---

### Post by hansdown on 2013-07-10
Hi  hnf a.

Have you tried connecting with bluetooth?

---

### Post by scbingham on 2013-07-10
Apparently the woes of connecting to newer android phones have been resolved in Ubuntu 13.04, all the necessary needed to connect via mtp are included. I haven't tried it yet as 12.04 plays nicely with my old 2.2 android.

---

### Post by hnf a on 2013-07-10
@hansdown : hi too, not yet but i think it can be done but i don't want that type of connection because well it's a bit complicated beside i don't have any bluetooth hardware in my pc
@scbingham: what a good news, but i can't do that beside the short term support maybe i'll upgrade to another LTS version of ubuntu but it's still way to long for me to wait, is there any way to make 12.04 possible to read my handphone using 13.04 software?

---

### Post by 3rdalbum on 2013-07-10
Think laterally... your Ubuntu can browse FTP servers, right? And you can probably find an app on the Google Play Store to run an FTP server on your phone, right? You can connect to wifi on both devices, right?

This works well. My dad does this on Ubuntu 12.10 with his Nexus 7. If you don't have a wifi network you can just start tethering or wifi tethering on the phone to act as the network.

---

### Post by scbingham on 2013-07-10
"[COLOR=#000000]is there any way to make 12.04 possible to read my handphone using 13.04 software?"

You can search through the forums but I get the impression it's not really doable. As 3rdalbum suggests, install FTP server s/w on your phone. This seems to be a common work around.

Good luck.[/COLOR]

---

### Post by vanadium on 2013-07-10
Thry this: [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

---

### Post by efflandt on 2013-07-10
Some useful Android apps if MTP does not work (assuming you have WiFi):
ConnectBot (ssh client, may want to set larger than default font)
AndFTP (client for sftp or scp)
SSH Server (to connect ssh, scp, or sftp to phone from Linux)

Since I always have Ubuntu sshd set to use keys only, I use those same openssh keys on the phone (Samsung Galaxy S3).

---

### Post by hnf a on 2013-07-13
thanks all for the support finally i've found what i looking for it almost work flawlessly [http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html?m=1](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html?m=1) even it has some "scanning media" issue for me, but in short time i'll use FTP methode for a while

---

### Post by vanadium on 2013-07-13
You probably did not check the link I provided you, which is somewhat more recent and allows to install the mpt support like it exists in 13.04 to 12.10 and 12.04.

---

### Post by hnf a on 2013-07-13
actually i've check it and run it for a while but because i'm not a very smart when using terminal it did not work very well, so i check for the go-mtpfs inside your recommended page, btw thanks for your link

---

### Post by moeadham on 2013-09-23
> **vanadium said:**
> Thry this: [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

This worked right away for me. Thanks!

---

### Post by sheldon-b on 2014-01-19
> **vanadium said:**
> Thry this: [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

Worked like a charm:)

---

### Post by nmyrick on 2014-04-03
Well, if the issues were resolved in 13.04, they re-appeared in 13.10.  I've tried several of the supposed solutions and they do not work.  I've tried installing go-mtpfs, and mtp-tools, and neither one works.  

 I have a Moto X with Android 4.4.2, and the best that I can do is to set up an FTP connection with Bluetooth.  Even when I do that, I still cannot open the Music folder, and neither Banshee nor RhythymBox recognize the phone as a mounted device.

When trying to open the Music folder in nautilus, I get the error "cannot parse the incoming data", which i have found is probably due to some odd characters in some file names.

Any help with getting MTP to work would be great.

Also, my computer does not have any USB 3.0 ports, so I'm just working with USB 2.0

---

