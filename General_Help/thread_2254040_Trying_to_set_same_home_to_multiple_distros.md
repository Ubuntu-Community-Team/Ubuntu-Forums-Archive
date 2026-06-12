---
title: "Trying to set same /home to multiple distros"
date: 2014-11-24
forum: General Help
---

### Post by user1397 on 2014-11-24
So I have a /home partition and a separate root partition for ubuntu 14.04.  I tried to make another partition and then installed kubuntu 14.04 on it, and in the partitioning stage I pointed to the /home partition (without reformatting it of course since I have documents on it) and installed the root ( / ) kubuntu in the empty partition.

I used a different username for each distro.  So now in my /home partition I have two users, the one from the ubuntu partition and the one from kubuntu.

My question is, can you make it so that multiple distros use the same /home partition but ALSO the same user folder?  As in /home/user?

Or does that not make any sense?

My head's not working 100%, I need some sleep :(

---

### Post by sudodus on 2014-11-24
It is possible but can create conflicts in the settings (the hidden files in the home directory) to use the same home partition for several installed systems. I would suggest, that you use a common ***data*** partition instead. I use that method, and my home partitions can be quite small. Furthermore, it is easy to use a separate backup method for the data partition.

---

### Post by nerdtron on 2014-11-24
This complexity is what I always try to avoid when dual booting different distros and including windows too.
It a bit hard to get right and it introduces another problem.

/home partitions (assuming you set it correctly and combine in all distros) will include custom config files for users and applications. It will also contain config file regarding your environment and versions of applications installed.

If you have another distro and use the same home partitions, these hidden config files can possibly conflict with each other.
My solution to multibooting distros is to leave each /home partitions in the / partition. I have a separate partition which I mount at /data to hold all my files. Unlike the /home partition, this custom partition contains all my data without any residues from the home folders. I can share this partition freely with each distro installed.


Regarding your situation, wouldn't it be easier if you just install the KDE desktop on top of Ubuntu?

---

### Post by Topsiho on 2014-11-24
As far as I can see you just should use the same user name in both Ubuntu and Kubuntu.
I think I have done so quite some time in the past without any difficulties.
Booting into Ubuntu you use / for Ubuntu and /home/user without any interference from / for Kubuntu
Booting into Kubuntu you use / for Kubuntu and the same /home/user without any interference from / for Ubuntu

Only possibility for problems may be conflicting configuration files in /home/user ...

Topsiho

---

### Post by oldfred on 2014-11-24
I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)


 Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

   howto shared data - by  captain_chaos2
[http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581](http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581)

---

### Post by Topsiho on 2014-11-24
I think you're right :). Never thought of that possibility.
This is a chance to say that I always admire oldfred's answers :)

Topsiho

---

### Post by oldfred on 2014-11-24
oldfred is not creative enough to come up with good answers, but he has good notes. ( I like Zim now.)
And I steal your good answers and add them to my notes. :)

So if around enough, you may see the similarity.

---

### Post by Topsiho on 2014-11-25
That you use something like Zim explains a lot. I never heard of it before, but now I read through it's Getting Started.
It looks great, and this indeed explains how you manage to give your answers. Still great answers, though :)

Topsiho

---

### Post by Bucky Ball on 2014-11-25
Zim's brilliant, and so are oldfred's ideas re. sharing data partitions.

I let Ubuntu (or any other flavour) create the /home *directory* in the / partition, then I delete the default directories in the /home directory and create symlinks to the existing directories in the /data (for instance) partition.

I used to go for using the /home partition for numerous installs (so yes, re. your original question, you can do that) but this way has worked out a lot better for me. ;)

---

### Post by HousieMousie2 on 2014-11-25
My Dad recently set up a machine with multiple hard drives, partitons, distros and users...
Each user/distro got it's own /home (where the config files for that distro would be saved,) then he linked our original /home partitons to a file in the various distro /homes, set the ownership and presto.
So now everything personal is in our original /home partitions (before we added all the extra distros and hard drives) and the config files stay with the mini /home created during the installations.

It's a variation on a theme, but it works well for us.

---

### Post by user1397 on 2014-11-27
Ok well it seems like the consensus is to create a separate partition such as /data for your personal files, while keeping all of the /home partitions in each respective distro's root partition, because of all of the hidden program folders that reside within each /home/user folder, so that no conflicts arise.

I shall apply this :)

---

### Post by user1397 on 2014-11-30
SO...I made a /MyFiles partition to be my data partition and I reinstalled kubuntu first to see what would happen.  What's weird now is that my user does not have write permissions to /MyFiles and so I cannot copy my backup onto that partition. 

I clearly missed some minute detail or does this happen to eveyone and then they have to change the permissions right after the install is complete?

Thanks.

