---
title: "Apache2 &amp; PHP folder access"
date: 2023-09-26
forum: General Help
---

### Post by unbuntunewbie02 on 2023-09-26
Hi,

I have LAMP server running on Ubuntu and samba which works correctly.

The LAMP server is look at var/www/html and the Apache\PHP is running correctly as www-data

My Shared-Drive for Samba is on /home/desktop/share-drive/ owned by the group webserver I have added the webserver user to the www-data group and www-data user to webserver group so the PHP can look at the home/desktop/share-Drive

But I am getting errors advising it cannot open the file stream if i do this on Windows and change the stream file location it works correctly.

I have used Webmin to edit the groups and setup my SAMBA can anyone advise how I can get Apache\PHP to read the txt file in the share-drive.

I am very new to Ubuntu and usually a Windows Admin so if any further info is required please ask.

---

### Post by TheFu on 2023-09-26
The short answer is "Don't use samba for Unix systems."  
The longer answer is that CIFS as implemented by non-MSFT system doesn't support permissions in the same way, so you will always be fighting the differences.  For read-only data, not programs, this can be fine, but not for anything else.  You'll spend far too much time trying to get things working.

BTW, 
var/www/html and /var/www/html are NOT the same places.  Please use absolute paths for servers on Linux.  Also, \ is an escape character, so just get in the habit of using / on all OSes. It works the same on Windows BTW and has since MS-DOS v1.0, perhaps earlier.

As for webmin, especially when you are knew, it is best not to use it.  Little issues that it creates are easy to fix, but not if you only know the webmin way. Plus, it is almost always setup incorrectly and becomes yet another attack vector for bad guys.  For server management, learn to use ssh, that's it. Nothing else.  AFTER you have that solved, then you'll have the necessary skills to setup a webgui for quick management needs or to help less knowledgeable people just starting out.

I completely understand that less knowledgeable people really want the "easy way" - I wanted that too.  And I was told about the same thing I'm trying to say by grey beards.  It was really frustrating.

I know you won't listen.  So, if you really want more help from other php wizards, you'll need to provide the **ls -al** for the locations that aren't working.  Don't make us guess.  You can remove most of the files, but leave a few files and the current+parent directory in the list.  Also, please wrap the output using forum code tags, so columns line up correctly. Without that, it is too hard to read.  Make it easy for people to help you. Please.   Text is always preferred when posting here, BTW.  With text the information isn't bloated and people can highlight/copy/paste the issues.

---

### Post by unbuntunewbie02 on 2023-09-26
As asked please see ls -al of the locations:

```

webserver@webserver-01:/var/www/html/SupportDesk$ ls -al
total 108
drwxr-xr-x 8 webserver webserver  4096 Sep 26 09:18 .
drwxr-xr-x 3 webserver webserver  4096 Sep 25 15:02 ..
drwxr-xr-x 3 webserver webserver  4096 Jul 22  2022 docs
drwxr-xr-x 2 webserver webserver  4096 Jul 22  2022 FavIcon
-rw-r--r-- 1 webserver webserver  7105 Jan 12  2023 Functions.php
drwxr-xr-x 2 webserver webserver  4096 Jun 14 14:59 Images
-rw-r--r-- 1 webserver webserver  4854 Jul 22  2022 Index1.php
-rw-r--r-- 1 webserver webserver  7240 Jul 19  2022 Index.html
-rw-r--r-- 1 webserver webserver 13126 Sep 26 10:32 Index.php
drwxr-xr-x 2 webserver webserver  4096 Sep 18 12:00 Logs
drwxr-xr-x 2 webserver webserver  4096 Sep 18 10:07 Logs-OLD
-rw-r--r-- 1 webserver webserver    22 Jun 28  2022 phpinfo.php
-rw-r--r-- 1 webserver webserver   301 Jun 30  2022 SqlConn.php
-rw-r--r-- 1 webserver webserver  5834 Aug  2 16:14 TestFile.txt
-rw-r--r-- 1 webserver webserver  7048 Jul 22  2022 test.html
-rw-r--r-- 1 webserver webserver  2263 Aug  3 16:32 Test.php
drwxr-xr-x 2 webserver webserver  4096 Jul 22  2022 Toast
-rw-r--r-- 1 webserver webserver  1347 Jul 19  2022 ToastTester.php
-rw-rw-r-- 1 webserver webserver   991 Sep 26 10:06 WUCounts.php

```

