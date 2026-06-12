---
title: "Google earth - No pictures"
date: 2016-06-08
forum: General Help
---

### Post by Mal_Ellis on 2016-06-08
I have sucessfully installed Google earth on my Ubuntu 16.04 and it runs very smartly . My problem is that when I click on a photo it opens a blank box with not picture . Can I please get some help so that I can see the pictures.




HP I5 Laptop
500 Gb HDD
4 Gb RAM
Ubuntu 16.04

---

### Post by u-alex-8 on 2016-06-09
Try this...

cd /opt/google/earth/free/
sudo wget [https://googledrive.com/host/0B2F__nkihfiNalQzN0ZmcjBPTGs/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz](https://googledrive.com/host/0B2F__nkihfiNalQzN0ZmcjBPTGs/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz)
sudo tar xvf ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz

---

### Post by Mal_Ellis on 2016-06-09
Thank you for your reply .This is the result



  sudo wget [https://googledrive.com/host/0B2F__n...buntu12.tar.xz](https://googledrive.com/host/0B2F__n...buntu12.tar.xz)[sudo] password for mal: 
--2016-06-10 10:25:54--  [https://googledrive.com/host/0B2F__n...buntu12.tar.xz](https://googledrive.com/host/0B2F__n...buntu12.tar.xz)
Resolving googledrive.com (googledrive.com)... 216.58.199.65, 2404:6800:4006:800::2001
Connecting to googledrive.com (googledrive.com)|216.58.199.65|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com/host/0B2F__n...buntu12.tar.xz](https://324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com/host/0B2F__n...buntu12.tar.xz) [following]
--2016-06-10 10:25:55--  [https://324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com/host/0B2F__n...buntu12.tar.xz](https://324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com/host/0B2F__n...buntu12.tar.xz)
Resolving 324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com (324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com)... 216.58.199.33, 2404:6800:4006:801::2001
Connecting to 324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com (324b41175977bb4fb92ac539462c567220d9fea6.googledrive.com)|216.58.199.33|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz](https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz) [following]
--2016-06-10 10:25:56--  [https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz](https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz)
Resolving drive.google.com (drive.google.com)... 119.235.103.23, 119.235.103.30, 119.235.103.57, ...
Connecting to drive.google.com (drive.google.com)|119.235.103.23|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://accounts.google.com/ServiceLogin?continue=https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz](https://accounts.google.com/ServiceLogin?continue=https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz) [following]
--2016-06-10 10:25:56--  [https://accounts.google.com/ServiceLogin?continue=https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz](https://accounts.google.com/ServiceLogin?continue=https://drive.google.com/st/auth/host/0B2F__n...buntu12.tar.xz)
Resolving accounts.google.com (accounts.google.com)... 216.58.199.77, 2404:6800:4006:806::200d
Connecting to accounts.google.com (accounts.google.com)|216.58.199.77|:443... connected.
HTTP request sent, awaiting response... 400 Bad Request
2016-06-10 10:25:57 ERROR 400: Bad Request.

---

### Post by Impavidus on 2016-06-10
The forum software abridged the url in the visible text, but kept the full url as link target underneath. You need the full url in wget. Or – simpler – you can just click the link, save the download somewhere temporarily and then move it (with root permissions) to /opt/google/earth/free/, all instead of the wget command.

---

### Post by u-alex-8 on 2016-06-14
An excellent blog post here giving a full how to guide for installing Google Earth on 16.04 from scratch (including the fix for images). Worked like a charm for me. [URL="http://blog.pztop.com/2016/04/28/Install-Google-Earth-on-Ubuntu-16-04/"]

http://blog.pztop.com/2016/04/28/Install-Google-Earth-on-Ubuntu-16-04/[/URL]

---

