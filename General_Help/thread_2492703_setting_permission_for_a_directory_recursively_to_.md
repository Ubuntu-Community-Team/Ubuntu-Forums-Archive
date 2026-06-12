---
title: "setting permission for a directory recursively to drwxrwxrwx  ?"
date: 2023-11-20
forum: General Help
---

### Post by isprins on 2023-11-20
Hi, how do I set the permissions recursively for /Mypool/filmerogserier to  drwxrwxrwx* ? 

It's folders that contains media for a jellyfin server. The server cannot access the movies and series at the moment, it's likely a permissions issue.
The files in those folders have these permissions.
-rw-rwxr-- 1 haaken 568* 

The correct is: 
-rw-rw-r-- 1 haaken haaken 

My groups looks like this:
groups haaken
haaken : haaken adm cdrom sudo dip plugdev lxd docker
$ groups jellyfin
jellyfin : jellyfin video render haaken

---

### Post by MAFoElffen on 2023-11-20
> **isprins said:**
> Hi, how do I set the permissions recursively for /Mypool/filmerogserier to  drwxrwxrwx* ? 

It's folders that contains media for a jellyfin server. The server cannot access the movies and series at the moment, it's likely a permissions issue.
The files in those folders have these permissions.
```

-rw-rwxr-- 1 haaken 568* 

```
The correct is:
```

-rw-rw-r-- 1 haaken haaken 

```
My groups looks like this:
```

groups haaken
haaken : haaken adm cdrom sudo dip plugdev lxd docker
$ groups jellyfin
jellyfin : jellyfin video render haaken

```

First, how did you install and how are you running jellyfin? As a snap? Container? Or installed on the system via a .deb package? Because each have differences in how they can access files... 

Next, why are you not a member of the video group?

The permissions you listed are actually more open that what the people say works:
> 
 The listing below applies to the user/group that your JF installation is running with. Which user that is, is up to you.

[LIST]
[*]Transcode folder: read, write, execute 
[*]Config folder: read, write, execute 
[*]Cache folder: read, write, execute 
[*]Media folders and any parent directory: read and execute (and write on the directory used for the Library and deeper if you want to be able to remove files from the JF UI) 
[*]Media files: read 
[*]/var/lib/jellyfin and all underlying folders should belong to jellyfin 
[/LIST]

Ownership of your media folders doesn't matter, as long as the jellyfin user has read access to them (and preferably only read access, to avoid accidental media deletion through the web UI)

The doc's say the same for Jellyfin as those of Plex, where it is not just permissions, but how the folders are orgrnised affects if files can be accessed or not, and how they are accessed.
> 
Your media does not follow the organizational requirements for Jellyfin's scanner to properly identify media. (Valid organization schemes can be found in the documentation for Movies, Shows, Music, and others.) If it's not one of these, please consider asking for help as it might be a bug.

But to just answer your question, what I would do first, it take screenshots of what the permission are set to now, so you have a record of what to reset them to if needed.

Then translate what the required above is into these commands...
```

# to change ownership of a file or directory
sudo chown <UserName>:<GroupName> /PathTo/FileOrDirectory
# to change ownership of directory and everything under it recursively
sudo chown -R <UserName>:<GroupName> /PathTo/Directory
# to change permissions of a file
sudo chmod 664 /pathTo/FileOrDirectory
# to change permission of directory and everything under it recursively
sudo -R chmod 664 /pathTo/Directory

```
Your question asked how to set the permissions to 777. You can do that with the above command, but I would really recommend against that. That is way to open. I mean you coudl try that as a test, to see if it is some permssion challenge, but even if it were, I would then figure out how to lock it down so that just what needs to access it, with what it needs to do, is all that is there.

---

