---
title: "How can I give multiple users equal access/ownership to the same samba share?"
date: 2013-12-18
forum: General Help
---

### Post by nebhead772 on 2013-12-18
I'm starting to pull my hair out (and I don't have much left unfortunately).

My setup is the following. I have Ubuntu Server 12.04LTS running on a box in my office which has the following SMB share:

> [galactica]
comment=galactica
path=/mnt/galactica
browsable=yes
writeable=yes
guest ok=yes
read only=no
create mask=0777
follow symlinks=yes
directory mask=0777

I have a desktop machine in the family room that my wife and I use (each with separate accounts), which is currently running Ubuntu Client 13.10. I've configured the FSTAB to auto-mount the samba share automatically at boot:

> //192.168.1.118/galactica /media/galactica cifs guest,_netdev,iocharset=utf8,gid=1002,uid=1000 0 0

The GID is a group that has both our user accounts in it (me + wife). The UID is my user account. All of this works just fine in my user account.

When my wife is using the share drive, she is able to create directories with no issue, however the problem arises when she attempts to create files.

When she copies or creates files in the share, the icons show up with a little lock in the lower right hand corner. When looking at the permissions for these files, it appears that my user owns the file and she has only read permissions (group and other have read permission as well).

I've tried many, many different fstab configurations, but nothing seems to help. (including adding her UID, noperm, umask, dmask, fmask, etc.)

Help me internet! You are my only hope.

---

### Post by TheFu on 2013-12-18
Whoa.... I skimmed your question.  Why are you mounting a samba share on a Linux box?  If that is the same Linux machine as holds the HDD, this is not what you want.

Samba shares folders to Windows machines.  The only reason to mount a CIFS share **from Linux** is if the files are hosted under Windows.

The best way to share files between 2 Linux machines is with NFSv4. There is a client side and a server side. [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) should help.  With NFS,  file owner, group, and other permissions are honored with just a few exceptions. It is easy to forget that files are actually located on a different physical machine. It is **THAT good.**

While you can use samba to share files between two UNIX/Linux systems, I wouldn't for systems that are not portable or wifi connected. NFS is much nicer.

---

### Post by papibe on 2013-12-18
Hi nebhead772.
> **TheFu said:**
> NFS is much nicer.
+1

...  and much easier I might add.

You seem to have a good grasp of setting ownership and permissions for a collaborative project. Since samba would add an extra layer on top of the Linux permission and ownership logic you know and understand,  I'd recommend going with NFS.

You would need to:
[LIST]
[*]Install one package.
[*]Add one line to a file to export the directory.
[*]Change slightly the mount on fstab so you use NFS instead of cifs, and
[*]Match your ownership and permissions on the server and in the client.
[/LIST]
This would be a good start: [Simple HOWTO: NFS Server/Client]("http://ubuntuforums.org/showthread.php?t=249889").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by nebhead772 on 2013-12-18
> **TheFu said:**
> Whoa.... I skimmed your question.  Why are you mounting a samba share on a Linux box?  If that is the same Linux machine as holds the HDD, this is not what you want.

Samba shares folders to Windows machines.  The only reason to mount a CIFS share **from Linux** is if the files are hosted under Windows.

The best way to share files between 2 Linux machines is with NFSv4. There is a client side and a server side. [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) should help.  With NFS,  file owner, group, and other permissions are honored with just a few exceptions. It is easy to forget that files are actually located on a different physical machine. It is **THAT good.**

While you can use samba to share files between two UNIX/Linux systems, I wouldn't for systems that are not portable or wifi connected. NFS is much nicer.

Yeah, I probably should have been more clear.  I have several computers in the house including both Windows and Linux boxes.  I have an Ubuntu 12.04LTS server which I use as a NAS drive for all our photos, videos, music, etc.  I need to share these files to all the other machines in the house (windows and linux) and hence have the samba share setup to share to the network.  The Windows machines have absolutely no issue accessing the share and have no permissions issues at all.  However, I have an Ubuntu desktop machine (not the same machine as the server) with two user accounts (mine and wifes) which have trouble with permissions when I try to mount the same share.  

Now, if you are suggesting that I use NFS on my Ubuntu Server to share files with the Ubuntu Desktop machine, that's great.  I can give that a shot.  Will that co-exist with Samba on the server?  Or will I have issues/conflicts?  Will this help eliminate my permissions issues client side? 

Thanks for the response!

---

### Post by bab1 on 2013-12-18
> **TheFu said:**
> Whoa.... I skimmed your question.  Why are you mounting a samba share on a Linux box?  If that is the same Linux machine as holds the HDD, this is not what you want.

Samba shares folders to Windows machines.  The only reason to mount a CIFS share **from Linux** is if the files are hosted under Windows.

This is not really true anymore.  At this point in their development, both have very effective userland filesystem (FUSE) drivers.  NFS and CIFS performance is is about the same.  The difference is That CIFS (both Windows and Samba) is designed to be browsed via a GUI interface.  NFS does not have that ability.  My Linux users like that.

---

### Post by bab1 on 2013-12-19
> **nebhead772 said:**
> I have several computers in the house including both Windows and Linux boxes.  I have an Ubuntu 12.04LTS server which I use as a NAS drive for all our photos, videos, music, etc.  I need to share these files to all the other machines in the house (windows and linux) and hence have the samba share setup to share to the network.  The Windows machines have absolutely no issue accessing the share and have no permissions issues at all.  However, I have an Ubuntu desktop machine (not the same machine as the server) with two user accounts (mine and wifes) which have trouble with permissions when I try to mount the same share.  

