---
title: "Rights help"
date: 2023-03-13
forum: General Help
---

### Post by tedfroop21 on 2023-03-13
I know this is rudimentary stuff but I have PTSD and its affects my logical abilities.  I used to be able to do CLI no problem but now I don't trust myself as to be brief - mistakes have been made......

I moved my media server to a new machine.  All has been well except there is no backup and recover for the media server database.  A simple piece of this is the people database. I had made a copy and there were a lot of people associated to personal media files that contain data per person.  All was good except rights, as I had to use sudo to copy files from the database to backup to the database.  Of course this give them root owner and group.

To move them back I need to recursively give rights for: 

user emby-Emby Server, group Emby 

To all the files and directories in  //var/lib/emby/metadata/people, 

Which contains alphabetic a-z subdirectories and subdirectories for each person that contain their data files. some of which now have User: root and group Root user rights.

If you could give me code to copy and paste I would be very thankful.

---

### Post by TheFu on 2023-03-13
If you use **rsync** with **sudo** and use the -avz options, then the owner, group, and permissions will be retained.  No copy/paste method, sorry.  You should copy the media over again, using **sudo rsync -avz ......**

What are "rights"?  There are different permissions, but you haven't said which ones you want to provide to whom.  I'm also confused by what a "person" is, since inside the media databased, that would typically be actors, directors, and other film-related people. This is all stored in the DB, not separate files.

 //var/lib/emby/metadata/people looks like a CIFS share. Is that allowed in Emby?  I don't think it is for plex or jellyfin or kodi, not for the DBMS files.  I'd bet that like Jellyfin, /var/lib/emby/ just needs to be owned by the emby daemon user. Here's my jellyfin setup:
```
$ ll /var/lib/jellyfin/
total 260
drwxr-x---  9 jellyfin adm        4096 Mar 13  2021 ./
drwxr-xr-x 81 root     root       4096 Feb 28 17:48 ../
drwxr-xr-x  3 jellyfin jellyfin   4096 Feb  1  2021 .aspnet/
drwxr-xr-x  9 jellyfin jellyfin   4096 Mar 13 15:28 data/
drwx------  2 jellyfin jellyfin  16384 Feb  2  2021 lost+found/
drwxr-xr-x  8 jellyfin jellyfin   4096 Nov 26  2021 metadata/
drwxr-xr-x  4 jellyfin jellyfin   4096 Dec 10 10:53 plugins/
drwxr-xr-x  3 jellyfin jellyfin   4096 Feb  1  2021 root/
drwxr-xr-x  2 jellyfin jellyfin 217088 Mar 13 15:22 transcodes/
```
If it is the same, this command:
```
sudo chown -R emby:emby /var/lib/emby
```
will likely do what you need.  I've never used emby, so YMMV.

You can ignore the lost+found/.  I mount separate storage just for jellyfin and mounts get that directory.

---

### Post by tedfroop21 on 2023-03-13
Thank you sir.  That did the trick.  I have difficulty with working memory so sometimes I think one thing and type another,  

Thanks much for translating and your help TheFu.....

---

