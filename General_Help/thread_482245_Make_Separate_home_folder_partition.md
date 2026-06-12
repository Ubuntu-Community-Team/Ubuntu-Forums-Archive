---
title: "Make Separate /home folder partition"
date: 2007-06-23
forum: General Help
---

### Post by strange_cathect on 2007-06-23
Hello,

I've been trying to use this [guide]("http://www.psychocats.net/ubuntu/separatehome") to make a separate partition for my /home folder.

While using the Live CD, I try to change the size of a NTFS partition but it keeps re-mounting for some reason, preventing me from changing it.

Has anyone had this problem?

---

### Post by Silenus on 2007-06-23
It shouldn't mount, are you following it command by command?

---

### Post by strange_cathect on 2007-06-23
Ok,

So I've now followed every command explicitly and successfully moved my home folder.  However, I now have a big problem:

Virtually none of my preferences were moved for some reason: desktop settings, background pictures, font preferences, bookmarks in firefox, mozilla firebird email settings and accounts and mail.  

How did this happen?

---

### Post by merlinus on 2007-06-23
When you llok at /home using Nautilus (or Thunar), and set it to show hidden files (Ctrl-H), do you see folders that begin with a dot (for example .mozilla, .mozilla-thundebird)?

-merlin

---

### Post by strange_cathect on 2007-06-23
Yes.  But all of those folders have a red "X" flag on the top right corner of them.

Aha: is this a permissions problem?  I don't have permissions to view or open these folders in the new partition?  

Does this sound like we're onto something?

---

### Post by merlinus on 2007-06-23
Yes, I think it is a permissions problem.

Just to be sure, try this in a terminal:

```

sudo nautilus

```Navigate to File System/Home/Username and see if the red exes are gone.

Remember to Show Hidden Files (Ctrl-H).

But be careful, as you are running Nautilus as root and can inadvertently delete things that wil screw up your system!

-merlin

---

### Post by coldstatue on 2007-06-24
I have the same situation. So now that I've tried Nautilus as su, and am sure that's the problem, how do I fix it? Thanks.

---

### Post by coldstatue on 2007-06-24
double post

---

### Post by merlinus on 2007-06-24
Try this:

```

sudo chown -R username:username /home

```(username is your username)

---

### Post by strange_cathect on 2007-06-24
Thank you for your replies.  Before I could use your method, I tried to use the "recovery" described in the article at psychocats.net:

> sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

Now, when I load up Ubuntu, it is unable to find the /home folder. (Or, at least /home is not located where I have told Ubuntu to find it).

Home is located on the following volume:

> /dev/sda4

I am currently using a Live CD--how can I instruct Ubuntu to find the home folder's new location?

Thank you very much...

---

### Post by strange_cathect on 2007-06-24
Merlin, others,

Thank you for your patient replies.

Let me try to explain my problem as it stands.  As the series of posts above indicate, I tried to create a separate partition for my **/home** folder.  I have succeeded in creating the partition and copying my **/home** folder to that partition.

At present, my **fstab** file must not be working correctly because at login I am told that my /home folder is not where it should be.  I believe I need to do two things:

1. Edit **fstab** to point to my new partition.
2. Change the permissions on the new partition so that the can be used.

Here is my current fstab file content:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=47b643ca-6c0b-4805-a9b2-3034f19dacb2 /               ext3    rw,errors=remount-ro 0       1
# /dev/sda5
UUID=61b67e85-6700-4bcf-bfb6-241fcc3d6ce5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I think I need to add this line to fstab:

> 

**/dev/sda4  /home ext3  defaults  0 2**



Will doing this solve issue #1 above?

---

### Post by merlinus on 2007-06-24
Just to be certain:

```

sudo fdisk -l
df -h
blkid

```Enter these one at a time in a terminal.  l is a lowercase L.

-merlin

---

### Post by strange_cathect on 2007-06-24
merlin,