Now, if you are suggesting that I use NFS on my Ubuntu Server to share files with the Ubuntu Desktop machine, that's great.  I can give that a shot.  Will that co-exist with Samba on the server?  Or will I have issues/conflicts?  Will this help eliminate my permissions issues client side? 

You can't use NFS if you have windows systems that need to share information.  You problem is fairly easy to solve however.  You actually have the first part already done ( the common group).  To extend that thought you need to add inheritance of the group.  See [here (post #5)]("http://ubuntuforums.org/showthread.php?t=2180383") where I have described the process previously.  Here is an [easy guide]("http://blog.jgriffiths.org/?p=126") to the use of Linux permissions (chmod)

I want to point out that if you want to change the permissions you should follow this```


chmod -R u=rwX,g=rwX[COLOR="#FF0000"]**s**[/COLOR],o=rX <share_root>


```...Using symbolic notation instead of octal allows you to use the X instead of the x.  The capital X means preserve permissions only if the file the is already eXecutable, but do not make executable any others. Also the 's' in the 'g' section (red) resets the sgid for the inheritance again.  Very handy when there is a lot of data.

In summary. you set the inheritance and permissions at the top of the share and everything new will work.  Then you reset the permissions on all the extant files and folders in the share tree.

This will set the Linux file sever.  We may have to tweak the Samba settings in smb.conf.  That is really the final step.

---

### Post by nebhead772 on 2013-12-19
Papibe - Ok, things are going great.  I read the guide that you pointed me to and it couldn't have been easier to setup.  I had a little trouble with Ubuntu Desktop 13.10 not auto-mounting, but I found this thread [here]("http://ubuntuforums.org/showthread.php?t=1139102") which fixed it for me. 

However, now when I create files or directories in the new shares, the permissions appear a bit wonky.  

Owner: nobody  (Read & Write)
Group: -2  (Read Only)

This part of your directions above makes me think I am missing something here, since I didn't see anything specific about the below.

> **papibe said:**
> 

[LIST]
[*]Match your ownership and permissions on the server and in the client.
[/LIST]


Can you elaborate?

Thanks!
Nebhead.

---

### Post by nebhead772 on 2013-12-19
> **bab1 said:**
> You can't use NFS if you have windows systems that need to share information.  You problem is fairly easy to solve however.  You actually have the first part already done ( the common group).  To extend that thought you need to add inheritance of the group.  See [here (post #5)]("http://ubuntuforums.org/showthread.php?t=2180383") where I have described the process previously.  Here is an [easy guide]("http://blog.jgriffiths.org/?p=126") to the use of Linux permissions (chmod)

I want to point out that if you want to change the permissions you should follow this```


chmod -R u=rwX,g=rwX[COLOR=#FF0000]**s**[/COLOR],o=rX <share_root>


```...Using symbolic notation instead of octal allows you to use the X instead of the x.  The capital X means preserve permissions only if the file the is already eXecutable, but do not make executable any others. Also the 's' in the 'g' section (red) resets the sgid for the inheritance again.  Very handy when there is a lot of data.

In summary. you set the inheritance and permissions at the top of the share and everything new will work.  Then you reset the permissions on all the extant files and folders in the share tree.

This will set the Linux file sever.  We may have to tweak the Samba settings in smb.conf.  That is really the final step.

Doh.  Well, I'm sort of already far down the path of setting up NFS based on feedback from others.  But, same concept right?  Maybe you can help with the permissions that I'm seeing here as well.  I'm still am having trouble with permissions after following your instructions.  

Now I'm not able to create directories or files at all inside the share.  As an experiment, I manually set a directory on the share to chmod 777 and I'm able to create files and sub-directories, however again I'm not able to modify them afterwards (they're assigned to nobody/users) with the group permissions set at read only.

---

### Post by bab1 on 2013-12-19
> **nebhead772 said:**
> Doh.  Well, I'm sort of already far down the path of setting up NFS based on feedback from others.  But, same concept right?  Maybe you can help with the permissions that I'm seeing here as well.  I'm still am having trouble with permissions after following your instructions.  

Now I'm not able to create directories or files at all inside the share.  As an experiment, I manually set a directory on the share to chmod 777 and I'm able to create files and sub-directories, however again I'm not able to modify them afterwards (they're assigned to nobody/users) with the group permissions set at read only.

The first thing you should check is that the username is the same on all machines.  The username: bill on a Windows machine will be be understood by Samba and that Samba user should have the same uid as the Ubuntu user named bill.  As a matter of fact this needs to be true in NFS.  The Linux user (bill) on one machine has to have the same uid on the second Linux machine (client and server).

The Samba server will set the user to nobody:nogroup if it can't match the user to the Samba user database.  This is what is happening right now.  Others have devised workarounds to this problem, but I prefer to set the thing up correctly in the first place.

I think you should start at the beginning.  You *do not* need to reinstall Samba on either the client or server.  We will have to reconfigure the server.  All we need to do is edit the smb.conf file.  From the server post the output of these commands ```

cat /etc/hosts

hosname

cat /etc/samba/smb.conf
```

Again, from the server,  post the output of ```
sudo pdbedit -L 
```...this show who is actually a Samba user. 

What are the user names you are using on the other machines (the clients)?  Do they match the users on the Samba server?  In this case if processes use the share, they would then be considered *system users*.  Not humans but still users of the services.

