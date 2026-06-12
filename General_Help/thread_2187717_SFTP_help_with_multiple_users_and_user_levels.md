---
title: "SFTP help with multiple users and user levels"
date: 2013-11-13
forum: General Help
---

### Post by Erikjd21 on 2013-11-13
Here is the general idea of what we are needing:

SFTP server for clients, each client cannot see the other clients folders, they must be locked into only their own folder. (I have this working)

Super user that can see all of the client folders that is controlled by our company (this half works). The super user must be able to upload and download files to the client folders for the clients to receive (this does not work).

I have configured SFTP using openssh, with the many tutorials found on Google. I have put clients into an ftpuser group, locked that group into a home directory of /home/company/client. I have made another group called masterftp, this is for our company, it is locked into a home directory of /home/company to allow for access to each of the client folders. 

This is where the problems begin. The company account can download, but cannot upload. If I change permissions to 770 within the client folder, everything works, unless the clients or company user create a new folder, which then requires the same permissions change to take place. This server will see a lot of traffic, so manually changing the permissions per folder (including each subfolder) would be a full time job. Each user is created with no shell, so they only have sftp access. 

Is there a program I am not finding out there that will allow me to do this, without having to dive into scripts put into cron jobs for this to take place?

Any help is appreciated!

What I am using: ubuntu server 12.04 LTS, OpenSSH-server.

---

### Post by TheFu on 2013-11-13
Please post a few sample directories with own/group and permissions. An **ls -rR** would be good.  Sorry, but I'm having touble following your description.

Also the output from '**id**' for each user would be extremely helpful.

There are exotic methods to get done what you need, but using commonly used methods would be better, if possible. Just need more concrete information.

---

### Post by Lars Noodén on 2013-11-13
One trick shown in another thread was to use [bindfs](http://ubuntuforums.org/showthread.php?t=2187472&highlight=bindfs+howto) to mount the directory elsewhere and then force permissions to stick.  

```

sudo  bindfs -o perms=0660:+X,force-group=ftpuser /path1/source/  /path2/mountpoint/

```

There /path1/source will have normal permissions, while the same directory accessible under /path2/mountpoint will have the permissions 770.

So if you have the users chrooted to the FUSE-mounted directories then the permissions will be forced even on new directories created by the user.  It's a bit of a hack but works.

---

