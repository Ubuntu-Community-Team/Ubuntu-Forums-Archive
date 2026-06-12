---
title: "Can't Copy/Move Files to External HD on 14.04 Server"
date: 2014-09-28
forum: General Help
---

### Post by Carl_Gitchel on 2014-09-28
Other threads I've read have not helped me in this situation. If you know of one which will, please advise...

I'm putting together a home file server using 14.04 Ubuntu Server.  The tower has a small 40GB HD to which I have mounted a 500GB USB external.  This is an NTFS drive I once had on a WinXP tower I was using as a file server.  It has my entire music collection, photo album and business related files on it.

I have successfully installed Plex and can access the music.  I have Samba and OpenSSH installed and I work with Putty to admin this machine remotely.

The road block I'm hitting is in adding additional music files to the external HD.  I have managed to find the file tree on the drive through WinSCP, but when I try to move files from my laptop (Win 7) to the external HD through WinSCP I get an error message saying I don't have permission to write to the directory.

I have added a directory to the HD and (I believe) given it the permissions needed to add/edit files.  But this apparently does not cover the files and folders already on the drive.

How do I give these permissions to the existing files?  Or do I need to move my entire music collection to the new directory on the drive and re-configure Plex to read the new directory?

Thanks for any feedback you may have.  It's really appreciated.

---

### Post by nerdtron on 2014-09-28
Which username are you using to login on WinSCP?
On the server, type the following command. Post the output here.
```
id username
```
We need to see the permissions. On the server, go to the directory on which you want to save files and post the output of the following command:
```
 ls -lah 
```



BTW: You're using WinSCP? I think Filezilla offers a better interface and much more options in transferring files to/from the server using a windows machine.

---

### Post by Carl_Gitchel on 2014-09-29
Sorry, it took me a little time to figure out the path to the hard drive I was trying to reach.  But it did help me figure out the problem I'm having, which is an important step to discovering a solution...

id carl:  uid=1000(carl) gid=1000(carl) groups=1000(carl),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),110(sambashare)
carl@ubuserver:/media/elements$ ls -lah
total 8.0K
drwxrwxrwx  2 root root 4.0K Sep 26 04:59 .
drwxr-xr-x 12 root root 4.0K Sep 26 05:07 ..


ls -lah =



Disk /dev/mapper/ubuserver--vg-swap_1 doesn't contain a valid partition table
carl@ubuserver:~$ ls /media/elements
carl@ubuserver:~$ cd /media/elements
carl@ubuserver:/media/elements$ ls -lah
total 8.0K
drwxrwxrwx  2 root root 4.0K Sep 26 04:59 .
drwxr-xr-x 12 root root 4.0K Sep 26 05:07 ..
carl@ubuserver:/media/elements$ ^C
carl@ubuserver:/media/elements$ cd
carl@ubuserver:~$ cd /media/usb0/



carl@ubuserver:/media/usb0$ ls -lah
total 1.4M
drwxr-xr-x 29 root root  32K Dec 31  1969 .
drwxr-xr-x 12 root root 4.0K Sep 26 05:07 ..
drwxr-xr-x  3 root root  32K Apr  5 03:01 26d15d0f332f239367723b5b925b27
drwxr-xr-x  2 root root  32K Aug 15 21:57 56b9ccde4d50e18a0970e9df249198
drwxr-xr-x  3 root root  32K Jan 20  2014 5f6a868b7dd0e25a8da0f96e07611fc3
drwxr-xr-x  3 root root  32K Apr  7 03:01 7a14400ebb690b378c8141
drwxr-xr-x  3 root root  32K Apr  6 03:05 938197f6454fcde992f2c23f
drwxr-xr-x  2 root root  32K Feb  9  2006 autorun
-r-xr-xr-x  1 root root   36 Oct 17  2002 autorun.inf
drwxr-xr-x  3 root root  32K Apr  4 03:01 b39edb1b0a49becf4e182369
drwxr-xr-x 18 root root  32K Oct 15  2008 Backup Documents
drwxr-xr-x  2 root root  32K May 11  2011 Business Matters
drwxr-xr-x  3 root root  32K Apr  3 03:01 ca857105bd26b29e01b080
drwxr-xr-x 13 root root  32K Sep 20  2010 Carl Laptop Backup
drwxr-xr-x  3 root root  32K Apr  8 03:01 cd730989861edef9109e95eb432c
drwxr-xr-x  6 root root  32K May 26  2013 CFG Material
drwxr-xr-x  5 root root  32K Nov 17  2013 CFG Videos
drwxr-xr-x  4 root root  32K Dec 15  2012 Copywriting Resources
drwxr-xr-x  6 root root  32K Aug  5 22:21 CZbackups
drwxr-xr-x  3 root root  32K Apr  9 03:02 e0a5564b609ddf7188
drwxr-xr-x  4 root root  32K Oct 20  2013 f47461ed6b119123faedf89e8b
drwxr-xr-x 12 root root  64K Nov 22  2012 Media
-rwxr-xr-x  1 root root 258K Feb  3  2013 MONTHCAL2013_february (3).doc
-rwxr-xr-x  1 root root  77K Oct 10  2009 .pdf
drwxr-xr-x 18 root root  32K Jan  3  2009 Recipes
drwxr-xr-x  4 root root  32K Apr  2  2013 $RECYCLE.BIN
drwxr-xr-x  2 root root  32K Sep  5  2008 Recycled
drwxr-xr-x 14 root root  32K Apr  9  2011 RHHD
drwxr-xr-x  8 root root  32K Oct 28  2010 Shared .exe Programs
drwxr-xr-x  5 root root  32K Sep  5  2008 System Volume Information
-rwxr-xr-x  1 root root 7.0K Jun  4  2011 Thumbs.db
drwxr-xr-x  2 root root  32K Apr 23 16:10 Video Camera Dump
drwxr-xr-x  5 root root  32K Sep  8  2012 WI Wedding Site
carl@ubuserver:/media/usb0$