I'll reread your posting so I don't ask the same questions that you have already answered.

You haven't gone so far that you can't recover.

[COLOR="#0000FF"]Edit after reading your later comments.[/COLOR]

> Doh. Well, I'm sort of already far down the path of setting up NFS based on feedback from others. But, same concept right? Maybe you can help with the permissions that I'm seeing here as well. I'm still am having trouble with permissions after following your instructions.

[COLOR="#0000FF"]NFS will never work with Windows.  I've tried this and it won't work.[/COLOR]
> 
Now I'm not able to create directories or files at all inside the share. As an experiment, I manually set a directory on the share to chmod 777 and I'm able to create files and sub-directories, however again I'm not able to modify them afterwards (they're assigned to nobody/users) with the group permissions set at read only.

[COLOR="#0000FF"]This isn't correct at all.  We don't need to dump any data, but we will end up doing what I recommended.  Is this data backed up somewhere.  Don't beat yourself up, it's complicated from a newbies perspective.  Understand that permissions and ownership are easily changed.  If you want I will explain everything step by step.[/COLOR]

---

### Post by TheFu on 2013-12-19
> **bab1 said:**
> This is not really true anymore.  At this point in their development, both have very effective userland filesystem (FUSE) drivers.  NFS and CIFS performance is is about the same.  The difference is That CIFS (both Windows and Samba) is designed to be browsed via a GUI interface.  NFS does not have that ability.  My Linux users like that.

What!!!!!?   I must be misreading this bab1.  NFS shares happen on the system-to-system level and are accessed using any GUI just like local drives physically connected to the machine are.  Plus using NFS skips the entire gvfs crap.  End-users shouldn't need to know where storage is on the network, IMHO. It should just be "available" where ever they need it and it should act the same as local storage for permissions.  CIFS doesn't do this, but NFS does.

To me, the fact that remote shared disks do not appear on the normal file system is a huge flaw in the gvfs stuff. Why should I need to use any GUI?  Sorta reminds me of MS-Windows "Libraries" ... they only work through Exploder, not from cmd.exe or powershell. Yuck.

I must be misunderstanding your point, bab1, since I know how smart you are (extremely!). It is usually you pointing out my lack of understanding and clarity. ;)

NFS provides a nearly-complete file system implementation to other NFS clients that support it. The Linux NFS client does, easily.

Back to the last question - **Can NFS and samba "share" the same file storage?** Yes. No issue. Linux file locking on the HOST will handle any contention issues. This has worked well since the mid-1990s.

Anyway, I hope this is clear. Sometimes I am not as clear as I believe.

Update: From my reading of the later posts, it seems that a 30 min Linux/Unix file permissions tutorial would be helpful to the OP.  There is nothing magical about users, groups, owners and the file permissions on Linux, but it does take a little effort to get a good understanding.

---

### Post by nebhead772 on 2013-12-19
Thanks for everyone jumping in to help me.  I am admittedly a newb when it comes to the permissions stuff so I'm very, very grateful to get all this support.  Here is what I have decided to do in this case. 


1. I'm going to keep the Samba share going to serve my Windows clients in the house.  Everything seems to be working well with respect to Samba and Windows machines accessing it.  (Ain't broke, don't fix it)
2. I've setup the NFS share definition pointing to the same directories and I'd like to get the permissions set up so that all user accounts on my Ubuntu client are able to create files, directories, move files, edit files, etc. freely without concern for permissions.  


Right now, I have NFS server set up, pointing successfully to the share directory (\mnt\galactica\) that I want shared on the Ubuntu client.  And when the Ubuntu client boots, it auto-mounts this directory in \media\galactica like a champ.  I'm actually very happy with the simplicity of NFS setup in fstab and like papibe mentioned, it seems very well integrated.  


OK, on to permissions.  I'm definitely stumped here.  I could definitely use a crash course in understanding all of this.  After doing a bunch of reading (thanks all of you for your pointers to threads) my understanding is this:


