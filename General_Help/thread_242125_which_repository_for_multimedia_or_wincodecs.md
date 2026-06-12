---
title: "which repository for multimedia or wincodecs?"
date: 2006-08-23
forum: General Help
---

### Post by eeried on 2006-08-23
Hello,

Now that ciperfunk is dead [http://64.71.152.24/index.html]("http://64.71.152.24/index.html")
is there another repository?

I do not wish to use EasyUbuntu or Automatix because I don't need much: only the win codecs. I know I can get them from the Mplayer website but I was wondering if there was a special repository for Ubuntu, like cipherfunk was.

Thanks in advance for your help!

---

### Post by aeiah on 2006-08-23
i know this comment may seem ignorant due to what you said about automatix, but it will install only the things you select, not everything. so you can have it only install your codecs

---

### Post by aeiah on 2006-08-23
if you still dont want automatix cluttering things up, then this should help:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Irony on 2006-08-23
You can get the latest codecs from here;

[http://www.mikesplanet.net/?p=38](http://www.mikesplanet.net/?p=38)

Simply download them and use the GDebi installer to install them.

---

### Post by visik7 on 2006-08-23
Seveas and plf has that package

---

### Post by yopnono on 2006-08-23
## Debian Multimedia Repository
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main


There you have codecs, acrobat etc,etc

Just import the key and you will not get any auth errors.

---

### Post by eeried on 2006-08-23
Sorry for sounding so ignorant -- last time I read this forum about Automatix, it didn't say you could choose what you can install. this is good news as I think Automatix sounds very good.

I don't trust PLF -- sorry for being ignorant again, certainly.

Yes, I know debian-multimedia -- I'm using this repository on my Debian -- but my belief was "don't use Marillat repository with Ubuntu" unless you really know what you're doin --I read that in a Breezy thread which advised to use cipherfunk instead.

Mike's Planet looks quite all right! Thank you Irony!

---

### Post by yopnono on 2006-08-23
> **eeried said:**
> 
Yes, I know debian-multimedia -- I'm using this repository on my Debian -- but my belief was "don't use Marillat repository with Ubuntu" unless you really know what you're doin --I read that in a Breezy thread which advised to use cipherfunk instead.

May I ask why not? I have so far never have any problems using the debian-multimedia on ubuntu.

---

### Post by eeried on 2006-08-23
I've no idea why, yopnono, but my impression is Ubuntu packages are  different from Debian packages and it can be dangerous to mix up both.

 Here's the thread where I got some information --  page 2 is where cipherfunk was advised over marillat (now debian-multimedia):
[Howto Win32 codecs by tseliot]("http://www.ubuntuforums.org/showthread.php?t=75278")

BTW I've found the deb packages for libdvdcss on the videolan website as Mike's Planet doesn't seem to have them:
[http://downloads.videolan.org/pub/videolan/libdvdcss/]("http://downloads.videolan.org/pub/videolan/libdvdcss/")

*caveat:* I don't know if libdvdcss is legal all over the world. I'm not inciting anyone to use it!

Cheers :-\"

---

### Post by yopnono on 2006-08-23
> **eeried said:**
> I've no idea why, yopnono, but my impression is Ubuntu packages are  different from Debian packages and it can be dangerous to mix up both.

 Here's the thread where I got some information --  page 2 is where cipherfunk was advised over marillat (now debian-multimedia):
[Howto Win32 codecs by tseliot]("http://www.ubuntuforums.org/showthread.php?t=75278")

BTW I've found the deb packages for libdvdcss on the videolan website as Mike's Planet doesn't seem to have them:
[http://downloads.videolan.org/pub/videolan/libdvdcss/]("http://downloads.videolan.org/pub/videolan/libdvdcss/")

*caveat:* I don't know if libdvdcss is legal all over the world. I'm not inciting anyone to use it!

Cheers :-\"

Ok. Well I have no idea either. Since like I said, never had any problems using the codecs or acrobat reader from that site. Thanks anyway.

---

### Post by Treviño on 2006-09-06
Some multimedia packages from cipherfunk are still available, but not into a repository: [http://64.71.152.24/ubuntu/multimedia-packages-for-dapper-6.06/](http://64.71.152.24/ubuntu/multimedia-packages-for-dapper-6.06/)

Anyone could make a repository for them (sites like tuxfamily.org gives you free space and bandwidth for this...)?

---

### Post by Anduu on 2006-09-06
> **eeried said:**
> Yes, I know debian-multimedia -- I'm using this repository on my Debian -- but my belief was "don't use Marillat repository with Ubuntu" unless you really know what you're doin --I read that in a Breezy thread which advised to use cipherfunk instead.

You should be OK to use that repo as long as it doesn't contain any core Ubuntu/Linux type files like Gnome,Nautilus,libc6 among many others.Basically if it contains any lib***** type stuff avoid it.

---

