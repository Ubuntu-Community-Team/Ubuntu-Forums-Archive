---
title: "Tomboy sync with owncloud"
date: 2014-08-31
forum: General Help
---

### Post by ELMIT on 2014-08-31
I have tomboy, owncloud on my 14.04 desktop installed. And I have on two Android devices tomdroid and several tries of Webdav clients.

The two android are syncing Tomboy's notes. However, no notebooks. Ok, might me a limitation for now.

See all the permissions:

cd /var/www/owncloud/data/RonNa/files

ls -la tomboy
total 16
drwxr-xr-x 3 www-data www-data 4096 Aug 31 08:51 .
drwxr-xr-x 6 www-data www-data 4096 Aug 31 08:42 ..
drwxrwxrwx 4 www-data www-data 4096 Aug 31 08:51 0
-rwxrwxrwx 1 www-data www-data  667 Aug 31 08:51 manifest.xml

ls -la tomboy/*/*
tomboy/0/0:
total 20
drwxrwxrwx 2 www-data www-data 4096 Aug 31 08:51 .
drwxrwxrwx 4 www-data www-data 4096 Aug 31 08:51 ..
-rwxrwxrwx 1 www-data www-data  860 Aug 18 03:30 8d892100-23e7-4957-b718-9b5c5c86d292.note
-rwxrwxrwx 1 www-data www-data 1254 Aug 18 03:30 d90d6278-bffb-4a26-be2a-5dbd2a0506ca.note
-rwxrwxrwx 1 www-data www-data  301 Aug 31 08:43 manifest.xml

tomboy/0/1:
total 40
drwxrwxrwx 2 www-data www-data 4096 Aug 31 08:51 .
drwxrwxrwx 4 www-data www-data 4096 Aug 31 08:51 ..
-rwxrwxrwx 1 www-data www-data 1424 Aug 31 08:51 430aad96-2c2b-4f06-b8ac-c240c33cb1d7.note
-rwxrwxrwx 1 www-data www-data  924 Aug 31 08:47 5e162cf4-d1e7-4bb4-ab3f-8ed9fbc47bfd.note
-rwxrwxrwx 1 www-data www-data  924 Aug 31 08:47 84aa57b8-1a13-4c70-ad06-6424f5d0ea33.note
-rwxrwxrwx 1 www-data www-data  918 Aug 31 08:51 892d3e99-74a5-40fd-853f-509b1bbd181a.note
-rwxrwxrwx 1 www-data www-data  843 Aug 31 08:45 990b6e51-9de1-46b5-86eb-000b16d7dc64.note
-rwxrwxrwx 1 www-data www-data  909 Aug 31 08:50 a91a2b09-c9c9-40f3-9152-89eae92cef11.note
-rwxrwxrwx 1 www-data www-data  918 Aug 31 08:50 bfd84ab3-16f7-41fa-b472-4b8a3594c3de.note
-rwxrwxrwx 1 www-data www-data  667 Aug 31 08:51 manifest.xml


grep www-data /etc/group
www-data:x:33:ronald


Tomboy I have setup to sync to Local Folder in  /var/www/owncloud/data/RonNa/files/tomboy

Sync (to local folder tomboy) gives me an error with detail (empty).
I tried therefore to setup the sync folder again.
When I want to save it, I get an error to see more details in the log file:

8/31/2014 1:19:59 PM [ERROR]: Unparsable last-sync-date '0001-01-01T00:00:00.0000000+08:00' in /home/ronald/.config/tomboy/manifest.xml

~/.config/tomboy$ cat manifest.xml 
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns="http://beatniksoftware.com/tomboy">
  <last-sync-date>0001-01-01T00:00:00.0000000+08:00</last-sync-date>
  <last-sync-rev>-1</last-sync-rev>
  <server-id>26354357-f80a-4375-bade-1659e9c07832</server-id>
  <note-revisions />
  <note-deletions />


How can I fix that?

---

### Post by ELMIT on 2014-09-01
I come closer, but cannot find a solution:

Notes created by the Android devices are stored with the owner    ronald:www-data
and so are available for Webdav clients.

Notes created by Linux have the ownership   ronald:ronald


The result is, that Linux has different notes than Android !!! What is on Android is not on Linux, what is on Linux is not on Android.

Any idea how to solve that?

---

### Post by xylometazolin on 2014-10-01
There is a also a new Tomboy sync server for ownCloud ([http://apps.owncloud.com/content/show.php?action=content&content=166654](http://apps.owncloud.com/content/show.php?action=content&content=166654)) which works well with Tomboy, Tomdroid and Conboy.

---