1. Permissions need to be set appropriately to allow for group inheritance on both the client and server directories (per BAB1's posts).  i.e. when new files or directories are created, they should follow the same permissions as the parent, right?  I've set the inheritance bits with chmod, but I'm pretty sure that I have the group/owner information incorrect for all files.  I need some guidance there (see #2)
2. Users from the client need to be mapped to the server.  I am assuming I should create these users on the server (since they do not currently exist) and put them into a group together on the server, with the same names as I'm using on the client.  However, I'm not sure how to link these two or specify the group for the share?  Is that implicit from the group ownership of the directories/files (meaning I will need to chgrp to something like 'users' to include all of the users)


So here is what I think I may need to do on the server side (assuming my client already has accounts for ben & suzy):


```

sudo adduser ben
sudo adduser suzy

```


Then, I need to go modify the share such that it is owned by the users group: 


```
 
sudo chown root:users /mnt/galactica
sudo chmod 2775 /mnt/galactica
chmod -R u=rwX,g=rwX,o=rX /mnt/galactica/*

```


Then on the client side, prior to mounting nfs: 


```
 
sudo chown root:users /media/galactica
sudo chmod 2775 /media/galactica
chmod -R u=rwX,g=rwX,o=rX /media/galactica/*

```


Then on the client side, modify the fstab to mount the NFS share as normal and away we go.  


In /etc/fstab
```

192.168.1.118:/mnt/galactica /media/galactica nfs rsize=8192,wsize=8192,timeo=14,intr

```


Then mount:
```

sudo mount -a

```


Does that look like what we need to do here?  Is there any other magic that needs to be done to link up the user accounts or are we good at this point?


I'm at work right now, so I won't be able to attempt any of this until I get home this evening, but feedback before then would definitely help me greatly.  


Thanks again for all your help.

---

### Post by bab1 on 2013-12-19
> **TheFu said:**
> What!!!!!?   I must be misreading this bab1.  NFS shares happen on the system-to-system level and are accessed using any GUI just like local drives physically connected to the machine are. 

You are misreading the whole point.  Access is the same, browsing *unmounted* shares is what I'm talking about in this context.
> 
Plus using NFS skips the entire gvfs crap.

I have never has any problems with gvfs.  The mount instructions are set arbitrarily the Gnome developers.  There are some gotchas, but for the average user gvfs is the least of the problems that can come up.  
> 
End-users shouldn't need to know where storage is on the network, IMHO. It should just be "available" where ever they need it and it should act the same as local storage for permissions.  CIFS doesn't do this, but NFS does.

IMHO is just that.  Let's just leave it at that.  All permissions are set by OS settings.  Samba can't override that.
> 
To me, the fact that remote shared disks do not appear on the normal file system is a huge flaw in the gvfs stuff. Why should I need to use any GUI?  Sorta reminds me of MS-Windows "Libraries" ... they only work through Exploder, not from cmd.exe or powershell. Yuck.

IMHO again. :-)  I have no problem with using "hidden mount points".  You just have to know what you are dealing with.  As a matter of fact if the OP needed a specific mount command or mount point that can be accommodated.    

I hear your opinions and prejudices.  They were mine also many years ago when I managed SUN Solaris networks and had to *accommodate a few Windows users.*  Experience has taught me to try and understand the developers intentions (and limitations).  Old dogmas die hard and admittedly for profit enterprises (Windows) have different objectives.  I tend to look at the tool and not the company the provides it.

---

### Post by bab1 on 2013-12-19
> **nebhead772 said:**
> Thanks for everyone jumping in to help me.  I am admittedly a newb when it comes to the permissions stuff so I'm very, very grateful to get all this support.  Here is what I have decided to do in this case. 


1. I'm going to keep the Samba share going to serve my Windows clients in the house.  Everything seems to be working well with respect to Samba and Windows machines accessing it.  (Ain't broke, don't fix it)

By working I assume you mean you can access the share, but the permissions are not correct.
> 
2. I've setup the NFS share definition pointing to the same directories and I'd like to get the permissions set up so that all user accounts on my Ubuntu client are able to create files, directories, move files, edit files, etc. freely without concern for permissions.

These are called NFS exports.  I say this only so that we don't confuse a share (Windows) with an export (NFS).  I have plenty of Samba shares that are also NFS exports.  Some things work better in some situations.  Use the tool that works for you.  We will get the file system permissions worked out.  You will see that most of it will be at the server.
>   
Right now, I have NFS server set up, pointing successfully to the share directory (\mnt\galactica\) that I want shared on the Ubuntu client.  And when the Ubuntu client boots, it auto-mounts this directory in \media\galactica like a champ.  I'm actually very happy with the simplicity of NFS setup in fstab and like papibe mentioned, it seems very well integrated.  


OK, on to permissions.  I'm definitely stumped here.  I could definitely use a crash course in understanding all of this.  After doing a bunch of reading (thanks all of you for your pointers to threads) my understanding is this:

