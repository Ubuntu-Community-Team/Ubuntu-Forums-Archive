---
title: "Problem with BTG in ubuntu 7.10"
date: 2007-11-11
forum: General Help
---

### Post by Pazzeo on 2007-11-11
Hi all,

I try to install btg ( a bit-torrent client) on my ubuntu server 7.10, but i have a problem with configure. 
The error is in the end of  the configure that terminates with this error:

```
configure: Link test, compiler flags: -g -O2   -I/usr/include -I/usr/include
configure: Link test, linker flags  :
            -lboost_iostreams -lboost_filesystem -lboost_date_time
            -lboost_thread -lboost_program_options
            -ltorrent   -lgnutls
checking if BTG can link with the provided/found libraries... no
configure: error: Unable to link with required libraries.

```

How can I resolve this problem?

Thank you very much

Pazzeo

---

### Post by glurgle on 2007-12-14
What version are you compiling? I managed to get 0.9.5 up and running, but with SVN I'm in the same boat, according to the BTG Howto there should be a clue in config.log, but all I get at the end is this:

```
#define GNUTLS_MAJOR_VER 1
#define GNUTLS_MINOR_VER 6
#define HAVE_BOOST_IOSTREAMS
#define HAVE_BOOST_FILE
#define HAVE_BOOST_DATE_TIME
#define HAVE_BOOST_THREAD
#define HAVE_BOOST_PROGRAM_OPTIONS
#define HAVE_NCURSES_H

configure: exit 1
```

I'll post back if I figure it out

---

### Post by glurgle on 2007-12-16
Ok so I now have 0.9.6 RC4 up and running, but still not SVN.

What I ended up doing was installing the libtorrent packages from the [btg debian repository]("ftp://ftp.berlios.de/pub/btg/debian/dists/unstable/main/binary-i386/") 

In order to install the dev package you will need libasio-dev installed. Since this package doesn't exist in the repositories I made it myself:

```
cvs -z3 -d:pserver:anonymous@asio.cvs.sourceforge.net:/cvsroot/asio co -P libasio-dev
cd asio
./configure --prefix=/usr
sudo checkinstall
```

Make sure to fix the package version (was 0.3.9 at the time this was written)

With that done I was able to install the libtorrent-rasterbar-0.12-dev package.

and after all that the ./configure for BTG works perfectly :)

---

### Post by minenok on 2008-02-09
i managed to configure using this package [http://packages.ubuntu.com/hardy/devel/libasio-dev](http://packages.ubuntu.com/hardy/devel/libasio-dev)

Your solution was fine excluding missing libasio-dev, thanks!

your line
[q]cvs -z3 -d:pserver:anonymous@asio.cvs.sourceforge.net:/cvsr oot/asio co -P libasio-dev[/q]
did not work for me. 

so i got libasio friom here

[http://nl.archive.ubuntu.com/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb)

(it was missing in on some mirrors like this [http://debian.charite.de/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb](http://debian.charite.de/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb))

---

### Post by minenok on 2008-02-09
i managed to configure using this package [http://packages.ubuntu.com/hardy/devel/libasio-dev](http://packages.ubuntu.com/hardy/devel/libasio-dev)

Your solution was fine excluding missing libasio-dev, thanks!

your line
```
cvs -z3 -d:pserver:anonymous@asio.cvs.sourceforge.net:/cvsr oot/asio co -P libasio-dev
```
did not work for me. 

so i got libasio friom here

[http://nl.archive.ubuntu.com/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb)

(it was missing in on some mirrors like this [http://debian.charite.de/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb](http://debian.charite.de/ubuntu/pool/universe/a/asio/libasio-dev_0.3.8~rc3-2_all.deb))

---