****EDIT: Nevermind!!!  Figured it out, just opened dolphin as root, right click > properties > permissions tab, and changed all permissions to read and write for everyone.

---

### Post by Bucky Ball on 2014-11-30
Great news! Did you create symlinks to the folders in the /Myfiles partition?

You can create the regular folders there, like Videos, Music, Documents, etc., delete the ones in you /home folder in / and create symlinks to there to the folders in the /Myfiles partition, if that makes sense, as suggested previously.

This way, when you install another OS on another partition, you do the same, then whichever OS you boot into, they are all accessing the same folders in /Myfiles via the symlinks in their /home folders.

Good luck.

---

### Post by oldfred on 2014-11-30
I do not know if I mention it above int previous posts, but I also move some of the hidden folders with lots of data.
So my Firefox & Thunderbird profiles, my kmymoney files, and maybe a few others when they start having lots of data.

I actually started sharing Firefox & Thunderbird when first using Ubuntu and knew XP. I knew I wanted to convert but it was a bit of a process. And my wife & I share a computer so she wanted to check email or go on Internet and I had to reboot into XP (3 to 5 minutes :) ) . So when I found you could move profiles & share them it allowed me to make much greater progress on learning Ubuntu. Back then the shared data partition was NTFS, but now everything is in ext4 Linux formatted partition.
I also the just copy profiles with rsync to my laptop when traveling & back when I return. Laptop is configured similarly so I just copy to data partition on laptop.

       [http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by user1397 on 2014-12-01
> **oldfred said:**
> I do not know if I mention it above int previous posts, but I also move some of the hidden folders with lots of data.
So my Firefox & Thunderbird profiles, my kmymoney files, and maybe a few others when they start having lots of data.

I actually started sharing Firefox & Thunderbird when first using Ubuntu and knew XP. I knew I wanted to convert but it was a bit of a process. And my wife & I share a computer so she wanted to check email or go on Internet and I had to reboot into XP (3 to 5 minutes :) ) . So when I found you could move profiles & share them it allowed me to make much greater progress on learning Ubuntu. Back then the shared data partition was NTFS, but now everything is in ext4 Linux formatted partition.
I also the just copy profiles with rsync to my laptop when traveling & back when I return. Laptop is configured similarly so I just copy to data partition on laptop.

       [http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)thanks oldfred, I'll keep that in mind although I think I'm ok with not sharing hidden folders and profiles for now.

> **Bucky Ball said:**
> Great news! Did you create symlinks to the folders in the /Myfiles partition?

You can create the regular folders there, like Videos, Music, Documents, etc., delete the ones in you /home folder in / and create symlinks to there to the folders in the /Myfiles partition, if that makes sense, as suggested previously.

This way, when you install another OS on another partition, you do the same, then whichever OS you boot into, they are all accessing the same folders in /Myfiles via the symlinks in their /home folders.

Good luck.I haven't created symlinks yet, although now I see it's pretty simple with Dolphin, so I'm probably gonna do that once I finish writing this post hehe.  I was going to ask though, did I set my permissions up correctly?  I'll attach a screenshot of the permissions tab of the /myfiles directory.  I just want to make sure my permissions are considered "safe" or perhaps some of it is unnecessary?

---

### Post by nerdtron on 2014-12-05
> I just want to make sure my permissions are considered "safe" or perhaps some of it is unnecessary?

Regarding permissions, I see that the owner is root and everyone can read/write on the that folder you are showing on your screenshot. This can be a security problem and it is not recommended. However if this is just a home computer and is mostly shared among other user, you still can leave it as it is.

The default permissions for normal folders are owned by the current user, and only the owner can read/write while other are read-only.

---

### Post by oldfred on 2014-12-05
I have not used dolphin to set permissions. And only occasionally will use Naulitus to set a file as executable.

If data partition is Linux, you can manually set owership & permissions. Example below uses /mnt/data, use your actual mount point.
 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

With NTFS you can only set ownership & permissions when you mount it. Auto mount of external drives usually gives users full access.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by user1397 on 2014-12-05
> **nerdtron said:**
> Regarding permissions, I see that the owner is root and everyone can read/write on the that folder you are showing on your screenshot. This can be a security problem and it is not recommended. However if this is just a home computer and is mostly shared among other user, you still can leave it as it is.

The default permissions for normal folders are owned by the current user, and only the owner can read/write while other are read-only.Oh ok thanks.

> **oldfred said:**
> I have not used dolphin to set permissions. And only occasionally will use Naulitus to set a file as executable.

If data partition is Linux, you can manually set owership & permissions. Example below uses /mnt/data, use your actual mount point.
 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

With NTFS you can only set ownership & permissions when you mount it. Auto mount of external drives usually gives users full access.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.Thanks oldfred, I used those commands to set the new permissions for my data partition.  Remarking this thread as solved.

---

