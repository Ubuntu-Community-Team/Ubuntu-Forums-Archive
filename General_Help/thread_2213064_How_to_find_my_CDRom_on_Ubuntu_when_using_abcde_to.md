---
title: "How to find my CDRom on Ubuntu when using abcde to rip CD's to mp3"
date: 2014-03-24
forum: General Help
---

### Post by greavette on 2014-03-24
Hello,

I'm using this thread to assist with ripping my CD's to MP3's:  [http://ubuntuforums.org/showthread.php?t=109429](http://ubuntuforums.org/showthread.php?t=109429)

I know..it's a little out of date but it appears complete so I'm hoping it will still work.

My question is during the setup of abcde it says to change my CD Drive from the default CDROM=/dev/cdrom to something else.  How do I find what to use for my CD Drive?

Also, is there a slick way for abcde to use the title of the CD for the folder where it rips too? 

Thank you.

---

### Post by mc4man on 2014-03-24
run this & look in below section for /dev/srX (usually 0 or 1
*-cdrom 

```
sudo lshw -C disk
```

---

### Post by greavette on 2014-03-24
Thanks for the reply...so when I run this I see the following:

  ```
*-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7190A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```

So you're saying in my abcde config file I would use /dev/sr0 to denote my CD Drive?

Thanks!

---

### Post by mc4man on 2014-03-24
> **greavette said:**
> 
So you're saying in my abcde config file I would use /dev/sr0 to denote my CD Drive?

Thanks!
That 's the one..

---