1. Permissions need to be set appropriately to allow for group inheritance on both the client and server directories (per BAB1's posts).  i.e. when new files or directories are created, they should follow the same permissions as the parent, right? 

Close but not quite accurate.  All of these *shares* and *exports* allow you to mount a section of the servers local file system (a branch (in your case /mnt/galactica)) to a remote client.  The permissions are inherited from the servers settings.  The part the needs to match is the user uid and gid.  Linux uses the uid/gid to ID a specific user.  The name attached to that is a peripheral concern.  It is for humans to make sense of the listing.  If the user bab1 is user 1000:1000 on one machine then you need make sure bab1 1000:1000 is on all networked machines.
> 
I've set the inheritance bits with chmod, but I'm pretty sure that I have the group/owner information incorrect for all files.  I need some guidance there (see #2)
2. Users from the client need to be mapped to the server.  I am assuming I should create these users on the server (since they do not currently exist) and put them into a group together on the server, with the same names as I'm using on the client.  However, I'm not sure how to link these two or specify the group for the share?  Is that implicit from the group ownership of the directories/files (meaning I will need to chgrp to something like 'users' to include all of the users)

Let me be very careful here.  The problem does include the mismatch and lack of users where you need them.  Let's talk about the changes before we make them from here on out.

The steps needed for Samba to work correctly are:
[LIST]
[*]Create a Linux user (adduser)
[*]Create a Samba user (smbpasswd -a)
[/LIST]
I recommend that you use adduser instead of useradd.  Debian derived distros (Ubuntu) have a different user setup that useradd doesn't know about.

We need to see what users are already created on the server. Post the output of```
getent passwd|grep 100
``` 

Once this is done we can work with the file permissions.

---

### Post by nebhead772 on 2013-12-19
Here's the output from the above gentent command:

```

parmeter@ubuntu-NAS:~$ getent passwd|grep 100                                   
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
parmeter:x:1000:1000:Ben Parmeter,,,:/home/parmeter:/bin/bash
ben:x:1001:1001:,,,:/home/ben:/bin/bash
suzy:x:1002:1002:,,,:/home/suzy:/bin/bash

```

---

### Post by TheFu on 2013-12-19
> **nebhead772 said:**
> 1. I'm going to keep the Samba share going to serve my Windows clients in the house.  Everything seems to be working well with respect to Samba and Windows machines accessing it.  (Ain't broke, don't fix it)

That's my belief too. Samba is fine for WindowsClient-to-LinuxServer file sharing on the same internal network. I get pretty great performance from samba here.

> **nebhead772 said:**
> 2. I've setup the NFS share definition pointing to the same directories and I'd like to get the permissions set up so that all user accounts on my Ubuntu client are able to create files, directories, move files, edit files, etc. freely without concern for permissions.  

The key to NFS is that users and groups need to match on both the clients and server. After that, everything *just works*.  When I say they need to match, that means the the uid numbers and  the gid numbers in the /etc/passwd, /etc/shadow, /etc/group files must match.  In an enterprise, people will use LDAP or NIS+ to handle user and groups across all their machines, so having matching uids/gids is nearly automatic, but that is overkill for a home setup.  If you change a uid number on any machine, you'll want to ensure that every file owned by that userid is also **chown**-'ed over.  On most Ubuntu systems I've seen, the first account is 1000 and the 2nd is 1001, 1002, 1003 .... you get the idea. So, when you create a new account for new users, if they are made in the same order on each machine, the uid/gid will align.

Further, to have multiple users be able to share editing and writing to a file or directory, then those users must be in the same group AND the directory and/or files must be set to be in that same group.  Once the users are in the same group and the uid/gid numbers match on the clients and server, then you can use **chmod** and **chgrp** to set the necessary permissions from either the NFS client OR the server.  Users can be in multiple groups, but there is an idea of the default group.  Might want to read a little about UNIX groups. These are extremely powerful, yet simple ideas.  It would be smart to change the default **umask** for each user to allow group read/write unless they specifically want it some other way.  The group used for their HOME directory doesn't need to be this new group created to share files, in fact, I wouldn't do that. 

In a multiuser environment, taking care with group file permissions is a core consideration.  Read up on the **chmod g+s** command to see how that can make managing shared directories easier. Once you get all the permissions set nicely, you'll almost never need to worry about them again because new files and dirs will be in the correct group *automagically*.  Basically, when I setup a new shared directory, I'll set the top level directory permissions to be 770, then add g+s to it and ensure the directory is owned by the correct group. From that point on, things sorta *just work* as expected for everyone.

> **nebhead772 said:**
> Right now, I have NFS server set up, pointing successfully to the share directory (\mnt\galactica\) that I want shared on the Ubuntu client.  And when the Ubuntu client boots, it auto-mounts this directory in \media\galactica like a champ.  I'm actually very happy with the simplicity of NFS setup in fstab and like papibe mentioned, it seems very well integrated.  

Any directory (best if empty) can be a mount point for a partition or NFS mount.  I like to put them under /d/ across all my systems - that way, the same files are in the same place regardless.  Plus /d is short to type.  I think of /mnt as a temporary place to mount things for special needs and just a few hours, but that is just opinion. ;)  In the old days, we'd use /export/{insert-cleaver-mount-name} as the place for non-local NFS mounts.

I hope they are recommending the use of **autofs** for the client machines to mount NFS exports. This way only when the storage is accessed does it get mounted. There are some nice options available with autofs too, which uses fewer resources.

May thanks to bab1 for calling out my "opinions." It is true, those are opinions ... built over 20+ yrs as a cross-platform Windows and UNIX programmer and admin. Since I'm here posting, you can tell which side I'm slanted towards these days. ;)

gvfs , IMHO, is a terrible hack.  It makes things appear as file system mounts, but doesn't actually do that.  It only appears that way in selected, "blessed" programs.  That is the main reason it is low on my suggested tool list.  

gvfs isn't installed on most of my desktops either. I guess it is only part of the default Ubuntu Desktop install, so if you use a different GUI or, dog forbid, Ubuntu Server, then it will need to be manually installed.  To me, it is redundant as there are great tools to perform the same task that have 15+ yrs of testing. These are solid, but they just don't have a GUI.

However, if gfvs works for you, please use it.  Just don't be surprised when it doesn't work as expected for all needs. Lots of threads in these forums about issues related to gvfs.  If gvfs were made to work everywhere, like other mount tools, my complaints would disappear.  About the only place there I see gvfs to be highly useful is when accessing flash drives and MTP devices, things that are mounted for 10 minutes at a time and only used with drag-n-drop file copies.

Still, these are opinions. Disregard those that don't work for you and sorry for any offense that may have occurred.

---

### Post by TheFu on 2013-12-19
> **nebhead772 said:**
> Here's the output from the above gentent command:

```

parmeter@ubuntu-NAS:~$ getent passwd|grep 100                                   
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
parmeter:x:1000:1000:Ben Parmeter,,,:/home/parmeter:/bin/bash
ben:x:1001:1001:,,,:/home/ben:/bin/bash
suzy:x:1002:1002:,,,:/home/suzy:/bin/bash

```

Any users that will access the NFS export from a client NFS machine needs to match those uids and guids. See my other post for details on the files involved.

BTW, I didn't know that getent was a CLI command. Nice.  When programming, I've used it to ensure LDAP, NIS, NIS+ and /etc/{insert file here} where checked in the correct order for the system, but dind't know it was available from the shell. VERY NICE. Thanks.

