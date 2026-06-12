---
title: "Unable to access disk content with Plex Media Server (appears empty)"
date: 2015-02-27
forum: General Help
---

### Post by fkervin on 2015-02-27
Hi All,
  
 I'm using plex on a Ubuntu system, my problem is that when I try to  access to a disk connected via USB (NTFS formatted) plex shows the disk  as empty so I can't add the media.
  
 I've modify the system to mount the disk in **/media/external** instead of **/media/myuser/external** and I've also take ownership of the whole disk (-R) and make "chmod -R 777".
  
 But despite this, plex still shows disk as empty. How can I make it recognize folders and files so I can add them to my library?
  
 Many thanks in advance.
  
 Regards

---

### Post by TheFu on 2015-02-27
NTFS ignores chmod -R 777.
You must mount it with permissions that the userid running plex can read.

So - what is your mount technique and command?

---

### Post by fkervin on 2015-02-28
Hi TheFu,

Many thanks for your answer. To make unit be mounted in this way I created a udev rule:

```
ENV{ID_FS_USAGE}=="filesystem", ENV{UDISKS_FILESYSTEM_SHARED}="1"
```

So all units are mounted under /media/ instead of /media/myuser/

The problem is I don't know how to set appropiate rights to the disk so plex can access the content.

Regards and thanks

---

### Post by TheFu on 2015-02-28
I've **never** touched udev rules to control mounts - I suppose that can work .... 

Most people use 
* /etc/fstab - SATA connected disks
* /etc/auto.master - autofs is handy for USB and NFS mounts
* a shell script that is run with sudo

I don't have any NTFS stuff here. All the network storage uses Linux file systems because those can be shared with Windows via samba trivially.

So you need to figure out how to 
a) set mount options for udev mounts or 
b) modify groupids for the userid that the mount action is happening under OR
c) change to a different mount method where mount userid/groupid and other permissions are easily controlled.

Your choice.

[https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux) has instructions ... but they got the permissions wrong at the end. NTFS ignores chown/chmod ... the userid/groupid and permissions shown to Linux need to be part of the mount options  ... uid= and gid= ... the actual values depend on the numbers that correlate to your plex userid/groupid. .... or you can just make them 775 for directories and 664 for any data files (user+group rw).

Again - your choice.

