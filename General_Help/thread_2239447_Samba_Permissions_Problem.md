---
title: "Samba Permissions Problem"
date: 2014-08-13
forum: General Help
---

### Post by 4traveler on 2014-08-13
I am running Ubuntu 12.  I've been running Samba for a few years on my Linux server and a few months (maybe over a year) on Ubuntu 12 after upgrading.  Everything has been working fine until a few days ago.  I no longer can create/update/delete any files on my Samba share.  The share is located at /home/Samba/Share.  The permissions on the directory has not changed and is still set to:
drwxrwxrwt  3 nalo  adminuser 4096 Aug 29  2010 Samba (for /home/Samba)
drwxrwxrwt 7 nalo  adminuser 4096 Aug  3 15:09 Share (for (home/Samba/Share)

   I documented the process when I setup Samba initially.  Nothing seems to have changed.  All my settings seem to be correct in my smb.conf file (here's a part of that configuration):
[Share]
   comment = Share For Pictures, Musics, and Misc With Links To Movies & Motion Pictures
   path = /home/Samba/Share
   guest ok = no
   read only = no
   writeable = Yes
   browseable = yes
   public = yes
   create mask = 0644
   directory mask = 0755


  I've also made sure the ID I am using from my Windows 8 machine is enabled in Samba.  Also, I've un-mapped and re-mapped the drive OK, but I can still only read files on my Samba.  I also made sure that the Share directory property is showing it as being shared as "Share.".  But, I still can NOT create/update/delete any of files on my share.  Any ideas?  I really need some help.

---

### Post by bab1 on 2014-08-14
> **4traveler said:**
> I am running Ubuntu 12.  I've been running Samba for a few years on my Linux server and a few months (maybe over a year) on Ubuntu 12 after upgrading.  Everything has been working fine until a few days ago.  I no longer can create/update/delete any files on my Samba share.  

The share is located at /home/Samba/Share.  The permissions on the directory has not changed and is still set to:
drwxrwxrwt  3 nalo  adminuser 4096 Aug 29  2010 Samba (for /home/Samba)
drwxrwxrwt 7 nalo  adminuser 4096 Aug  3 15:09 Share (for (home/Samba/Share)

I see you have the sticky bit set on these directories.  I'm not sure why you did that.  If you are using a share for multiple users you should set the sgid bit instead.  This sets the inheritance for the group. 

I'm not sure why you need 2 shares with one nested inside the other.
> 

   I documented the process when I setup Samba initially.  Nothing seems to have changed.  All my settings seem to be correct in my smb.conf file (here's a part of that configuration):
[Share]
   comment = Share For Pictures, Musics, and Misc With Links To Movies & Motion Pictures
   path = /home/Samba/Share
   guest ok = no
   read only = no
   writeable = Yes
   browseable = yes
   public = yes
   create mask = 0644
   directory mask = 0755

Guest ok and public are the same but you have one set to no and the other set to yes.  If you delete both  the default = no.  Which do you want?
Also read only and writable are inverse synonyms.  You only need one of them.
> 

I've also made sure the ID I am using from my Windows 8 machine is enabled in Samba.  Also, I've un-mapped and re-mapped the drive OK, but I can still only read files on my Samba.  I also made sure that the Share directory property is showing it as being shared as "Share.".  But, I still can NOT create/update/delete any of files on my share.  Any ideas?  I really need some help.
my best guess is that the permissions of files in the share directories are not not correct.  With the current settings the files and subdirectories will most likely be that of the objects creator (e.g name:name).

Post the output from the server of these commands```

ls -l /home/Samba

ls -l /home/Samba/Share

```

---

### Post by 4traveler on 2014-08-14
Thank you for your reply.  Yes you are correct the public entry is contradictory.  I just added that last night as part of troubleshooting I was doing.  Originally the entries were as you see above without the "public = yes" entry.  The directory permissions you had requested were in the original post, but here they are again:

drwxrwxrwt  3 nalo  adminuser 4096 Aug 29  2010 Samba (for /home/Samba)
drwxrwxrwt 7 nalo  adminuser 4096 Aug  3 15:09 Share (for (home/Samba/Share)

  I would appreciate any help as I am completely stuck on this one.  Something that has been working for over 4 years suddenly stopped working a couple of days ago and nothing has changed on the system since I do NOT allow automatic update of packages.  I control all the updates there has been none in the past couple of weeks.

---

### Post by bab1 on 2014-08-14
> **4traveler said:**
> The directory permissions you had requested were in the original post, but here they are again:

drwxrwxrwt  3 nalo  adminuser 4096 Aug 29  2010 Samba (for /home/Samba)
drwxrwxrwt 7 nalo  adminuser 4096 Aug  3 15:09 Share (for (home/Samba/Share.
I'm looking for the permissions on the ***contents*** of those directories.

Don't ignore my remarks about the appropriateness of the sticky bit.

---

### Post by 4traveler on 2014-08-14
Thank you for your response.  Please correct me if I&#8217;m wrong, but my understanding is that you set the SGID or GUID for executables so that when a user runs a program the system executes it as the group ID or User ID of the owner thereby giving that running program access to resources that the user initiating the execution might otherwise not have.
But Sticky bit is set mainly on folders to prevent users from deleting the folder or other users&#8217; files even though they have write permissions to the folder.  This is exactly what I want or at least that&#8217;s what I think I want based on the research I had done on Linux permissions.  My share is used by multiple users in various groups, they can all see/use each other&#8217;s files but any user who uploads a file is the only one that can delete it, except for me since I have root access.
Another point to clarify is that I don&#8217;t have a share within a share.  There is only one share location and that is /home/Samba/Share.  I only listed the permissions of the /home/Samba to show the permissions on the directory chain.  Sorry if that caused some confusion. Here are the permissions on the Share directory and one of it's sub directory:

/home/nalo$ l /home/Samba/Share
total 20
drwxrwxrwt  2 nalo adminuser 4096 Dec  2  2010 family
drwxrwxrwt  5 nalo adminuser 4096 Aug 11 18:34 Misc
lrwxrwxrwx  1 nalo adminuser   31 Jul 21  2013 Movies -> /media/Seagate_2TB/Share/Movies
drwxr-xr-t 32 nalo adminuser 4096 Aug 23  2013 Musics
drwxrwxr-x  8 nalo adminuser 4096 Feb  8  2014 Pictures
drwxr-xr-x  4 nalo adminuser 4096 Jul 12 08:21 Program Files
/home/nalo$ l /home/Samba/Share/Misc
total 58516
-rw-r--r-- 1 nalo adminuser 3339419 Feb 17 17:21 2014_Italy_Trip.docx
-rwxr-xr-x 1 nalo adminuser  934336 Aug 17  2012 bash
-rw-r--r-- 1 terry terry  593279 Nov 17  2013 Ben.jpg
-rw-r--r-- 1 nalo adminuser 1915392 Sep 15  2010 ____Complain_Less.pps
-rw-r--r-- 1 david david 1612010 Aug  8  2012 David_In_Harry_Potter.jpg
-rw-r--r-- 1 david david 1448248 Aug  8  2012 David_&_John_In_Harry_Potter.jpg
drwxr-xr-x 3 david david    4096 Dec  1  2013 David_PC
-rw-r--r-- 1 nalo adminuser   11776 Aug 31  2012 DefensiveDrivingTest1.pdf
-rw-r--r-- 1 nalo adminuser  103555 Aug 31  2012 DefensiveDrivingTest2.pdf
-rw-r--r-- 1 nalo adminuser   20007 Aug 31  2012 DefensiveDrivingTest3.pdf
-rw-r--r-- 1 nalo adminuser   92234 Aug 31  2012 DefensiveDrivingTest4.pdf
lrwxrwxrwx 1 nalo adminuser      13 Oct  3  2012 Download -> /var/www/Data
drwxr-xr-x 2 nalo adminuser    4096 May  2  2013 FileManager
-rw-r--r-- 1 nalo adminuser    2931 Nov  7  2011 FormatLinuxFiles.sh
-rw-r----- 1 nalo adminuser  106149 Aug 17  2012 Linux_Notes
drwxr-xr-x 2 nalo adminuser    4096 Dec  8  2013 Other
-rw-r--r-- 1 nalo adminuser      50 Sep  9  2013 Printer.txt
-rw-r--r-- 1 nalo adminuser 1720320 Jun 18  2012 Recipes.accde
-rw-r--r-- 1 nalo adminuser  171191 Feb  6  2013 Restaurant.pdf
-rw-r--r-- 1 nalo adminuser   31138 Apr 22  2011 Server.pdf
-rwxr--r-- 1 nalo adminuser   63148 Dec 23  2010 TCL_Bookmarks.html
-rw-r--r-- 1 nalo adminuser 1305906 Nov  3  2010 top-10-castles-around-the-world.pdf
lrwxrwxrwx 1 nalo adminuser      25 Jan  8  2013 Upload -> /media/Seagate_2TB/Upload
-rw-r--r-- 1 david   david      384794 May 28  2011 __What_To_Recycle_&_What_Not_To_Recycle.pdf
/home/nalo$

---

### Post by bab1 on 2014-08-14
> **4traveler said:**
> Thank you for your response.  Please correct me if I’m wrong, but my understanding is that you set the SGID or GUID for executables so that when a user runs a program the system executes it as the group ID or User ID of the owner thereby giving that running program access to resources that the user initiating the execution might otherwise not have.

The suid and sgid bits *allow any manipulation of the file or directory *to be done in the name of the owner (suid) or user-group (sgid).  This means if you set the sgid bit on a directory and set the user-group to smbusers, every object (file or directory) will have the user group of smbusers.  This allows user common user access via the user-group permissions.  If you want a "share" that is just a common landing spot (such as /tmp) then you really don't have sharing at all.  Just common storage.

The question you posed: " I no longer can create/update/delete any files on my Samba share." might be that either you are not the owner of the file or directory or not part of the user-group of of the file or directory/ 
> 
But Sticky bit is set mainly on folders to prevent users from deleting the folder or other users’ files even though they have write permissions to the folder.  This is exactly what I want or at least that’s what I think I want based on the research I had done on Linux permissions.  My share is used by multiple users in various groups, they can all see/use each other’s files but any user who uploads a file is the only one that can delete it, except for me since I have root access.

The sticky bit only deals with deletion of objects that reside in that directory.  Read and write are allowed.  The sticky bit does not inhibit read or write operation.  It's useful to note that the RW permissions are granted by the directory in which the object reside, not intrinsic to the object itself.
> 
Another point to clarify is that I don’t have a share within a share.  There is only one share location and that is /home/Samba/Share.  I only listed the permissions of the /home/Samba to show the permissions on the directory chain.  Sorry if that caused some confusion.

The only thing that needed along the path is read and eXecute permissions of the directory.  This allows the user to descend into that directory (traverse).  This means that all users would have access to the directory it the "others" group has r-x (5).  The latest Ubuntu has a umask of 0775 for directories and 0664 for file. 
> 
Here are the permissions on the Share directory and one of it's sub directory:

UGH!!!!  If you want to add preformatted text please wrap in in ```
 blocks.  This can be easily done by clicking on the [SIZE=4]#[/SIZE] icon at the top center of the advanced editor.  It should look like below. 

> 
[CODE]/home/nalo$ l /home/Samba/Share
total 20
drwxrwxrwt  2 nalo adminuser 4096 Dec  2  2010 family
drwxrwxrwt  5 nalo adminuser 4096 Aug 11 18:34 Misc
lrwxrwxrwx  1 nalo adminuser   31 Jul 21  2013 Movies -> /media/Seagate_2TB/Share/Movies
drwxr-xr-t 32 nalo adminuser 4096 Aug 23  2013 Musics
drwxrwxr-x  8 nalo adminuser 4096 Feb  8  2014 Pictures
drwxr-xr-x  4 nalo adminuser 4096 Jul 12 08:21 Program Files
/home/nalo$ l /home/Samba/Share/Misc
total 58516
-[COLOR="#FF0000"]rw-r--r-- 1 nalo adminuser 3339419 Feb 17 17:21 2014_Italy_Trip.docx
-rwxr-xr-x 1 nalo adminuser  934336 Aug 17  2012 bash
-rw-r--r-- 1 terry terry  593279 Nov 17  2013 Ben.jpg
-rw-r--r-- 1 nalo adminuser 1915392 Sep 15  2010 ____Complain_Less.pps
-rw-r--r-- 1 david david 1612010 Aug  8  2012 David_In_Harry_Potter.jpg
-rw-r--r-- 1 david david 1448248 Aug  8  2012 David_&_John_In_Harry_Potter.jpg
drwxr-xr-x 3 david david    4096 Dec  1  2013 David_PC
-rw-r--r-- 1 nalo adminuser   11776 Aug 31  2012 DefensiveDrivingTest1.pdf
-rw-r--r-- 1 nalo adminuser  103555 Aug 31  2012 DefensiveDrivingTest2.pdf
-rw-r--r-- 1 nalo adminuser   20007 Aug 31  2012 DefensiveDrivingTest3.pdf
-rw-r--r-- 1 nalo adminuser   92234 Aug 31  2012 DefensiveDrivingTest4.pdf[/COLOR]
lrwxrwxrwx 1 nalo adminuser      13 Oct  3  2012 Download -> /var/www/Data
[COLOR="#FF0000"]drwxr-xr-x 2 nalo adminuser    4096 May  2  2013 FileManager
-rw-r--r-- 1 nalo adminuser    2931 Nov  7  2011 FormatLinuxFiles.sh
-rw-r----- 1 nalo adminuser  106149 Aug 17  2012 Linux_Notes
drwxr-xr-x 2 nalo adminuser    4096 Dec  8  2013 Other
-rw-r--r-- 1 nalo adminuser      50 Sep  9  2013 Printer.txt
-rw-r--r-- 1 nalo adminuser 1720320 Jun 18  2012 Recipes.accde
-rw-r--r-- 1 nalo adminuser  171191 Feb  6  2013 Restaurant.pdf
-rw-r--r-- 1 nalo adminuser   31138 Apr 22  2011 Server.pdf
-rwxr--r-- 1 nalo adminuser   63148 Dec 23  2010 TCL_Bookmarks.html
-rw-r--r-- 1 nalo adminuser 1305906 Nov  3  2010 top-10-castles-around-the-world.pdf[/COLOR]
lrwxrwxrwx 1 nalo adminuser      25 Jan  8  2013 Upload -> /media/Seagate_2TB/Upload
-rw-r--r-- 1 david   david      384794 May 28  2011 __What_To_Recycle_&_What_Not_To_Recycle.pdf
/home/nalo$
```

None of the objects listed in red above are writable or deletable by *adminuser*.  Is this your problem?

---

### Post by 4traveler on 2014-08-14
Thank you for your patience.  I will try the SGID later on tonight to see if that helps.  The problem right now is that I'm trying to copy a new file that does NOT exist on the server to the /home/Samba/Share/Misc director, which I own (nalo:adminuser) and I get permission denied.  I've also tried creating and/or copying a file to /home/Samba/Share and I get the same permission denied error.

---

### Post by bab1 on 2014-08-14
> **4traveler said:**
> Thank you for your patience.  I will try the SGID later on tonight to see if that helps.  The problem right now is that I'm trying to copy a new file that does NOT exist on the server to the /home/Samba/Share/Misc director, which I own (nalo:adminuser) and I get permission denied.  I've also tried creating and/or copying a file to /home/Samba/Share and I get the same permission denied error.

Are you a member of the group *adminuser*?  What does this command produce```
getent group adminuser
```
Is your username *nalo* or *david*?

At this point adding sgid bit to any of the above directories might not help you get to where you want to go.

I know you have suggested that you are looking for a "common workspace" that files can only be deleted by their owners.  Is this true?  If you set common groups (sgid) then multiple users will be able to delete data.  Is that okay?

I know it seems like I'm being tough on you.  I'm trying to get you to think about the design BEFORE you implement anything,  I have the the same file system and share setup for the at last the last 6 years (Ubuntu 8.04 LTS).  I run Ubuntu 14.04 with Samba 4.1 currently on a test computer.

---

### Post by 4traveler on 2014-08-14
I changed the permissions on the share directory to use SGID as in:
/home/nalo$ l /home/Samba
total 4
drwxrwsrwx 7 nalo adminuser 4096 Aug 14 19:43 Share

  Then I tried to copy a new file to the root of the share drive at /home/Samba/Share and I get permission denied.  Sucks.  What I don't get is that I literally did not make any changes whatsoever to Samba (or anything else for that matter) for weeks.  That server just runs on its own and I only log on if there are any issues.  And as I said I do NOT allow any automated package updates until I review them, so no changes of any kind.  I also use that share drive to automatically backup my MS money file every time I exit MS money.  I see that the newest copy of MS money was copied there to a sub directory on 8/11/2014 at 5:43 AM (I'm an early bird). On the afternoon of Aug 11 I could not copy anything to my Share drive.  I ended up copying it to a cloud storage at 6:31 PM that day.

---

### Post by bab1 on 2014-08-14
> **4traveler said:**
> I changed the permissions on the share directory to use SGID as in:
/home/nalo$ l /home/Samba
total 4
drwxrwsrwx 7 nalo adminuser 4096 Aug 14 19:43 Share

  Then I tried to copy a new file to the root of the share drive at /home/Samba/Share and I get permission denied.  Sucks.  What I don't get is that I literally did not make any changes whatsoever to Samba (or anything else for that matter) for weeks.  That server just runs on its own and I only log on if there are any issues.  And as I said I do NOT allow any automated package updates until I review them, so no changes of any kind.  I also use that share drive to automatically backup my MS money file every time I exit MS money.  I see that the newest copy of MS money was copied there to a sub directory on 8/11/2014 at 5:43 AM (I'm an early bird). On the afternoon of Aug 11 I could not copy anything to my Share drive.  I ended up copying it to a cloud storage at 6:31 PM that day.

I know you are frustrated.  If we are to diagnose this rather than throw pasta at the wall, we should diagnose what we have now.

Read the previous post (#8) and answer all the questions.

---

### Post by 4traveler on 2014-08-14
I have thought about the design and I am do want a common place for users to copy/backup their files hence the sticky bit, but at this point I would take anything as long as I can use my share.  Right now the share is read-only and useless.  BTW it is mounted as read/write.  Also, my user ID is nalo in adminuser group.  I am the only one in the adminuser group:
/home/nalo$ getent group adminuser
adminuser:x:1000:
I am trying to troubleshoot this.  I believe that things don't break all of a sudden for no reason.  Something has caused this.  Typically things break when there is a change, especially when something has been working for years.  If I can find what what changed/what happened I should be able to fix it.  I have also checked access to the share from different machine just make sure the firewalls on the PC are not causing problem and they all behave the same.  I would gladly take any suggestions and am willing to try different things.

BTW, due to my work schedule I probably will not be able to get back to this thread until Saturday mid-day.  Thank you for all your help and suggestions.

---

### Post by bab1 on 2014-08-14
> **4traveler said:**
> I have thought about the design and I am do want a common place for users to copy/backup their files hence the sticky bit, but at this point I would take anything as long as I can use my share.  Right now the share is read-only and useless.  BTW it is mounted as read/write.  

The problem is not the Linux file system and it appears Samba is working as it is configured.  See below.
> 
Also, my user ID is nalo in adminuser group.  I am the only one in the adminuser group:
/home/nalo$ getent group adminuser
adminuser:x:1000:

You are NOT part of the group named adminuser.  If you were it would appear like this```
getent group adminuser
[COLOR="#0000FF"]adminuser:x:1000:[/COLOR][COLOR="#FF0000"]nalo[/COLOR]
```
Everything in blue above is the user-group.  Everything in red are the users in the user group.

Most of the time I use the user-group named *users*.  It looks like this```
getent group users
users:x:100:bab

```
> 
I am trying to troubleshoot this.  I believe that things don't break all of a sudden for no reason.  Something has caused this.  Typically things break when there is a change, especially when something has been working for years.  
I hate to disagree.  The above is clearly a misconfiguration and it explains why you can't rely on the adminuser group to give you read/write access.> 
If I can find what what changed/what happened I should be able to fix it.  I have also checked access to the share from different machine just make sure the firewalls on the PC are not causing problem and they all behave the same.  I would gladly take any suggestions and am willing to try different things.
Take my advice and add yourself to the user group adminuser.  I notice that you have used the UID of 1000.  That is usually reserved for the first user.  What have we done here?

What do you get from this command ```
getent passwd nalo
``` 
If you are changing the group name from nalo to adminuser you well can be causing your own problems.  The Debian distros are designed to use User Private Directories.  This means that the default user group is supposed to be a placeholder only (i.e nalo:nalo) If you are going to use a common group then you need to add youself to a specific ADDITIONAL group and deal with that in a Debian manner.

If you have root powers then why do you need this adminuser group.  If you use the adminuser group then you will need to deal with the management of a common user group.  Maybe we should start with a test share away from al the other shares at* /srv/samba/nalo*.  > 

BTW, due to my work schedule I probably will not be able to get back to this thread until Saturday mid-day.  Thank you for all your help and suggestions.Fine by me.  I'm not on the road until Tuesday.

Answer ALL the questions so I can present you with a list of steps you need to take to resolve the issue.  It's pretty clear now what happened, now we need to clean up the misconfiguration and create solid shares that will always work.  I have the same file system and shares I originally configured for Ubuntu 8.04.  I'm now using 14.04.  Never a problem.

---

### Post by 4traveler on 2014-08-15
No I am part of that group.  That's my primary group:
/home/nalo$ id nalo
uid=1000(nalo) gid=1000(adminuser) groups=1000(adminuser),0(root),4(adm),20(dialout),24(cdrom),33(www-data),46(plugdev),100(users),105(lpadmin),119(admin),122(sambashare)
/home/nalo$ getent passwd nalo
nalo:x:1000:1000:nalo,,,:/home/nalo:/bin/bash

Now I have to head to work.

---

### Post by 4traveler on 2014-08-16
Well here's an oddity for you.  I went ahead and uninstalled and re-installed Samba while my share had the SGID set.  After the installation I was able to create a new directory in /home/Samba/Share and I was then able to delete it.  Just to make sure it is working then I rebooted the system.  After the reboot I can NOT create a directory anymore.  The share permissions have NOT changed.  Now that's areal pickle.

---

### Post by bab1 on 2014-08-16
> **4traveler said:**
> Well here's an oddity for you.  I went ahead and uninstalled and re-installed Samba while my share had the SGID set.  After the installation I was able to create a new directory in /home/Samba/Share and I was then able to delete it.  Just to make sure it is working then I rebooted the system.  After the reboot I can NOT create a directory anymore.  The share permissions have NOT changed.  Now that's areal pickle.
I don't see how re-installing Samba has relevance to a problem with Linux permissions which is your basic problem.  The sgid bit is set on a Linux directory not a Samba share.

Are you acting DIRECTLY on the /home/Samba/Share directory (e.g. from the local host)?  Or are you trying to create a directory via a CIFS share using a Windows or Samba client?

I don't think you should be storing data other that the users OWN data in the /home directory anyway.  The convention is to store data for servers at /srv.

If I was an AppArmor developer and Ubuntu decided to manage all /home directories using AppArmor to do that, you might have difficulties.  Exactly as you have.  The /srv directory would not be affected.  Is this what's happening?  I don't know.  But then again I have never stored any data that is managed by Samba other than usershares (via GUI) in the /home file system tree.

Once again I suggest you create the directory /srv/Samba/share.  Change the ownership (chown)  to nalo:<whatever your primary group is> and set the permissions to 0775.

Then set the sharing and restart the Samba daemon ```
sudo service smbd restart
```
Now do your testing.

---

### Post by 4traveler on 2014-08-16
My apologies for not being clear.  You are correct in that the whole problem was related to me accessing the share from Windows.  Accessing it directly from Linux was never an issue since I owned the path.  I took your advice and move everything from /home/Samba to /srv/Samba, redefined the share in Samba and restarted it and at least for a while it was working fine.
However, now I have major problems.  I have seen many times when something changes that it works fine until the system is booted and then it starts having problems so I decided to reboot the system just to make sure thing still work after it comes up.  Well now the system won't boot up.  I blame this at least partially on all the power hits that we get around here with the idiots at Reliant Energy.  Now I have to troubleshoot this problem.  I'm thinking I may just replace the hardware, but that would take a while.  It's at least 10 years old.
Anyway thank you very much for all your help.

---

### Post by bab1 on 2014-08-16
> **4traveler said:**
> My apologies for not being clear.  You are correct in that the whole problem was related to me accessing the share from Windows.  Accessing it directly from Linux was never an issue since I owned the path.  I took your advice and move everything from /home/Samba to /srv/Samba, redefined the share in Samba and restarted it and at least for a while it was working fine.

The point I would make is:  Always use a directory outside of /home for shared data.  The /home directory is monitored internally for security breaches and can cause "common data" problems.  This has become increasingly so in the latest versions of Ubuntu in my opinion.

I also noticed that you use sym-links in your shares.  This also is disallowed at kernel level in some instances.  Samba by default also is hardened against following sym-links.  I just never use hard or soft (sym) links at all with Samba.

This is not to say I don't use hard links or soft links at all.  I do use both extensively, just not with Samba. 
> 
However, now I have major problems.  I have seen many times when something changes that it works fine until the system is booted and then it starts having problems so I decided to reboot the system just to make sure thing still work after it comes up.  Well now the system won't boot up.  I blame this at least partially on all the power hits that we get around here with the idiots at Reliant Energy.  Now I have to troubleshoot this problem.  I'm thinking I may just replace the hardware, but that would take a while.  It's at least 10 years old.
Anyway thank you very much for all your help.
Sorry to hear about your apparent hardware problems.  

You shouldn't have reboot problems with Samba.  Restarting the daemon is the same as a reboot to Samba.  Upon startup Samba parses the /etc/samba/smb.conf file by default to get the various settings that are other than the default settings.

---