---

### Post by bab1 on 2013-12-19
Please post the output of:
sudo pdbedit -L
getent group users

---

### Post by nebhead772 on 2013-12-19
```

parmeter@ubuntu-NAS:~$ sudo pdbedit -L
[sudo] password for parmeter: 
nobody:65534:nobody
parmeter:1000:Ben Parmeter
david:4294967295:David Parmeter
parmeter@ubuntu-NAS:~$ getent group users
users:x:100:

```

David is a user that I deleted recently (has been a completely inactive account).

---

### Post by bab1 on 2013-12-20
No ben or suzy samba users.

No ben or suzy in the group users.

I'm busy for the rest of the night and away from home.  These last few posts are from an old iTouch.  :-)

Add the users to the linux system. Then add the users to the group named users.  Lastly add the users to samba with:
sudo smbpasswd -a <username>

Use the same user pass as you used when you created the linux user.

Post the results back here.  Use getent and pdbedit.

I'll check back later tonight and respond in the morning.

---

### Post by nebhead772 on 2013-12-20
OK, logged into both the new accounts and now they're showing up when I do this: 

```

parmeter@ubuntu-NAS:~$ sudo pdbedit -L
nobody:65534:nobody
parmeter:1000:Ben Parmeter
ben:1001:
david:4294967295:David Parmeter
suzy:1002:

```

But they are still not showing up in the group 'users'.  Newb question, but how might I get Ubuntu to get all of my users into the group 'users'?

Like this?
```

usermod -a -G users ben

```

---

### Post by bab1 on 2013-12-20
Yes that is correct

---

### Post by nebhead772 on 2013-12-20
OK - Here we go:

```

parmeter@ubuntu-NAS:~$ getent group users
users:x:100:ben,suzy,parmeter

```

Looks like that was successful.

---

### Post by bab1 on 2013-12-20
So now we have the user and groups on the NAS set up.

Show me the output of this:
ls -ld /mnt/galactica

...and also:
ls -l /mnt/galactica

---

### Post by nebhead772 on 2013-12-20
> **bab1 said:**
> So now we have the user and groups on the NAS set up.

Show me the output of this:
ls -ld /mnt/galactica

...and also:
ls -l /mnt/galactica

Ok, here it goes with directory names obscured for my privacy. :) 

```

parmeter@ubuntu-NAS:~$ ls -ld /mnt/galactica
drwxrwsrwx 25 root users 4096 Dec 18 20:20 /mnt/galactica
parmeter@ubuntu-NAS:~$ ls -l /mnt/galactica
total 144
drwxrwsrwx 12 nobody   users  4096 May  5  2013 
drwxrwsrwx  2 nobody   users  4096 Nov 17  2012 
drwxrwsrwx  8 nobody   users  4096 Mar 18  2013 
drwxrwsrwx 17 nobody   users  4096 Nov  7 19:40 
drwxrwsrwx  2 nobody   users  4096 Apr 30  2011 
-rwxrwsrwx  1 www-data users     0 Jun 27  2012
drwxrwsrwx 10 nobody   users  4096 Jun  5  2013 
-rwxrwsrwx  1 nobody   users   456 Jul 17 22:54 
drwxrwsrwx  2 nobody   users 16384 Feb 15  2012 lost+found
drwxrwsrwx  2 nobody   users  4096 May 10  2012 
drwxrwsrwx  8 nobody   users  4096 Dec  8 17:48 
drwxrwsrwx  3 parmeter users  4096 May  4  2012 
drwxrwsrwx  2 nobody   users  4096 Jun 23 19:53 
drwxrwsrwx 19 nobody   users 40960 Dec 18 22:47 
drwxrwsrwx  4 nobody   users  4096 Aug 21  2012 
drwxrwsrwx 54 nobody   users 12288 Nov  7 19:55 
drwxrwsrwx  5 nobody   users  4096 Oct 17 13:13 
drwxrwsrwx  5 nobody   users  4096 Dec 17 20:55 
drwxrwsrwx  4 nobody   users  4096 Dec 18 23:12 
drwxrwsrwx  6 nobody   users  4096 Jan 26  2013 
drwxrwsrwx  3 nobody   users  4096 Nov  5 18:26 
drwxrwsrwx  2 nobody   users  4096 Feb 16  2012 
drwxrwsrwx  4 parmeter users  4096 Jun 27  2012 

```

---

### Post by bab1 on 2013-12-20
> **nebhead772 said:**
> Ok, here it goes with directory names obscured for my privacy. :) 

