---
title: "Synaptic package manager can not uninstall MythTv"
date: 2016-07-16
forum: General Help
---

### Post by 4kh3RAm on 2016-07-16
Synaptic package manager can not uninstall MythTv.

I performed a complete removal, but it is still present.

What else can I do to get rid of that program ?

---

### Post by Bucky Ball on 2016-07-16
Had a search? [First link, post four]("https://www.google.com.au/#q=completely+uninstall+mythtv"). They seem to have found a fix.

Presuming you installed it with Synaptics? Helps if you are more specific. MythTV is still there. What's there? The entry in your apps menu? And presume if that is the case, as you've 'completely removed' MythTV, it doesn't open MythTV when you click the entry anymore?

---

### Post by 4kh3RAm on 2016-07-16
It was still in menu and still functioning.

I found the fix though I forgot where.

I had to manually delete some MythTv files.

It was still in menu, so I removed it.

There are still some files around but no big deal.

If I get too aggressive in deleting files, I may break something else and end up with a Frankenubuntu. :-)

---

### Post by Bucky Ball on 2016-07-16
Try this. It lets you know what it is about to remove and gives you the option to say no, although it is generally fine to click 'Y'.

```
sudo apt-get autoremove
```

---

### Post by 4kh3RAm on 2016-07-16
I do not know if other programs need these ??

```
The following packages will be REMOVED:
  fonts-droid-fallback fonts-texgyre libarchive-zip-perl
  libclass-factory-util-perl libclass-inspector-perl libclass-methodmaker-perl
  libclass-singleton-perl libcommon-sense-perl libconvert-binhex-perl
  libdate-manip-perl libdatetime-format-builder-perl
  libdatetime-format-iso8601-perl libdatetime-format-strptime-perl
  libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl
  libdbd-mysql-perl libdbi-perl libemail-address-perl libemail-find-perl
  libemail-valid-perl libexporter-lite-perl libexporter-tiny-perl
  libfile-chdir-perl libfile-slurp-perl libhtml-fromtext-perl
  libhtml-tableextract-perl libhttp-cache-transparent-perl
  libhttp-server-simple-perl libio-sessiondata-perl libio-stringy-perl
  libjs-jquery libjson-perl libjson-xs-perl liblingua-preferred-perl
  liblist-moreutils-perl liblog-tracemessages-perl libmime-tools-perl
  libmodule-implementation-perl libmodule-runtime-perl libmyth-0.28-0
  libmyth-python libmythtv-perl libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libnet-upnp-perl libossp-uuid-perl libossp-uuid16
  libpackage-deprecationmanager-perl libpackage-stash-perl
  libpackage-stash-xs-perl libparams-classify-perl libparams-util-perl
  libparams-validate-perl libparse-recdescent-perl libqt5opengl5 libqt5webkit5
  libquicktime2 libregexp-common-perl libsoap-lite-perl libsox-fmt-alsa
  libsox-fmt-base libsox2 libsub-install-perl libtask-weaken-perl
  libterm-progressbar-perl libterm-readkey-perl libtext-bidi-perl
  libtry-tiny-perl libtypes-serialiser-perl libwww-mechanize-perl
  libxml-dom-perl libxml-libxml-perl libxml-libxslt-perl
  libxml-namespacesupport-perl libxml-perl libxml-regexp-perl
  libxml-sax-base-perl libxml-sax-expat-perl libxml-sax-perl
  libxml-simple-perl libxml-treepp-perl libxml-writer-perl libxmlrpc-lite-perl
  libxmltv-perl php-mysql php-mythtv php7.0-mysql pwgen python-bs4
  python-html5lib python-imaging python-imdbpy python-lxml python-mysqldb
  python-pil python-pycurl python-urlgrabber s
```

---

### Post by Bucky Ball on 2016-07-16
Have you, by any chance, done a lot of installing and removing programs? If so, should be safe. 

All these appear to be related to perl which suggests there was a program there before that isn't there now. In other words, they may all be related to a program that is no longer there. It could be that they were related to MythTV. When you remove things with Synaptics, do you use 'Complete removal' or just remove? Try this and see what it throws up.

```
sudo apt-get --purge remove mythtv
```

Not sure if it is mythtv or myth-tv. You better check, but use the right one.

If a package is shared and required by another app, it is generally not offered for autoremove.

---

### Post by 4kh3RAm on 2016-07-16
It looks like it gave me the same list.

I installed Clonezilla so if something went corrupt or I deleted to much, I could restore a disk image.

Clonezilla worked once, then failed at next 5 attempts.

I need a disk imager that works in Ubuntu.

---

### Post by Bucky Ball on 2016-07-17
Clonezilla works fine for me. Did you do exactly the same thing with the failed attempts as you did with the first? I use fsarchiver myself nowadays. 

Anyway, that is the stuff of another thread and if you want help with Clonezilla, please post a new thread about it. Back to the problem at hand, run
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

That will get your current install up to date (it will _not_ upgrade you to a newer release). Reboot and see what you've got.

---

### Post by 4kh3RAm on 2016-07-17
It worked well.

MythTv no longer shows up in Main Menu.

---

### Post by Bucky Ball on 2016-07-17
Great to hear it, thanks for marking 'solved', enjoy. :)

* Note: Those autoremove and update commands I posted are handy to run every now and then. I update/upgrade only using terminal and use those three. For 16.04, although those work, you can also forget the '-get' and there's a slightly different command:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

---

