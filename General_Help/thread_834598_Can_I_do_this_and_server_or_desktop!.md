---
title: "Can I do this? and server or desktop!?"
date: 2008-06-19
forum: General Help
---

### Post by I_need_help2 on 2008-06-19
Hi
  I'm look for a "server" for my home that can do the following:

Server files
server printers
server media to my Xbox 360 and PS3 (doesn't need to transcode just pictures and mp3's)
restrict access to shares by user
run ftp server



optionaly 
Itunes server 
VPN Server

It will be installed on a 3.2Ghz Intel box 1Gb ram, 3 * Hdu
Os to go on HDU 1 (350gb IDE), HDU 2 & 3 as software RAID 1 (500Gb SATA).

A lot to ask I know!

Freenas is great and does a lot of it but not the print serving :(

A friend said Ubuntu could, I have tried the desktop but after installing it on the IDE I can find not way to setup the software raid!

I know windows OSs but this is a first for me!

---

### Post by russlar on 2008-06-19
> **I_need_help2 said:**
> Hi
  I'm look for a "server" for my home that can do the following:

Server files
server printers
server media to my Xbox 360 and PS3 (doesn't need to transcode just pictures and mp3's)
restrict access to shares by user
run ftp server



optionaly 
Itunes server 
VPN Server

It will be installed on a 3.2Ghz Intel box 1Gb ram, 3 * Hdu
Os to go on HDU 1 (350gb IDE), HDU 2 & 3 as software RAID 1 (500Gb SATA).

A lot to ask I know!

Freenas is great and does a lot of it but not the print serving :(

A friend said Ubuntu could, I have tried the desktop but after installing it on the IDE I can find not way to setup the software raid!

I know windows OSs but this is a first for me!

I don't know of any software raid that will work on ubuntu, as most software raid is, as the name implies, software, and most likely is written for windows,

---

### Post by I_need_help2 on 2008-06-19
> **russlar said:**
> I don't know of any software raid that will work on ubuntu, as most software raid is, as the name implies, software, and most likely is written for windows,

Hi Thanks for your reply, however it appears that server does support software Raid 1.

also supports file and print serving...

now anyone know how to get a media server on to it?

---

### Post by bodhi.zazen on 2008-06-19
samba will do most of what you are asking. You can restrict shares to specific users with samba.

to run a ftp server, install one. If you are behind a router, ftp is probably fine, otherwise look at vsftp or proftp.

what do you mean be "server media" ? will samba do this ?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

[https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)

---

### Post by I_need_help2 on 2008-06-19
Thank you.

Re media server I mean a UPnP server to server pictures, MP3s and video to both an Xbox360 and a PS3.

---