```

parmeter@ubuntu-NAS:~$ ls -ld /mnt/galactica
drwxrwsrwx 25 root users 4096 Dec 18 20:20 /mnt/galactica
parmeter@ubuntu-NAS:~$ ls -l /mnt/galactica
total 144
drwxrwsrwx 12 nobody   users  4096 May  5  2013 
drwxrwsrwx  2 nobody   users  4096 Nov 17  2012 
drwxrwsrwx  8 nobody   users  4096 Mar 18  2013 
drwxrwsrwx 17 nobody   users  4096 Nov  7 19:40 
drwxrwsrwx  2 nobody   users  4096 Apr 30  2011 
-rwxrwsrwx  1 www-data users     0 Jun 27  2012
drwxrwsrwx 10 nobody   users  4096 Jun  5  2013 
-rwxrwsrwx  1 nobody   users   456 Jul 17 22:54 
drwxrwsrwx  2 nobody   users 16384 Feb 15  2012 lost+found
drwxrwsrwx  2 nobody   users  4096 May 10  2012 
drwxrwsrwx  8 nobody   users  4096 Dec  8 17:48 
drwxrwsrwx  3 parmeter users  4096 May  4  2012 
drwxrwsrwx  2 nobody   users  4096 Jun 23 19:53 
drwxrwsrwx 19 nobody   users 40960 Dec 18 22:47 
drwxrwsrwx  4 nobody   users  4096 Aug 21  2012 
drwxrwsrwx 54 nobody   users 12288 Nov  7 19:55 
drwxrwsrwx  5 nobody   users  4096 Oct 17 13:13 
drwxrwsrwx  5 nobody   users  4096 Dec 17 20:55 
drwxrwsrwx  4 nobody   users  4096 Dec 18 23:12 
drwxrwsrwx  6 nobody   users  4096 Jan 26  2013 
drwxrwsrwx  3 nobody   users  4096 Nov  5 18:26 
drwxrwsrwx  2 nobody   users  4096 Feb 16  2012 
drwxrwsrwx  4 parmeter users  4096 Jun 27  2012 

```

Well here is our first bit of pain. The entire directory and I assume the same for all subdirectories and their contents are set to 2777 not 2775.  Here is what it should look like (blue) and what it is now (red)```

[COLOR="#0000FF"]drwxrwsr-x  [/COLOR] 4 parmeter users  4096 Jun 27  2012
[COLOR="#FF0000"]drwxrwsrwx[/COLOR]  4 parmeter users  4096 Jun 27  2012 

```...This means that all users can read, right, and execute in all of these directories.  Not a good thing.  In addition you have files the anyone can modify and execute.  This is definitely a security breach. This one specifically because it refers to your Apache Web Server```

-[COLOR="#FF0000"]rwxrwsrwx[/COLOR]  1[COLOR="#FF0000"]**[SIZE=2] www-data users[/SIZE]**[/COLOR]     0 Jun 27  2012

```

The first thing we should do is this```
sudo chmod -R 2775 /mnt/galactica/CODE]...This removes the *others *write ability for the entire share.
Next you need to remove the executable abilities for the **files** should not be executable.  For sure all the ones that are world executable (by the group others)you can easily do this by using chmod, **but you have to do each directory separately** because we do not want to remove the executable ability for the directory for others.  As an example you would do this on a **file**[CODE]
sudo chmod 664  /mnt/galactica/<file>

```...Files don't really need the sgid sgid set.  The sgid bit is for inheritance at creation time so it only needs to be set on the directory.  Unfortunately chmod doesn't separate out the directory form the file.  Yes this can be scripted, but I don't have one in my cookbook.  This is what @TheFu was talking about when he said to use a clean (empty) directory as the share foot and set the permissions at 2775.  This would have set the permissions at 2775 for the subdirectories while the file permissions would all be 0664.

Hopefully there aren't many subdirectories involved or you decide that you only need to do a few strategic files in a few directories.  I'm sure that there are other ways to do this, but I've never used them.

---

### Post by nebhead772 on 2013-12-21
Maybe I can start with an empty directory and start moving things in and changing permissions over time.  Unfortunately, I have tons of files in this directory with tons of sub-directories.  I'll close the security issues by broadly changing the 'other' permissions.  

Thanks!

---

### Post by TheFu on 2013-12-21
> **nebhead772 said:**
> Maybe I can start with an empty directory and start moving things in and changing permissions over time.  Unfortunately, I have tons of files in this directory with tons of sub-directories.  I'll close the security issues by broadly changing the 'other' permissions.  

Thanks!

You don't need to do that.  

Changing permissions from the shell recursively to all subdirectories isn't hard and doesn't take much time ... just a few seconds even for many TB of files.  I think Bab1 provided the commands above.  Should be a mix of **sudo chown -R** and **chmod -R**.  Please re-read his most recent post.

---

### Post by 1clue on 2013-12-21
Wow.

There's quite a bit of FUD going on in both directions here.

Both CIFS and NFS can work well in a mixed environment.  There are advantages and disadvantages to each, and they will probably affect your choice based on things only you know about your environment.  The best bet is to read some documentation and some FAQs and, most of all, take everything posted by a user with a grain of salt, and an understanding of which service is their favorite.

There are good NFS drivers for Windows, both free and commercial.  Likewise, CIFS support is good on Linux too.

Almost any home/small business NAS device you get anymore is a Linux-based box which offers CIFS and NFS shares over the same data, as well as whatever Apple uses.  These are stable enough to put your business on it.

You might consider looking at FreeNAS or similar.  It's a FreeBSD based NAS operating system.  You could run it directly or put it on a VM, if you have other things you want your server hardware to do.

---

### Post by bab1 on 2013-12-21
> **TheFu said:**
> You don't need to do that.  

Changing permissions from the shell recursively to all subdirectories isn't hard and doesn't take much time ... just a few seconds even for many TB of files.  I think Bab1 provided the commands above.  Should be a mix of **sudo chown -R** and **chmod -R**.  Please re-read his most recent post.

You can't just chmod recursively down the tree. For the file permissions you need chmod 0664 and for the directories need chmod 2775.  In this case the OP has recursively made the entire branch (all directories and all files) 2777.  The ownership has already been taken care of.

[COLOR="#0000FF"]Edit:  I have written a small script to chmod the files only to 0664.  So that problem is solved now.[/COLOR]