Here is the result:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2515    20201706    7  HPFS/NTFS
/dev/sda2            8012       14318    50660977+  83  Linux
/dev/sda3           14319       14593     2208937+   5  Extended
/dev/sda4            2516        8011    44146620   83  Linux
/dev/sda5           14319       14593     2208906   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 128 MB, 128974848 bytes
8 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         979      125296    6  FAT16
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  152K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   16K  506M   1% /tmp
/dev/sda4              42G   14G   27G  34% /media/disk
/dev/sda1              20G   12G  7.6G  61% /media/disk-1
/dev/sda2              48G   31G   16G  67% /media/disk-2
/dev/sdc1             123M   87M   36M  71% /media/LEXAR MEDIA
ubuntu@ubuntu:~$ blkid
/dev/sdc1: SEC_TYPE="msdos" LABEL="LEXAR MEDIA" UUID="17E9-242F" TYPE="vfat" 


---

### Post by merlinus on 2007-06-24
What is /dev/sdb1?

Also, do you have a flashdrive (sdc1) plugged in when running these commands?

I am surprised that blkid did not give more info.

The mountpoints for sda2 and sda4 seem strange.

And nothing is showing up as /home.  Maybe because you undid the changes from  psychocat????

-merlin

---

### Post by strange_cathect on 2007-06-24
Merlin,

Yes: I did have a flashdrive plugged in.  I used to to save a copy of fstab and the fstab_backup I created during the psychocats terminal session.

I am really out of my league with your other comments: mount points, blkid, etc.  I don't really know what to do at this point.  Its frustrating: I have two perfect copies of home/alan but can't seem to use them or figure out how to get Ubuntu to locate them.

To answer your question...here is a tour of my system:

> /dev/sda1 * 1 2515 20201706 7 HPFS/NTFS
/dev/sda2 8012 14318 50660977+ 83 Linux
/dev/sda3 14319 14593 2208937+ 5 Extended
/dev/sda4 2516 8011 44146620 83 Linux
/dev/sda5 14319 14593 2208906 82 Linux swap / Solaris

I am dual booting XP and Ubuntu on my first hard drive.  /sda1 is a partition for Windows.  /sda2 is the Ubuntu partition. /sda4 is the space where I tried to place my /home folder.

I have another hard drive that uses ext3 but is only for storage and is unrelated to this problem.

At present, /sda4 only has one folder on it: /alan.  Somehow it does not have /home/alan.  

--Alan



> **merlinus said:**
> What is /dev/sdb1?

Also, do you have a flashdrive (sdc1) plugged in when running these commands?

I am surprised that blkid did not give more info.

The mountpoints for sda2 and sda4 seem strange.

And nothing is showing up as /home.  Maybe because you undid the changes from  psychocat????

-merlin

---

### Post by r0ck80y on 2007-06-24
your /etc/fstab file does not have the /home entry with the partition. I think it should be there.

---

### Post by merlinus on 2007-06-24
OK.  As rockboy suggested, and you as well, try adding this line to /etc/fstab:

/dev/sda4 /home ext3 defaults 0 0

then:

```

sudo mount -a

```and see what happens.

You may have to manually mount sda4 as home, but first things first.

-merlin

---

### Post by strange_cathect on 2007-06-24
One problem is that I don't have /home on that partition.  I only have /alan.  I need to create /home and then put /alan inside it.  (I'm guessing here...tell me if this is wrong).  The other problem is that I have is that I don't have permissions to change these folders (or fstab) so I need help with that.

Sorry for the newb questions...

---

### Post by merlinus on 2007-06-24
Copy /alan to somewhere else, and add the line to fstab.  Also note my edited change to that line in my last post.

Then if need be you can copy it back as a subdirectory of /home.

If permissions are still a problem, that should be easy to fix.....

Reboot after editing /etc/fstab

-merlin

---

### Post by strange_cathect on 2007-06-24
Wait, guys, I just saw something interesting.

I used nautilus to look at what was in my Linux partition.  I have a strange problem with the existing /home folder.

Inside the folder it looks like this: 

> **/home/home_backup/alan.**

Would this be causing the problem?  I tried to take out /alan and restore the folder to this:
[B]> 
/home/alan[/B]

But it won't let me since I'm using the Live CD and don't have permissions.

Does this help?

---

### Post by strange_cathect on 2007-06-24
Also:

When issuing command: **sudo gedit fstab**

The file that comes up is blank.

---

### Post by merlinus on 2007-06-24
```

gksudo gedit /etc/fstab

```

