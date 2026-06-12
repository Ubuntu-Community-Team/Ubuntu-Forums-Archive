---
title: "so I'm an idiot (apache2 help)"
date: 2013-01-13
forum: General Help
---

### Post by chaosadnd1 on 2013-01-13
Hi all, 

New poster to the forums but longtime lurker. I run an webserver on my home ubuntu 12.04 server, and host up a couple of small sites for my family. trying to cut down on the log error i was reading a thread to remove some files to make apache more secure, but can no longer access these sites from the web.

The list of files I deleted are:

/etc/apache2/mods-enabled/autoindex.load
/etc/apache2/mods-enabled/autoindex.conf
/etc/apache2/mods-enabled/dav.load
/etc/apache2/mods-enabled/dav_fs.conf
/etc/apache2/mods-enabled/dav_fs.load
/etc/apache2/mods-enabled/dav_lock.load

My attempt was to disable webdav and autoindex...but apparently they are needed. my https sites, and ones assigned ports are working fine. Just not the ones that dont have anything after .com. Is there a way to get these files back, or replace them so my links work again?

Thanks in advance!

---

### Post by mcduck on 2013-01-14
> **chaosadnd1 said:**
> Hi all, 

New poster to the forums but longtime lurker. I run an webserver on my home ubuntu 12.04 server, and host up a couple of small sites for my family. trying to cut down on the log error i was reading a thread to remove some files to make apache more secure, but can no longer access these sites from the web.

The list of files I deleted are:

/etc/apache2/mods-enabled/autoindex.load
/etc/apache2/mods-enabled/autoindex.conf
/etc/apache2/mods-enabled/dav.load
/etc/apache2/mods-enabled/dav_fs.conf
/etc/apache2/mods-enabled/dav_fs.load
/etc/apache2/mods-enabled/dav_lock.load

My attempt was to disable webdav and autoindex...but apparently they are needed. my https sites, and ones assigned ports are working fine. Just not the ones that dont have anything after .com. Is there a way to get these files back, or replace them so my links work again?

Thanks in advance!
Sure, the *mods-enabled* directory doesn't actually contain any files, only links to the actual files. Which are in the */etc/apache2/mods-available* -directory. So you can just create new links from there.

Also you should use the *a2enmod* and *a2dismod* commands when enabling/disabling various Apache mods.

---