Linux is extremely flexible and there are reasons for doing it in any of these different ways.  I'd probably just mount with those dir/file permissions in the last paragraph. Plex won't be able to delete/modify any of the files, however.  
google also found this: [https://forums.plex.tv/index.php/topic/56668-how-to-external-ntfs-and-ubuntu-plex/](https://forums.plex.tv/index.php/topic/56668-how-to-external-ntfs-and-ubuntu-plex/) - which looks to be exactly what I'd do in your situation except on my system the plex uid is 107 and gid is 114, so the options are:
```
fmask=664,dmask=775,uid=107,gid=114 0 0
```
Make sense? Then I'd add my userid to the plex group

Lastly - I only mount temporary storage with udev. All other storage, I specifically mount **anywhere** else to avoid confusion.  The udev rules were setup that way for security reasons and the change you've made can make a system less secure.

---

### Post by fkervin on 2015-02-28
Many thanks for your answer again, Thefu,

I created that udev rule quite ago, when I firstly experienced the problems with Plex, and I had to spent a lot of time until I found that procedure. Until now it has work nice with ext3 disks but now I need to add external disks content (disks in NTFS since are shared with windows systems).

The most important here is I need a procedure that works with every disk in NTFS I connect. I mean, having to modify /etc/fstab or any other file for every disk I use is not an option. I need an user friendly method that doesn't involve configuring a file manually for every new NTFS disk I use.

What would you reccomend in this case?

Many thanks again for your interest.

Regards

---

### Post by TheFu on 2015-02-28
You can use the UUID or disk Label to setup the fstab - plex doesn't like it when storage is removed - but that is a different issue.
If you control the Labels, then having 5-5000 pre-configured mounts shouldn't be hard - I'd definitely use autofs for temporary storage - that's how I do it.

I have dual HDD docks here, but don't swap drives ... yet. For me, it is cleaner to just get 2 more 4TB hdds and worry about cleanup later. I always get 2 drives - primary and backup.

---

### Post by fkervin on 2015-02-28
Thanks again for your help,

I'm not sure if I understand you, but looks like autofs is what you recommend me, I'm going to look at this.

Think that I've to give the computer to a person who has **many** external disks in NTFS and I want all those disks to work ok without this person having to handle configuration files, adding UUIDs or something similar.

Configuring all those disks one by one is not an option since I'm not here to make this work for him and he needs something easy. Let's say.... I want the procedure as easy as would be in Windows.
Regards

---

### Post by fkervin on 2015-03-04
Hi all,

I've spent some time with it but I get nothing. I've been reading about /etc/auto.master (at this moment doesn't exist on my system) but I can't figure out how to make it mount NTFS disks in way they can be used by plex.

I don't need several methods to do it, I need only one, a modification to my system so I can use NTFS disks with plex.

Many thanks in advance and regards

---

### Post by raptir on 2015-03-04
[https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux)

When I was doing this I was only using a single disk and mounted it with the *permissions* option. That made plex able to see the disk without an issue. I don't know how you would go about making this automatically apply to all ntfs disks that are mounted, though.

---

### Post by TheFu on 2015-03-04
> **fkervin said:**
> Hi all,

I've spent some time with it but I get nothing. I've been reading about /etc/auto.master (at this moment doesn't exist on my system) but I can't figure out how to make it mount NTFS disks in way they can be used by plex.

I don't need several methods to do it, I need only one, a modification to my system so I can use NTFS disks with plex.

Many thanks in advance and regards

If you post which method you think you need and what you've done, perhaps we can help?

Since this is about permissions, showing both
a) the exact mount command
    AND
b) the **ls -al** 

for the plex data area after mounting would be helpful - at least for the ./ ../ and a few files/directories at the mount point.

Really all you need is for mounted directories to be 755 and the media files to be 644. This will remove the need to deal with specific userids or groups.

Sorry - that I don't know any method easier than autofs.  There may be some new-fangled automatic mounting tools of which I am not aware.

---

### Post by fkervin on 2015-03-04
Many thanks for your help, TheFu, and of course don't say you're sorry for anything, I only can thank you for your interest and help.

I really don't know which method I prefer, the only thing I know is I want all NTFS disks I connect to USB to be used in Plex without having to modify system files or doing things that can damage the system.

 Think I need a procedure that can be used not only by me, but also by an **user**, and when I say "**user**" I mean someone who have the computer as an entertaining machine and it's not interested in becoming system administrator, programmer or ubuntu geek (In my case "ubuntu geek" is perhaps too much, but I try to learn all my time allows me :) ).

Said this, I've follow this thread:

[https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux)

After all, everything in this link can be summarized in adding a line to /etc/fstab:

```
UUID=XXXXXXXXXXXXXXXX /media/EXTERNAL ntfs-3g permissions,auto 0 0
```

Doing this I can use the disk with plex, but it has 2 big problems:

1.- Requires the edit of /etc/fstab for every NTFS disk used
2.- Much worse: When I power on the computer and the disk is not connected I have an error on boot saying that this disk is not present and I have to press "S" key to ignore.

In your last post you talk about 755 for directories and 644 for the media. Perhaps it could be interesting. At the moment I'm using Thunar custom actions to have options to to easily and automatically perform actions such as take ownership or assign 755 or 777 rights of a folder and all its content. Perhaps I could make another one to assignt those rights (It it has to be done only once per disk is a good solution). What I don't know is how could I do it via terminal to any disk, If I know this I could create this automated thunar custom action.

Regards and many thanks again.

---

### Post by TheFu on 2015-03-04
chmod does NOT work on NTFS mounted partitions. The file system doesn't support POSIX owner and permissions.

The only way I know to control those permissions are at mount time, with mount options.

You realize that Plex doesn't like when media is removed. Have you tested that it works in a way you can live with?

---

### Post by fkervin on 2015-03-04
Hi again, TheFu, and thanks for your help,

I've realize chmod does nothing here, but I asked since you said in your last post:

> Really all you need is for mounted directories to be 755 and the media  files to be 644. This will remove the need to deal with specific userids  or groups.

Regardless of possible problem with media removed, what I need is well defined: I want the same effect that I have when I add the line I told to **/etc/fstab**:

[B]```
UUID=XXXXXXXXXXXXXXXX /media/EXTERNAL ntfs-3g permissions,auto 0 0
```

[/B] But I want it for every disk in NTFS I connect, having not to edit the file and more important, having no error on boot if a disk that I configured is not present in this moment. More clear: I want all NTFS disks connected to USB to be readable by Plex by default. I think the way to do it is modifying the way that OS automount devices to make it match whith the way it's mounted when a add the line to** /etc/fstab**.

How could I archieve this?

Regards and many thanks

---

### Post by raptir on 2015-03-16
> **fkervin said:**
> 2.- Much worse: When I power on the computer and the disk is not connected I have an error on boot saying that this disk is not present and I have to press "S" key to ignore.

I know this doesn't address the entire issue, but if you add the "noauto" option to the disk in fstab you will avoid this. It will still be mounted if it is present but the system will not wait for it if it is not.

---