And you will able to fix the /home issues afterwards.

-merlin

---

### Post by strange_cathect on 2007-06-24
Hi Merlin,

Thanks again.  Really nice of you to help me out here.

This is all that I have in the fstab file:

> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

Doesn't seem like very much here.

My old backup has this:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=47b643ca-6c0b-4805-a9b2-3034f19dacb2 /               ext3    rw,errors=remount-ro 0       1
# /dev/sda5
UUID=61b67e85-6700-4bcf-bfb6-241fcc3d6ce5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

So, I just probably replace the first fstab info with the second?  But then add the code:

> # /dev/sda4 /home ext3 defaults 0 0

to the end of the text?  Right?

Sorry, thanks again.

---

### Post by merlinus on 2007-06-24
Looks like the first /etc/fstab you posted is from the live cd, not from your hard drive.  Is that what you are running?

If so, you need to boot from your hard drive, and edit that /etc/fstab

Add the line but without the # in front:

/dev/sda4 /home ext3 defaults 0 0

and reboot.

-merlin

---

### Post by coldstatue on 2007-06-24
edit - addressed by the time I replied

---

### Post by strange_cathect on 2007-06-24
Hi,

I tried what we discussed but get an error message when I try to boot (from HD) that basically says it can't find /home.

I am unable to boot from the HD without the /home folder (which is why I'm using the Live CD to work on the problem).

Ideas?

---

### Post by merlinus on 2007-06-24
Complicated, eh?

Try this, from a terminal whilst booted from the live cd:

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab

```If the last command does not work, then:
```

sudo nano /media/ubuntu/etc/fstab

```nano is a text editor.

In either case, add the line:

/dev/sda4 /home ext3 defaults 0 0

to the end of the file.

Save, exit, and reboot, but this time from your hard drive.

-merlin

---

### Post by strange_cathect on 2007-06-24
Yes, very complicated.  I'll never try this again!  Thanks for being patient!

Got a problem:

> ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/ubuntu
mount: mount point /media/ubuntu does not exist


---

### Post by merlinus on 2007-06-24
Yeah, I made a mistake, which I just edited.  Re-read my last post with the new code.

-merlin

---

### Post by strange_cathect on 2007-06-24
Merlin! You beautiful wizard!  I'm back in!!!

Now all I have to do is figure out how to set the permissions in the new partition because all of my settings, email, bookmarks, are unreadable.

Do I:
> 
sudo chown -R username:username /home

---

### Post by merlinus on 2007-06-24
```

sudo chown -R username:username /home

```username is your login id.

-merlin

---

### Post by merlinus on 2007-06-24
BTW, I had to jump through all these hoops the first time.

But I learned so much in the process, and then made sure to create a /home partition whilst installing on my other two machines.

Next time you'll be able to help someone as well!

-merlin

---

### Post by strange_cathect on 2007-06-24
Merlin,

So far so good.  I'm back in and now I "own" these files.  However, firebird acts like I've never used it before.  As does my firefox bookmarks, music player, etc.  This worries me some.

Thanks for the encouragement.   I appreciate it.  You've been a great help.

---

### Post by merlinus on 2007-06-24
I believe all your settings are in your old /home/alan directory.  With Nautilus:

Ctrl-H to show hidden files.

Look for these:

.mozilla

firefox

xxxxxxxx.default

Copy that to your new /home/alan folder.

It has all your preferences, bookmarks, etc.

Then delete the profile that may have been created by default when starting up Firefox.

You can do the same for Thunderbird or any other program.

And it may simply be easier to copy the entire contents of the old /alan to the new one.

-merlin

---

### Post by strange_cathect on 2007-06-24
So that would be ok to just use Nautilus to drag it over and replace /alan with a new (backup) one?

And, for that matter, could you just back up your /home folder, install a fresh Ubuntu, and then replace the /home with your old backup? (not that I'm going to try any time soon!)

---

### Post by merlinus on 2007-06-24
Yes, you can simply drag all the contents of old /alan into the new /alan.  Make sure to have hidden files showing.

It is probably better to Select-All and then Paste-into-folder.  Tell it to overwrite existing files, if that error message appears.

The beauty of a separate /home partition is when reinstalling, or installing the next version, you simply "tell" the partitioner not to format /home, and all, or most, of your settings and preferences will remain intact.  No need to back it up.

-merlin

---

### Post by strange_cathect on 2007-06-24
Yes,  the beauty of the /home folder (and the headaches).

I've been a long, longtime user of Windows and mostly got interested in Linux.  But since starting Ubuntu about 3 months ago I've become a real Ubuntu zealot.  The promise of open source software is truly amazing.

I began to see the wisdom of a separate /home folder after spending a lot of time with Ubuntu.  And now I've got one, thanks to you.  I really appreciate your help (in the spirit of Ubuntu).

Take care, merlin.

---

### Post by strange_cathect on 2007-06-24
merlin,

Just to let you know: copying everything from /alan to /alan didn't work as planned.

I still can't resurrect my bookmarks or email settings.

And all my customizations evaporated.

Sigh.
_____________

---

### Post by merlinus on 2007-06-24
You may need to delete the new profiles so that Firefox and Thunderbird use the old ones.

Also, and forgive me for asking such a basic question, you did copy everything into /home/alan?

And when you look at its contents, do you see lots of folders whose names begin with a dot (.)?

Also, please post your current /etc/fstab

-merlin

---

### Post by coldstatue on 2007-06-25
> **merlinus said:**
> Try this:

```

sudo chown -R username:username /home

```(username is your username)


Does the new partition have to be logical, rather than primary? This command did not solve my problem, and I am wondering if it is the type of partition causing the problem. I had no problems on my desktop, using a logical partition, not even the permissions problem, but the laptop, using a primary partition, has permissions problems that were not fixed with your command.
Thanks for your help.

---

### Post by merlinus on 2007-06-25
I do not think the partition type matters.  

What are the current permissions?

There are other ways to change them.

-merlin

---

### Post by coldstatue on 2007-06-25
> **merlinus said:**
> I do not think the partition type matters.  

What are the current permissions?

There are other ways to change them.

-merlin

You want to know everything under Users and Groups for that person?

---

### Post by merlinus on 2007-06-25
Owner and access.
Group and access.
Others.

-merlin

---

### Post by coldstatue on 2007-06-25
Ok, well, for some reason, the laptop is set up by default so that the main user doesn't even have the users and groups option under Administration. i don't know why or how I set this one up to be so different than my desktop. (allow user to administer?) Ok, I log in as root to view it and get this. I assume you want "User Privileges"

for the owner, the following are NOT checked:
Administer the system
Allow use of fuse...
Send/recieve faxes
use tape drives.

The rest are checked.

Now for the group listed under the user's advanced tab is just the user's name, and if I got to manage groups, that group has no members checked. So, the user is basically part of no groups, but that's how my desktop is, and it's fine./ I am going to set the laptop user to administer the system, because that's how my desktop is, and I prefer it's behavior. Still, I think I tried that when trying to get the new home directory to work, and it didn't help. (I think)

---

### Post by merlinus on 2007-06-25
Let's back up a minute.

In Nautilus, right-click Home Folder, left-click Properties, and go to Permissions.

Write down what you see for:

Owner and Folder Access
Group  and Folder Access
Others and Folder Access

-merlin

---

### Post by coldstatue on 2007-06-25
I went back to using the home folder on the original partition. I'll do the process again and post back.
Thank you

---

### Post by coldstatue on 2007-06-25
ok, owner is correct user name
folder access - create and delete files

group (username - but remember the user is not actually checked under this group's properties.)
folder access - access files

others
access files

The most obvious problems I see off the bat are:

The NetworkManager applet could not find some required resources. It cannot continue.
I also get red exes over the logout button, the gnome menu, and the help icon.

My colors and icons are right thou8gh. Not when I open the entire computer though. Drives have paper icons now.
lots of missing icons on menus as well.

---

### Post by merlinus on 2007-06-25
Try adding the owner to the admin group, and see if any of the problems are resolved.

Also, if you like, we can check some of your configurations, etc.

```

sudo fdisk -l
blkid
cat etc/fstab
cat etc/mtab

```

-merlin

---

### Post by coldstatue on 2007-06-25
```
# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/sda2            3649        7296    29302560    5  Extended
/dev/sda3            1825        3648    14651280   83  Linux
/dev/sda5            3649        7052    27342598+  83  Linux
/dev/sda6   *        7053        7296     1959898+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

sda 1 is windows, 5 is ubuntu, and 3 is the new home partition

```
# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/sda2            3649        7296    29302560    5  Extended
/dev/sda3            1825        3648    14651280   83  Linux
/dev/sda5            3649        7052    27342598+  83  Linux
/dev/sda6   *        7053        7296     1959898+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

and something is wrong with the access fstab and mtab here, because i am looking at them in nautilus

```
# cat etc/fstab
cat: etc/fstab: No such file or directory

```

```
# cat etc/fstab
cat: etc/fstab: No such file or directory

```

Also, I know that the new partition is being mounted and treated as home, because going into my home folder, nautiuls reports 10.6 GB free,and if I go into say, boot, it reports 18.7

---

### Post by coldstatue on 2007-06-25
I already did add the owner to the admin group. I guess last night when I was working on this.

---

### Post by coldstatue on 2007-06-25
btw - logged in as root for those commands

---

### Post by coldstatue on 2007-06-25
fstab

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=5964bcc8-708c-44ef-9401-964302c90d66 / ext3 defaults,errors=remount-ro 0 1
# Entry for home partition
/dev/sda3 /home ext3 nodev,nosuid 0 2
# Entry for /dev/hda6 :
UUID=235d74be-6480-49dc-830b-8ee17f8bd55d none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/scd1 /media/floppy0 auto rw,user,noauto 0 0
#/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0
```


mtab

```
/dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda3 /home ext3 rw,nosuid,nodev 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk ntfs rw,nosuid,nodev,umask=222,utf8 0 0

```

---

### Post by coldstatue on 2007-06-25
what about the fstab entry? I see that someone else on this thread is using defaults, rather than nodev,nosuid

---

### Post by merlinus on 2007-06-25
FWIW, here is my fstab for /home:

# Entry for /dev/hda7 :
UUID=a961b624-ed15-4878-b66f-bb2d007b74a4 /home ext3 defaults,errors=remount-ro 0

and mtab:

/dev/sda7 /home ext3 rw,errors=remount-ro 0 0

What were the results of:

sudo fdisk -l

and

blkid

And did adding user to the admin group change anything?

-merlin

---

### Post by coldstatue on 2007-06-25
```
# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/sda2            3649        7296    29302560    5  Extended
/dev/sda3            1825        3648    14651280   83  Linux
/dev/sda5            3649        7052    27342598+  83  Linux
/dev/sda6   *        7053        7296     1959898+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

```
# blkid
/dev/sda1: TYPE="ntfs" 
/dev/sda5: UUID="5964bcc8-708c-44ef-9401-964302c90d66" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="235d74be-6480-49dc-830b-8ee17f8bd55d" TYPE="swap" 
/dev/sda3: UUID="31c78edb-d93e-4592-8102-9e49eef71ad0" SEC_TYPE="ext2" TYPE="ext3" 

```

honestly,im not too concerned if it works at this point. there is more space on my ubuntu partition anyway. at least i have a backup now

---

### Post by merlinus on 2007-06-25
OK.  But you may wish to replace your /dev/sda3 line in /etc/fstab with the UUID from blkid.

# Entry for /dev/sda3 :
UUID=1c78edb-d93e-4592-8102-9e49eef71ad0 /home ext3 defaults,errors=remount-ro 0

Good luck!

-merlin

---

### Post by coldstatue on 2007-06-25
ok, I will give it one more shot in the next few days. Thanks for all your help. It is greatly appreciated. I wouldn't be using linux without people like you. It's been my only OS for 2 months now. 
Cheers

---

### Post by coldstatue on 2007-06-26
Alas, it didn't work, but that's ok. For the laptop, I will be trying some automated backup scripts, and for the desktop, I think I may be heading for dedicated partitions for /etc and /usr/local, and maybe some others... once i learn which ones should have their own partition. I am so excited to have a system that doesn't need a complete reformat and fresh install (with no real backup but important files on cd) that I want to do everything I can to prepare.Thanks again. You are a big help. Open source spirit! I need to make a cheer.

---

