---
title: "Best practices for user, group and access right management"
date: 2019-01-04
forum: General Help
---

### Post by saleb on 2019-01-04
I have spent some time in the last few days learning about the commands for file permissions, file ownership change, the creation of new users and groups. That s all very intuitive the commands are almost self-explanatory, even the bitmasks. 

I am interested in best practices for use of these options when you are having users for your apps. For example, if an application is run under some user the data it creates is owned by its user who is the head member of its own group; and every other user that wants access to that data is associated (a member of) that group. What happens if the user running the app is not a physical user, but some system user? On home media server there are various examples like a download manager, which can be controlled by any physical user or the app which orders something to be downloaded when its downloaded the other app takes the downloads and moves them to the other location, the third app is used to access the data (ex. music or a video) to play it locally or stream it to an outside device. Should all of these apps be the members of one group and the owner of the data be the creator app and all the other apps be the users who are members of the same group with full access granted to all group members or have I misunderstood something. 

The last paragraph is just an example, maybe a confusing one, but in short I do understand the commands that are to be used, but I do not grasp the big picture and the final goal. Yes, I understand that the goal is to isolate data from unauthorized access, but cannot really grasp how to accomplish that with system-wide apps whose data is used by many, in addition, I would like to avoid a typical newbie mistake, to run everything that errors out by the root user, but to really understand the process and create the structure as its meant to be created/used.

---

### Post by TheFu on 2019-01-05
I always create a new group and add members to it when there is a new purpose needed. I don't reuse older groups, since those often have very specific security requirements.  Screwing up those is good way to be hacked.

And be certain that you practice with the setgid permission bit - this is how you force a default group for all new sub-objects in a directory to be in a specific group.  That makes it nearly mindless for different members of the same group to work together.

As for different processes dealing with files at different stages, don't be afraid to move/copy the files to different directories. The copy will fix the permission, assuming the next directory group permissions are well configured.  

Normally, userids that need write permissions are added to the group while userids that only need read access are left out of the group and gain access permissions only through the "other" permissions.

Is this all clear?  Nothing can replace spending 45 minutes with 3 terminal sessions, 3 userids and at least 2 different groups playing around with chmod and chown.  Try every possible octal permission mode ... there are 4 places, not just 3.  4775 is useful for example.  So is 0711.  I assume you have 775, 755, 664, 750, 640 nailed down already.  When is 711 useful?  When is 751 useful?

---

### Post by Morbius1 on 2019-01-05
Just a quick note before you start to use the setgid bit that TheFu talked about above and you are using Ubuntu 18.04. Best to show an example.

I want to create a folder that allows everyone in a group access and also allow everyone in that group to have write access to every object in it. By definition this is what setgid does. So If I am using Ubuntu 18.04 I go through the steps:

> tester@vub1804:~$ sudo mkdir /TestDir [COLOR=#000080]<-- create the directory[/COLOR]
tester@vub1804:~$ sudo chown :plugdev /TestDir  [COLOR=#000080]<-- change groups to plugdev[/COLOR]
tester@vub1804:~$ sudo chmod g+ws /TestDir [COLOR=#000080]<-- make group access writeable and setgid[/COLOR]
tester@vub1804:~$ ls -dl /TestDir [COLOR=#000080]< -- check permissions[/COLOR]
drwxrwsr-x 2 root plugdev 4096 Jan  5 16:51 /TestDir [COLOR=#000080]<-- exactly what I wanted.[/COLOR]

Now I add a file to that directory:
> tester@vub1804:~$ touch /TestDir/test.txt
And check permissions:
> tester@vub1804:~$ ls -l /TestDir/test.txt
-rw-r--r-- 1 tester plugdev 0 Jan  5 16:54 /TestDir/test.txt

Ruh Row, that's not supposed to happen. The setgid part works as designed but the group doesn't have write access.

Go through the exact same steps in Xubuntu 18.04 or Ubuntu Server 18.04 and you get this:
> morbius@zub1804:~$ ls -l /TestDir/test.txt
-rw-rw-r-- 1 morbius plugdev 0 Jan  5 17:01 /TestDir/text.txt
That's the way it's supposed to work.

The problem is the default umask which dictates how new files are created. In Xubuntu and the server it's 002: new files have 664 permissions - writeable to group. In Ubuntu it's 022: new files have have 644 permissions. The documented way to change the default umask in Linux don't seem to work in Ubuntu 18.04 so I don't know a way to resolve it short of something like bindfs.

---

