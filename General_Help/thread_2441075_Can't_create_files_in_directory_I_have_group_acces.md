---
title: "Can't create files in directory I have group access to."
date: 2020-04-18
forum: General Help
---

### Post by Tadaen_Sylvermane on 2020-04-18
```
yansell@bionicltsp:/snapraid/pool/video/20200308tvshows/dune (2000)$ ls -al
total 1886244
drwxrwxr-x  2 jason ourmedia      4096 Nov  3 18:02 .
drwxrwxr-x 23 jason ourmedia      4096 Jan 13 06:51 ..
-r--r--r--  1 jason ourmedia 593797524 Sep  4  2019 Dune_s1e1.mkv
-r--r--r--  1 jason ourmedia 678156427 Sep  4  2019 Dune_s1e2.mkv
-r--r--r--  1 jason ourmedia 659531594 Sep  4  2019 Dune_s1e3.mkv
-r--r--r--  1 jason ourmedia         0 Nov  3 18:02 .update
yansell@bionicltsp:/snapraid/pool/video/20200308tvshows/dune (2000)$ groups
yansell ourmedia
yansell@bionicltsp:/snapraid/pool/video/20200308tvshows/dune (2000)$ touch lol
touch: cannot touch 'lol': Permission denied
```

I was trying to set it up on another machine so my wife can rip movies / tv series discs at the same time to the share on the server but for some reason she has no write access, even with the above permissions on the directory. The only way I can get her write access is 777 but that is obviously not the right course of action. I'm unsure of what to do here or why this doesn't work.

---

### Post by TheFu on 2020-04-19
Please show the output from 'id' for both accounts.
I don't have any specific knowledge about snapraid. Does it honor Unix permissions?  Is this mount NFS or something else?  Could the mount be read-only?  Why are all the file permissions 444? That seems odd.

---

### Post by Tadaen_Sylvermane on 2020-04-19
```
uid=5000(jason) gid=5000(jason) groups=5000(jason),27(sudo),2002(ourmedia)
```

```
uid=5001(yansell) gid=5001(yansell) groups=5001(yansell),2002(ourmedia)
```

Snapraid lays on top of the file system and works via directory. All it does is create non realtime parity. I only sync when I add media to the drive. I can restore from that parity if I lose x number of disks assuming I have enough parity disks. It can handle 6 disks for parity. So I could theoretically lose 6 disks at the same time and still be able to recover. Similar to ZFS it can provide bit rot detection by scrubbing the array. I have it set to scrub every night and it emails me if it finds something out of sorts. Can then repair it from parity if needed.

The mount is NFS. Insecure is for Kodi to access, I think mergerfs requires the fsid. Can't recall exactly.

```
jason@server:~$ cat /etc/exports/snapraid/pool
192.168.1.0/24(rw,insecure,no_root_squash,no_subtree_check,fsid=2)
```

I set permissions on all media 444 to prevent anyone other than me deleting them, and in my own case accidental deletion by a careless mistake when trying a find command or something.  The folders still have proper permissions to allow people to go in them though.

I'm not sure if it matters. The yansell user is coming from my NIS server.

---

### Post by TheFu on 2020-04-19
> **Tadaen_Sylvermane said:**
> ```
uid=5000(jason) gid=5000(jason) groups=5000(jason),27(sudo),2002(ourmedia)
```

```
uid=5001(yansell) gid=5001(yansell) groups=5001(yansell),2002(ourmedia)
```

Snapraid lays on top of the file system and works via directory. All it does is create non realtime parity. I only sync when I add media to the drive. I can restore from that parity if I lose x number of disks assuming I have enough parity disks. It can handle 6 disks for parity. So I could theoretically lose 6 disks at the same time and still be able to recover. Similar to ZFS it can provide bit rot detection by scrubbing the array. I have it set to scrub every night and it emails me if it finds something out of sorts. Can then repair it from parity if needed.

The mount is NFS. Insecure is for Kodi to access, I think mergerfs requires the fsid. Can't recall exactly.

```
jason@server:~$ cat /etc/exports/snapraid/pool
192.168.1.0/24(rw,insecure,no_root_squash,no_subtree_check,fsid=2)
```

I set permissions on all media 444 to prevent anyone other than me deleting them, and in my own case accidental deletion by a careless mistake when trying a find command or something.  The folders still have proper permissions to allow people to go in them though.

I'm not sure if it matters. The yansell user is coming from my NIS server.

