---
title: "Where does my Samsung Tablet PTP actually mount?"
date: 2013-06-29
forum: General Help
---

### Post by geekyhawkes on 2013-06-29
Hello;

having been tearing my hair out for months trying to get USB mass storage working on my Samsung Note 10.1 tablet I have given up, just not an option.  I am now looking at making the most of PTP (MTP doesnt work as I have a lot of "hidden" folders to sync with my apps and MTP ignores all folders beginning with .) 

I am left with PTP as I see it, it doesnt work great but I think I could bash script something to make it work, the problem I have is I cannot find where the device is mounted.  I am using Xubuntu / XFCE4 and the device appears in thunar and on the desktop, but I cannot find it in the filesystem anywhere!

Thanks for the help;

Andy

---

### Post by Mark Phelps on 2013-06-29
I don't know what file manager you're using, but I'm a fan of Gnome-Commander and it has an option (turned off by default) of viewing hidden files.  You should check if your file manager has that option, as well.

---

### Post by cwsnyder on 2013-06-29
PTP mounts your Samsung Note as a camera _only_.  The best luck I have had with my Samsung Galaxy 2.0 7 inch tablet is with the Kies app, Airdroid app, or using an FTP app on the tablet connecting with Filezilla on my desktop, all working through wireless connection.  I have had no luck connecting through USB.

The other method which I know works requires a microSD card and adapter to my desktop machine, transferring all data through the SD card.

---

### Post by efflandt on 2013-06-29
In (64-bit) 12.04 have not had any luck with MTP with my Samsung Galaxy SIII (nautilus only shows root directories, not contents of directories) and with PTP it only shows internal storage (not my microSD), so I have resorted to using ssh related apps. With **AnyFTP** I can sftp to Ubuntu or with **SSH Server** app I can scp or sftp from Ubuntu to my phone, using my Linux openssh key (I have root login and ssh passwords disabled in Ubuntu). It is easiest using sftp from the phone to copy filews to/from my phone using **AnyFTP** app on WiFi (since sftp from Ubuntu is text based instead of gui).

---