I have figured out that the directory I created (called "elements") is not the same thing as the content of "Elements" hard drive, which has been its name since I first started using it.  So I have an empty "elements" directory which I granted all the permissions to when I created the server, and the existing content in the media/usb0 directory I don't know how to change.

I will check out Filezilla&#8212;that option never occurred to me.

Thank you so much for your help and your lightning fast reply!  I hope you can help me figure this out.

---

### Post by nerdtron on 2014-09-29
So I guess your external hard drive is mounted /media/usb0 right?
Now you want to copy files on this directory while you are logged in as chris right?
Then try taking ownership of the /media/usb0 folder (you'll be asked for your password, the password won't appear on the screen while you enter it)
```
sudo chown -R chris:chris /media/usb0
```

To check that you successfully taken ownership of the folder:
```
cd /media/usb0
ls -lah
```

---

### Post by Carl_Gitchel on 2014-09-29
Below is what the -lah command brought up...no change on the WinSCP program.  But, there were continuous "Operation not permitted" comments when I ran the chown command.

carl@ubuserver:/media/usb0$ ls -lah
total 1.4M
drwxr-xr-x 29 root root  32K Dec 31  1969 .
drwxr-xr-x 12 root root 4.0K Sep 26 05:07 ..
drwxr-xr-x  3 root root  32K Apr  5 03:01 26d15d0f332f239367723b5b925b27
drwxr-xr-x  2 root root  32K Aug 15 21:57 56b9ccde4d50e18a0970e9df249198
drwxr-xr-x  3 root root  32K Jan 20  2014 5f6a868b7dd0e25a8da0f96e07611fc3
drwxr-xr-x  3 root root  32K Apr  7 03:01 7a14400ebb690b378c8141
drwxr-xr-x  3 root root  32K Apr  6 03:05 938197f6454fcde992f2c23f
drwxr-xr-x  2 root root  32K Feb  9  2006 autorun
-r-xr-xr-x  1 root root   36 Oct 17  2002 autorun.inf
drwxr-xr-x  3 root root  32K Apr  4 03:01 b39edb1b0a49becf4e182369
drwxr-xr-x 18 root root  32K Oct 15  2008 Backup Documents
drwxr-xr-x  2 root root  32K May 11  2011 Business Matters
drwxr-xr-x  3 root root  32K Apr  3 03:01 ca857105bd26b29e01b080
drwxr-xr-x 13 root root  32K Sep 20  2010 Carl Laptop Backup
drwxr-xr-x  3 root root  32K Apr  8 03:01 cd730989861edef9109e95eb432c
drwxr-xr-x  6 root root  32K May 26  2013 CFG Material
drwxr-xr-x  5 root root  32K Nov 17  2013 CFG Videos
drwxr-xr-x  4 root root  32K Dec 15  2012 Copywriting Resources
drwxr-xr-x  6 root root  32K Aug  5 22:21 CZbackups
drwxr-xr-x  3 root root  32K Apr  9 03:02 e0a5564b609ddf7188
drwxr-xr-x  4 root root  32K Oct 20  2013 f47461ed6b119123faedf89e8b
drwxr-xr-x 12 root root  64K Nov 22  2012 Media
-rwxr-xr-x  1 root root 258K Feb  3  2013 MONTHCAL2013_february (3).doc
-rwxr-xr-x  1 root root  77K Oct 10  2009 .pdf
drwxr-xr-x 18 root root  32K Jan  3  2009 Recipes
drwxr-xr-x  4 root root  32K Apr  2  2013 $RECYCLE.BIN
drwxr-xr-x  2 root root  32K Sep  5  2008 Recycled
drwxr-xr-x 14 root root  32K Apr  9  2011 RHHD
drwxr-xr-x  8 root root  32K Oct 28  2010 Shared .exe Programs
drwxr-xr-x  5 root root  32K Sep  5  2008 System Volume Information
-rwxr-xr-x  1 root root 7.0K Jun  4  2011 Thumbs.db
drwxr-xr-x  2 root root  32K Apr 23 16:10 Video Camera Dump
drwxr-xr-x  5 root root  32K Sep  8  2012 WI Wedding Site

