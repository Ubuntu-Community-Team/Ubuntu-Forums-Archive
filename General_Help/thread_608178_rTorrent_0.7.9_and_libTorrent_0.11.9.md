---
title: "rTorrent 0.7.9 and libTorrent 0.11.9"
date: 2007-11-09
forum: General Help
---

### Post by karvec on 2007-11-09
Just wondering if someone could test these packages for me, built deb files of the latest and greatest rTorrent and libTorrent (unstable) v 0.7.9 and v 0.11.9..  The files are located at:

[http://files-upload.com/files/609614/libtorrent_0.11.9-1_i386.deb](http://files-upload.com/files/609614/libtorrent_0.11.9-1_i386.deb)

[http://files-upload.com/files/609619/rtorrent_0.7.9-1_i386.deb](http://files-upload.com/files/609619/rtorrent_0.7.9-1_i386.deb)

Will move to a more permanent location if they work okay, please let me know if you get any errors.  Thanks!!

---

### Post by AlexTheMad on 2007-11-09
Nice job, rtorrent is definitively the best torrentclient out there. Unfortunately these debs didn't work for me

alexanbj@alex-desktop:~$ rtorrent
rtorrent: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory

---

### Post by karvec on 2007-11-09
Okay, thanks...  Can you install libcurl-dev and try again?

sudo apt-get install libcurl-dev

Also, changing the site:

[http://www.mediafire.com/?6ztjywecymg](http://www.mediafire.com/?6ztjywecymg)

and 

[http://www.mediafire.com/?cwr2yfxmbl1](http://www.mediafire.com/?cwr2yfxmbl1)

Thanks alot!!!

I will try to rebuild the package with that as a dependency...

---

### Post by AlexTheMad on 2007-11-09
just install the package libcurl4-openssl-dev and now it works like a charm! Thank you! :)

If you want to I can provide proper hosting of the files :)

---

### Post by karvec on 2007-11-10
That would be awesome, thanks for testing that out for me!!  I don't know how or where I could post this so that more people know about it, but if you want to host them that would be sweet.  Umm, you have the files {obviously} but I will work on the whole dependency thing--  Not sure if I should just tell people they need to get libcurl4-openssl-dev and then install it or actually figure out how to build the dependency in there...  What's your thoughts?

Reading about checkinstall tells me that you cannot actually build the dependencies in with it--  I'd have to use dh_make...  Will toy around with that for awhile.

**EDIT**  libcurl-openssl-dev should refer to that package, and also work.  so, without having to install a specific version...

---

### Post by Rocketeer on 2007-11-12
Hmm.... I installed the packages, but it did not work. I am recieving following error:

rtorrent: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory

and i also installed those libcurl3 pacakges....

---

### Post by AlexTheMad on 2007-11-12
Here are the files, hosted by my uni:

[http://folk.ntnu.no/alexanbj/linux/libtorrent_0.11.9-1_i386.deb](http://folk.ntnu.no/alexanbj/linux/libtorrent_0.11.9-1_i386.deb)
[http://folk.ntnu.no/alexanbj/linux/rtorrent_0.7.9-1_i386.deb](http://folk.ntnu.no/alexanbj/linux/rtorrent_0.7.9-1_i386.deb)

---

### Post by dunomous on 2007-11-18
These packages still produce the libcurl error message that previous users have reported.

---

### Post by karvec on 2007-11-19
I know, I have not yet generated the dependencies...  Haven't had a chance to use the computer for a week; part-AYYYYY!!!!

---

### Post by shirilover on 2007-11-20
The following is the list of depends for building rtorrent 0.7.8. There shouldn't be any difference for 0.7.9.
```

Build-Depends: debhelper (>= 5), cdbs, libtorrent-dev (>= 0.11.4), libsigc++-2.0-dev, libcurl4-openssl-dev, libncurses5-dev, bc, dpatch, patchutils

```

Building libtorrent also depends on libssl-dev.

Myself, I will continue to use the stable version and can make debs for Feisty available when the next stable version is released.

---

