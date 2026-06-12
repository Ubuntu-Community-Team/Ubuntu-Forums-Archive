---
title: "curlftpfs &amp; curl &amp; feisty bug"
date: 2007-04-26
forum: General Help
---

### Post by blackfire on 2007-04-26
Hello everyone,
 I've just upgraded to feisty and I'm now experiences serious problems with curlftps: it will simply freeze from time to time (VERY often).
I think the bug is related to this one ([http://sourceforge.net/tracker/index.php?func=detail&aid=1635141&group_id=160565&atid=816357](http://sourceforge.net/tracker/index.php?func=detail&aid=1635141&group_id=160565&atid=816357))

I downgraded libcurl to the dapper package and now curlftpfs is working OK so we've got our man I think, but my system is in an unstable state right now (downgraded = dpkg -i, so I've got plenty of unmatched dependencies now :( ).

Any idea?

---

### Post by pelleke on 2007-05-18
The problem is known, and can be solved either by downgrading libcurl to version 7.15.4 (or 7.14, I always forget the right one) or (better!) upgrade it to 7.16.2. 

The only way I found so far to upgrade it, is install 7.15.5 via apt (otherwise you'll get some dependency-troubles) and then compile 7.16.2 yourself and replace all libcurl.so.x with the new ones.

---

### Post by alepar on 2007-06-16
Have this bug too.
Method by pelleke works, though it would be great to see updated package at least in backports.

PS Dont forget to enable gnutls while configuring curl, and to update libcurl-gnutls links in your /usr/lib

---

### Post by mburris on 2007-07-10
ok so I have downloaded the source for libcurl-7.16.2 from [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

then I made sure i had installed the build esentials...

then i did a ./configure and then make to compile...

can you be a little more specific on the rest of the process?

---

### Post by mburris on 2007-07-10
Ok I think I just about there... but i need help with the libcurl-gnutls files... here is what i've done so far:


downloaded [source for libcurl]("http://archive.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.16.2.orig.tar.gz") 7.16.2 from the Gusty Package Repo, Then extracted them to /usr/src

Change folder to the source location and get root permissions
```
sudo su
cd /usr/src/curl-7.16.2
```


installed libgnutls-dev to give me the "/usr/bin/libgnutls-config" file the ./configure process needs.
```
apt-get install libgnutls-dev
```

I then had to edit _both_ the _configure and configure.ac files_ (located where I extracted the source  /usr/src/curl-7.16.2 for me) to change the line:
```
      GNUTLS_ENABLED = 1
```
to
```
      GNUTLS_ENABLED=1
```

then i configured (the kinda of pre-make step) the libcurl makefile with
```
./configure --with-ssl --with-gnutls
```

then i compiled with make
```
make
```
this will compile the code and put the libcurl files in a hidden folder: /usr/src/curl-7.16.2/lib/.libs

then after that, ran the install
```
make install
```

This copied the files libcurl.so.* to /usr/local/lib, from here I would move it to the /usr/lib folder but for the life of me, I can't figure out what to do with libcurl-gnutls files... I cant find any that were created by the make/make install process

---

### Post by mburris on 2007-07-15
bump

---

### Post by Boelcke on 2007-10-02
mburris, did you ever figure this one out?  Or find an answer somewhere else?

I'm running in Dapper, and need to upgrade from libcurl 7.15.1 to get CurlFtpFS to work.  I was figuring on getting libcurl 7.15.4 (which is what the [_CurlFtpFS_]("http://curlftpfs.sourceforge.net/") website recommends), but I'm also not sure of all the steps required to get it working without messing up dependencies.

---