---

### Post by nerdtron on 2014-09-29
> But, there were continuous "Operation not permitted" comments when I ran the chown command.

You haven't made any changes. Did you run the chown command with sudo? Did it asked for your password?

---

### Post by Carl_Gitchel on 2014-09-29
I was in root before, so I didn't sudo.

This time I backed out and repeated the steps exactly as you directed.  I'm afraid I achieved the same result...

```

total 1.4M
drwxr-xr-x 29 root root  32K Dec 31  1969 .
drwxr-xr-x 12 root root 4.0K Sep 26 05:07 ..
drwxr-xr-x  3 root root  32K Apr  5 03:01 26d15d0f332f239367723b5b925b27
drwxr-xr-x  2 root root  32K Aug 15 21:57 56b9ccde4d50e18a0970e9df249198
drwxr-xr-x  3 root root  32K Jan 20  2014 5f6a868b7dd0e25a8da0f96e07611fc3
drwxr-xr-x  3 root root  32K Apr  7 03:01 7a14400ebb690b378c8141
drwxr-xr-x  3 root root  32K Apr  6 03:05 938197f6454fcde992f2c23f
drwxr-xr-x  2 root root  32K Feb  9  2006 autorun
-r-xr-xr-x  1 root root   36 Oct 17  2002 autorun.inf
drwxr-xr-x  3 root root  32K Apr  4 03:01 b39edb1b0a49becf4e182369
drwxr-xr-x 18 root root  32K Oct 15  2008 Backup Documents
drwxr-xr-x  2 root root  32K May 11  2011 Business Matters
drwxr-xr-x  3 root root  32K Apr  3 03:01 ca857105bd26b29e01b080
drwxr-xr-x 13 root root  32K Sep 20  2010 Carl Laptop Backup
drwxr-xr-x  3 root root  32K Apr  8 03:01 cd730989861edef9109e95eb432c
drwxr-xr-x  6 root root  32K May 26  2013 CFG Material
drwxr-xr-x  5 root root  32K Nov 17  2013 CFG Videos
drwxr-xr-x  4 root root  32K Dec 15  2012 Copywriting Resources
drwxr-xr-x  6 root root  32K Aug  5 22:21 CZbackups
drwxr-xr-x  3 root root  32K Apr  9 03:02 e0a5564b609ddf7188
drwxr-xr-x  4 root root  32K Oct 20  2013 f47461ed6b119123faedf89e8b
drwxr-xr-x 12 root root  64K Nov 22  2012 Media
-rwxr-xr-x  1 root root 258K Feb  3  2013 MONTHCAL2013_february (3).doc
-rwxr-xr-x  1 root root  77K Oct 10  2009 .pdf
drwxr-xr-x 18 root root  32K Jan  3  2009 Recipes
drwxr-xr-x  4 root root  32K Apr  2  2013 $RECYCLE.BIN
drwxr-xr-x  2 root root  32K Sep  5  2008 Recycled
drwxr-xr-x 14 root root  32K Apr  9  2011 RHHD
drwxr-xr-x  8 root root  32K Oct 28  2010 Shared .exe Programs
drwxr-xr-x  5 root root  32K Sep  5  2008 System Volume Information
-rwxr-xr-x  1 root root 7.0K Jun  4  2011 Thumbs.db
drwxr-xr-x  2 root root  32K Apr 23 16:10 Video Camera Dump
drwxr-xr-x  5 root root  32K Sep  8  2012 WI Wedding Site
```

---

### Post by nerdtron on 2014-09-29
I'm pretty puzzled by this. Can you included the commands and their output on your post? And did you use chris:chris? 

```
sudo chown -vR chris:chris /media/usb0
cd /media/usb0
ls -lah /media/usb0 
```

If you can't change the ownership, then we can try changing the permissions on the folder /media/usb0 to allow the user chris to read/write on this directory. (I assume this is an NTFS drive?)

```
sudo chmod -R 777 /media/usb0
```

---

### Post by Carl_Gitchel on 2014-11-10
Thanks again for all your help.  I have decided a substantial source of my problems is the tower I'm using.  Not only does it hang spontaneously, it does so when I re-install the Vista package it used to run.

So for the moment I'm giving up my server project.  I'll be building my own and come back here when I'm ready to move forward with that project.

---

### Post by jimmyh1972 on 2014-11-12
servers dont automount external devices like GUI systems
you should read about _**fstab**_ and edit your /etc/fstab file to mount your external HD
then you will have to write a command or create a script / cron job to do it

---