```

webserver@webserver-01:~/Desktop/Share-Drive$ ls -al
total 28
drwxrwxr-x 7 webserver webserver 4096 Sep 26 09:08 .
drwxr-xr-x 4 webserver webserver 4096 Sep 26 10:10 ..
drwxrwxrwx 2 webserver webserver 4096 Sep 25 15:08 CCTV
drwxrwxrwx 2 webserver webserver 4096 Sep 25 15:08 Clocking-In
drwxrwxrwx 2 webserver webserver 4096 Sep 25 15:17 KMS-CRM
drwxrwxrwx 2 webserver webserver 4096 Sep 26 09:59 Office-5
drwxrwxrwx 2 webserver webserver 4096 Sep 25 15:08 SQL

```

```

webserver@webserver-01:/var/www/html$ ls -al
total 24
drwxr-xr-x 3 webserver webserver  4096 Sep 25 15:02 .
drwxr-xr-x 4 root      root       4096 Sep 25 11:22 ..
-rw-r--r-- 1 webserver webserver 10671 Sep 25 10:42 index.html
drwxr-xr-x 8 webserver webserver  4096 Sep 26 09:18 SupportDesk

```

Basically a separate app will send logs to the Share-Drive and the php app reads the logs and gathers the info on a Windows box this works fine.

Anymore info please ask.

---

### Post by TheFu on 2023-09-26
Typically, the webserver runs as www-data on Ubuntu. I shouldn't be important, since the web server doesn't need anything except read for the files there, right?

Hummmm. The more I think about this, the more I think it is related to the CIFS mount being in your HOME.  Some distros have tightened security of the HOME directories in the last few years, so you'll need to check the access levels allowed for every parent directory up to the root, / directory.

```
$ ls -l  /home/
drwxr-x--- 183 thefu   thefu   495 Sep 26 14:22 thefu/

```
See how 'other' doesn't have any permissions?  That means no other accounts can access anything deeper.

Also, all those files with 777 permissions are just asking to be deleted when your server is hacked.

From a security standpoint, the program files should all be read-only to the www-data user and group.  Only the files that need to be modified by the www-data user should be in the group with write permissions. Same for any directories where new files might be created, perhaps an uploads/ directory.  For example, my wallabag server:
```
$ ll /var/www/wallabag/html/web
total 23
drwxrwsr-x  8 root     root        14 Oct  1  2021 ./
drwxrwsr-x 14 root     root        40 Mar  3  2023 ../
-rw-rw-r--  1 root     root      1093 Oct  1  2021 app_dev.php
-rw-rw-r--  1 root     root       494 Oct  1  2021 app.php
drwxrwsr-x  3 root     root         3 Oct  1  2021 assets/
...
drwxrwsr-x  3 root     root         6 Jul 24  2022 img/
drwxrwsr-x  2 root     root         3 Jul 24  2022 js/
-rw-rw-r--  1 root     root      1158 Oct  1  2021 manifest.json
-rw-rw-r--  1 root     root        26 Oct  1  2021 robots.txt
**drwxrwsr-x  3 www-data www-data     3 Oct  1  2021 uploads/**
drwxrwsr-x  5 root     root         7 Mar  3  2023 wallassets/
```
I'm using nginx for the webserver here. This stuff shouldn't matter - any php webapp would be setup similarly.

Try moving the CIFS mount to /opt/something ... modify the app settings to look there as needed, and try it.  CIFS isn't really a great file sharing solution.

---

### Post by SeijiSensei on 2023-09-27
If this is a Linux client connecting to a Linux webserver, you should use NFS to connect to your machine, or if the server is in a remote location, something like sftp. CIFS makes no sense outside a Windows environment.

I've found sshfs to be a convenient method as well. See, for instance,[https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh](https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh). The "allow_other" parameter is important if you want to share the files with different users.

---

