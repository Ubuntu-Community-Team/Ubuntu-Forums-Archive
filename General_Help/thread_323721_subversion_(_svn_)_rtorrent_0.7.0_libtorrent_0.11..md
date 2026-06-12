---
title: "subversion ( svn ) rtorrent 0.7.0 libtorrent 0.11.0 encryption support"
date: 2006-12-22
forum: General Help
---

### Post by vimchi on 2006-12-22
I'm attempting to build the **subversion** ( svn ) **rtorrent 0.7.0** with **libtorrent 0.11.0** since it supports **encryption**.

One issue appears during the build:  a **PKG_CONFIG_PATH** error.

Everything is fine until ./configure is called for rtorrent, which then throws this message.
```
Requested 'libtorrent >= 0.11.1' but version of libtorrent is

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```

The developoment environment packages all look good and aren't compaining.  I believe it's the PKG_CONFIG_PATH that's somehow causing the barf.

I run this script with sudo to do the svn install, which illustrates PKG_CONFIG_PATH setup and where all the svn files live.
```
PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
export PKG_CONFIG_PATH

cd /home/user/rtorrent/trunk
svn up
cd libtorrent
./autogen.sh
./configure
make
make install

cd ../rtorrent
./autogen.sh
./configure
make
make install
```

---

### Post by magnastiks on 2006-12-29
Hello vimchi

I was able to get rtorrent 0.7.1 and libtorrent 0.11.1 working compiling from source (a first for me) following the directions [here]("http://notes.minty.org/cgi-bin/wiki.pl?Upgrading_To_The_Latest_Rtorrent_And_Libtorrent_On_Ubuntu").

There were some difficulties installing libcurl3-dev libcurl3-openssl-dev libcurl3-gnutls-dev together, as apt would only allow 2 of the 3 at a time.  I was not able to resolve this, but tried configure and make(ing) anyway from the libtorrent then rtorrent source and was sucessful.

I'm glad there is an encrypted alternative for dapper that doesn't require either wine, java, or kdelibs; even though it took some time to get used to the interface.  I got a sample rtorrent.rc from [here]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=835&format=raw").

---

### Post by vimchi on 2006-12-29
ok! cool.  Thanks for the links.  I'll give this another go.

---

### Post by anywebloco on 2007-01-05
How did you go? I had the same issue as you originally had and haven't been able to resolve it yet...

---

### Post by SailBlue5 on 2007-01-29
I tried the link and installed rtorrent 0.7.1 with it with out a problem (I had many problems doing it prior to that link). I just replaced the versions I wanted of libtorrent and rtorrent where needed.

---

### Post by mancuso on 2007-02-25
I get this when I run the second line [Upgrading To The Latest Rtorrent And Libtorrent On Ubuntu]("http://notes.minty.org/cgi-bin/wiki.pl?Upgrading_To_The_Latest_Rtorrent_And_Libtorrent_On_Ubuntu")



>  sudo aptitude install curl libcurl3-dev libcurl3-openssl-dev libcurl3-gnutls-dev

```
Building tag database... Hecho      
The following packages are BROKEN:
**  libcurl3-dev **
The following packages have been automatically kept back:
  linux-image-server 
The following NEW packages will be automatically installed:
  comerr-dev libcurl3 libcurl3-gnutls libgcrypt11-dev libgnutls-dev 
  libgpg-error-dev libidn11 libidn11-dev libkadm55 libkrb5-dev liblzo-dev 
  libopencdk8-dev libpopt-dev libtasn1-3-dev pkg-config 
The following NEW packages will be installed:
  comerr-dev curl libcurl3 libcurl3-gnutls libcurl3-gnutls-dev 
  libgcrypt11-dev libgnutls-dev libgpg-error-dev libidn11 libidn11-dev 
  libkadm55 libkrb5-dev liblzo-dev libopencdk8-dev libpopt-dev 
  libtasn1-3-dev pkg-config 
0 packages upgraded, 18 newly installed, 0 to remove and 1 not upgraded.
Need to get 20,8kB/4007kB of archives. After unpacking 11,2MB will be used.
[B]The following packages have unmet dependencies:
  libcurl3-dev: Depende: libcurl3-openssl-dev (= 7.15.4-1ubuntu2) but it is not installable[/B]
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libcurl3-dev [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] 
```

Anything to worry about ? 

I´m running ubuntu server 6.10 kernel 2.6.17-10-server i686

---

