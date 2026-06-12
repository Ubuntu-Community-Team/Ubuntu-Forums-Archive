---
title: "Newly configured SSD 240GB with second disc for Data - help"
date: 2014-10-25
forum: General Help
---

### Post by Timmoore001 on 2014-10-25
I use Ubuntu 14.04 on both drives. (I didn't know how to format the data drive so I just installed Ubuntu on it. that worked ok !)

All is well and the SSD drive is MUCH faster than the drive it replaces.  The data drive is 1TB and has  nealy 600GB of data on it.

On the data drive there is one directory I want to use a lot so I want to put an ikon on the Dektop of the SSD drive, that links me directly to that directory.
Only I don't know how to do that.  [IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

Anybody any thoughts on this please let me know if its possible and how to do it.

Many thanks,

Tim

PS  Hope all that makes sense.

---

### Post by oldfred on 2014-10-25
I do not know Unity so do not know details on an icon.

But you will have to permanently mount partition with fstab. And set ownership & permissions. Many mount in /media, some mount in /mnt. The Nautilus default mount now is /media/$USER where $USER is you and you have default settings for ownership & permissions.

I prefer /mnt so it does not show in left panel of Nautilus, but others want it in the left panel. The main reason I do not want it is that I rarely directly use the mount, but link all folders in the data partition back into /home. I replace all the default folders like Documents, Music, Videos etc with the same folders in my data partition. I do this as soon as I install so I have no files in those default folders in/home as otherwise those files would be lost. All data is just in my data partition.

This is manual mounting from terminal and setting ownership & permissions. 

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

You also want to add to fstab. Example byt Morbius1 shows both NTFS and ext4, use the one that applies:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

      
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Timmoore001 on 2014-10-25
Many thanks for replying.

I'm afraid I have extreme difficulty understanding that.

Am I trying to create a 'symbolic link ?

If so does

ln -s target source

do the job ?

I need something that won't nuke the OS if I make a mistake.

right clinking on the directory in question gives various link options but I'm abit terrified of destroying the data that has taken years to gather.

Many thanks again tho...

Tim

---

### Post by Dennis N on 2014-10-25
If you are accessing the data drive frequently, you need to have the partition you use on the data drive mounted at startup or log in, or you could also mount it before use from Nautilus side pane by clicking on its icon.

An alternative to a Desktop icon linked to your special folder is a Bookmark in Nautilus for that folder you use a lot. The bookmark appears (under Bookmarks) in the side pane as long as the partition is mounted. This avoids any symbolic links.

---

### Post by Timmoore001 on 2014-10-25
Brill !  That sounds like its exactly what I need.

I'll try it out and report back as to how it goes !

(Is Doophin the same as Nautilus ?)

A very happy,

Tim

---

### Post by Dennis N on 2014-10-25
Nautilus is Ubuntu's default file manager. Dolphin is the file manager from kde (Kubuntu). I don't use it, but I would suspect it can do the same.

---

### Post by Timmoore001 on 2014-10-25
In Dolphin , right click on a directory and select 'Add to Places' and job done.

It shows up in the left hand side list of likely places worth going to !

Mega Brill !

MANY MANY THANKS !

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by Dennis N on 2014-10-25
Glad to hear you have an solution. And thanks for the feedback.

---

### Post by huwwevans on 2014-10-25
You should probably make sure that your swap partition is on the HDD.  Last I heard SSDs have limited writes before they expire.

---