---

### Post by nebhead772 on 2013-12-22
> **1clue said:**
> You might consider looking at FreeNAS or similar.  It's a FreeBSD based NAS operating system.  You could run it directly or put it on a VM, if you have other things you want your server hardware to do.

Yup, I ran FreeNAS 7 before, but it wasn't keeping up with my hardware (drivers for USB3.0, ethernet, chipset) and thus wasn't getting very good bandwidth at all.  Also, I found it not great for software compatibility (i.e. subsonic, plex, etc.) and required a good deal of shoehorning to get things to work in tandem with it.  I have to say, the setup of FreeNAS and general usage was amazing.  I have briefly looked at OpenMediaVault instead, since it runs on Debian it would be a bit less difficult to work with than BSD.  Haven't taken the plunge with that yet.  I'm pretty happy with my Ubuntu Server setup and have put many hours installing software like SabNZBd and SickBeard.

---

### Post by 1clue on 2013-12-22
Ya, FreeNAS not for everyone.  But if nothing else it (or a Linux-based alternative) might give you clues as to configuration for both NFS and CIFS, to get everything behaving the same way on both file sharing services.

---

### Post by Morbius1 on 2013-12-22
Before anyone gets all medieval on me hear me out first: I may have a possible answer to why your mount isn't working as you want.

*** There's really nothing wrong with your share definition. It's a guest share, the folder being shared is owned by "nobody", and all of your remote users are adding files as "nobody". Just don't add any shares that require authentication or it will hose everything up - although it's fixable.

*** The problem isn't really your mount expression either. 

*** The problem is you are using Ubuntu 13.10 as the client OS. 

_In Ubuntu 13.04 and earlier:_

Somebody adds a file to the local mount point in Ubuntu 12.10 it will add as 664 to the local mount point and the mount will force it to have gid=1002 so it will work.

_In Ubuntu 13.10:_

There is a bug in the default umask mechanism that will not be fixed so if somebody adds a file it will save as 644. It's unwritable to everyone else locally.

Give this a shot:
```
//192.168.1.118/galactica /media/galactica cifs guest,_netdev,iocharset=utf8,gid=1002,uid=1000,dir_mode=0770,file_mode=0660,nounix 0 0 
```

---

### Post by bab1 on 2013-12-22
> **Morbius1 said:**
> Before anyone gets all medieval on me hear me out first: I may have a possible answer to why your mount isn't working as you want.

*** There's really nothing wrong with your share definition. It's a guest share, the folder being shared is owned by "nobody", and all of your remote users are adding files as "nobody". Just don't add any shares that require authentication or it will hose everything up - although it's fixable.

*** The problem isn't really your mount expression either. 

*** The problem is you are using Ubuntu 13.10 as the client OS. 

_In Ubuntu 13.04 and earlier:_

Somebody adds a file to the local mount point in Ubuntu 12.10 it will add as 664 to the local mount point and the mount will force it to have gid=1002 so it will work.

_In Ubuntu 13.10:_

There is a bug in the default umask mechanism that will not be fixed so if somebody adds a file it will save as 644. It's unwritable to everyone else locally.

Give this a shot:
```
//192.168.1.118/galactica /media/galactica cifs guest,_netdev,iocharset=utf8,gid=1002,uid=1000,dir_mode=0770,file_mode=0660,nounix 0 0 
```

I assume you mean [[COLOR="#FF0000"]**this**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686") and  [**[COLOR="#FF0000"]this[/COLOR]**]("http://askubuntu.com/questions/384514/how-to-set-the-umask-in-13-10").

---

### Post by nebhead772 on 2013-12-31
[SIZE=2]All - I wanted to let everyone know that I finally did resolve this issue.  With the excellent help of Bab1 and the pointer from Morbius1 I was able to get the right guidance to make it work.  Just to close the thread out, here is what we did to resolve:

1. I decided to go back to SMB/CIFS Samba server instead of NFS and made sure my share was mounted on my Ubuntu 13.10 client with the following: 

```
//192.168.1.118/galactica /media/galactica cifs guest,_netdev,iocharset=utf8,gid=1002,uid=1000,dir_mode=0770,file_mode=0660,nounix 0 0
```

Where GID=1002 is a group that contains the users that should have access to the share.

2. Then, I followed the [launchpad]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686") link that Bab1 provided in his last post to do the following on my Ubuntu 13.10 client:
[/SIZE]
[LIST]
[*][SIZE=2]Download the upstart deb package from here:  [https://launchpad.net/ubuntu/trusty/+package/upstart](https://launchpad.net/ubuntu/trusty/+package/upstart)  (specifically for me, 64-bit here: [https://launchpad.net/ubuntu/trusty/amd64/upstart/1.11-0ubuntu1](https://launchpad.net/ubuntu/trusty/amd64/upstart/1.11-0ubuntu1)[/SIZE]
[*][SIZE=2]Install the package:[/SIZE]
[/LIST]
[INDENT][SIZE=2]```
sudo dpkg -i upstart_1.11-0ubuntu1-amd64.deb
``` [/SIZE][/INDENT]

[LIST]
[*][SIZE=2]Reboot[/SIZE]
[/LIST]
[SIZE=2]
Now I can read/write create files between users and everyone has equal access.  Awesome work everyone and thanks for the help.

I still need to fix my permissions on the server side, but I'll leave that out of this thread for now.  Again, many thanks to Bab1 for taking the time to help me.[/SIZE]

---