444 on media doesn't have anything to do with delete permissions.  **It is the parent directory permissions controls create/delete permissions.** 
I have no clue what /etc/exports/snapraid/pool has to do with NFS.  /etc/exports is the NFS exports file.  Hever seen "insecure" as an option for NFS either or fsid. Guess insecure is an option, don't know why that would be needed on any normal Unix.  My kodi/osmc systems don't have any issue connecting with NFS.  They all have a /etc/services file and nfs would be on a port under 1024.  These days, on the client side, I use the "tcp" mount option to limit data corruption from UDP. That has been recommended for any network with over 100 Mbps connections for a while.

I don't think parity works that way. Don't be overly certain about redundancy.  People get burned by misunderstanding RAID striping + parity all the time.

Have both users logged out and logged into the system since the shared group was created?

For multiple users to work together,  
[https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965)

* Put everyone into the same group (perhaps www-data or plex or xbmc is what you want?).
* Create a directory where they can share files (somewhere for apache/plex/xbmc).
* Make the group on that empty directory have rwxs permissions
```
           $ sudo gpasswd -M  user1,user2,user3  ourmedia
           $ mkdir -p /tmp/Workspace
           $ cd /tmp/
           $ chmod g=rwx**s** Workspace
           $ ls -Fl Workspace
              drwxrw**s**---   owner    group    Workspace/ 
           $ chgrp ourgroup Workspace
           $ ls -Fl Workspace
              drwxrw**s**---   owner    **ourmedia**    Workspace/

```
Media servers tend to run under different userids, say xbmc, plex, whatever, so usually, I just let those userids get their access using the "other" permissions of r or r-x for directories.  The example above doesn't show that.  I'm a huge believer in 007 umask to prevent unknown users access to files by accident.

The g+s permissions on a directory force the group on that directory to be used for all files/directories created as children. Sub-sub-directories will inherit the group and g+s permission, so whenever a new area to be shared by multiple people is setup, just make the top directory have the group and g+srwx permissions you want. All new objects created under there (not moved, but copied), will get the expected group and rw permissions.

---

### Post by Tadaen_Sylvermane on 2020-04-19
Ok I clearly misunderstood some things then. 

first

```
[COLOR=#000000][FONT=&amp]jason@server:~$ cat /etc/exports
/snapraid/pool [/FONT][/COLOR][COLOR=#000000][FONT=&amp]192.168.1.0/24(rw,insecure,no_root_squash,no_subtree_check,fsid=2)[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Typo. Sometimes when I copy / paste from a terminal it screws up my formatting. I missed it when I posted the other night. The above is my exports file. I just know that for Kodi to be able to see the nfs shares it needs the insecure flag. Won't work without it. If I change the suid bit I'll try to remove that flag and see what it does. That is 99.9% of what I do on my server. Pretty much nothing but media. A few other things, but the majority just media serving > Kodi machines around my lan.

second.

 I figured if the files were read only then it wouldn't allow the directory to be deleted. I don't understand the letter method of permissions. I do understand Octals. I recently was reading about sticky, setgid, and suid bits. 

So to sort it out like you say octally? This would be run on each of the video and music directories?

```
find /snapraid/pool/video/ -type d -exec chmod 4775 \;
```

```
find /snapraid/pool/video/ -type f -exec chmod 4644 \;
```

From then on it would create everything properly under my user / and the ourmedia group?


As far as users go. Each Kodi machine has it's own user. The only people I want to have write access is my wife and I, hence the ourmedia group.

Is this what I should aim for?[/FONT][/COLOR]

---

### Post by TheFu on 2020-04-19
suid has nothing to do with this.  It is a way to force a different userid to always be used to run a process, usually root, but it could be any other userid.  There are almost always better methods than using setuid bit.  NEVER user a setuid bit on scripts or any programs not 100% controlled by the userid/owner of the file AND directory.

g+s doesn't get used on files. It is only a directory thing. And it won't change the existing group on either. That's a separate command.

NFS doesn't care about username or groupname.  The different userid (the number) is what counts, not the username.  If the username is different, but the number maps to the groupid of the shared directories/files, then it will have those permissions.  In my posts, I' usually careful to always include "id" in the object if I mean the numbers, not the names.  user is ambiguous.  userid=number. uid=number. username=thefu. Same for group, groupid, gid and groupname.  If there's an 'id' in the term, it is about the number, not the letters. ;)

---

