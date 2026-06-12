---
title: "Directories in Kubuntu"
date: 2016-02-05
forum: General Help
---

### Post by incurablegeek on 2016-02-05
Briefly, I develop educational materials - multiple levels and multiple iterations on each level. All of these files represent about 20K hours of computer work, so there are indeed many.

Naturally I must be able to access them immediately as I can in Windows.

Now I partitioned and formatted my 2 X 3TB hdd's with Gparted in Ext 4. All totaled I have 60 TB on 6 computers.

Also I have been reading so long that I believe my brain is beginning to leak out my ears. From that reading I have learned much, specifically that there are a myriad of file managers out there. 

Which one and, how, can I create directories and many, many subdirectories in tree format? I must have these directories in visual format for the obvious reason that I have many, many thousands of files to which I must have access. 

Therefore doing everything in Sudo would not be at all appealing. Actually it would be impossible.

Suggestions, anyone?

..............

Point of fact: I have encountered "trolls" before and tolerated their verbal abuse without retaliation. I shall do so no more. This is a classy forum with tons of really knowledgeable people. I do hope that we will all mind our manners and remember the promise we agreed to upon signup. I know that I will.

---

### Post by bab1 on 2016-02-05
> **incurablegeek said:**
> Briefly, I develop educational materials - multiple levels and multiple iterations on each level. All of these files represent about 20K hours of computer work, so there are indeed many.

Naturally I must be able to access them immediately as I can in Windows.

Now I partitioned and formatted my 2 X 3TB hdd's with Gparted in Ext 4. All totaled I have 60 TB on 6 computers.

Also I have been reading so long that I believe my brain is beginning to leak out my ears. From that reading I have learned much, specifically that there are a myriad of file managers out there. 

Which one and, how, can I create directories and many, many subdirectories in tree format? I must have these directories in visual format for the obvious reason that I have many, many thousands of files to which I must have access. 

Therefore doing everything in Sudo would not be at all appealing. Actually it would be impossible.

Suggestions, anyone?

..............

Point of fact: I have encountered "trolls" before and tolerated their verbal abuse without retaliation. I shall do so no more. This is a classy forum with tons of really knowledgeable people. I do hope that we will all mind our manners and remember the promise we agreed to upon signup. I know that I will.You don't need to use sudo to make all the directories you need as long as you make the directories in your home directory or change the ownership of the section of the file system you want to use (e.g. /srv or /data or ...).

---

### Post by grahammechanical on 2016-02-05
You may find that you cannot create folders on other partitions. But we can do that if we load the File Manager with administrator privileges.

This will work for Ubuntu

```
sudo -H nautilus
```

I am not sure what will work for Kubuntu. Possibly

```
sudo -H dolphin
```

Perhaps someone else can confirm.

Now we can create folders but they will be owned by root. So, we select the folder & right click and select Properties>Permissions and we will see that the owner is root with access to create and delete files. And also that Group is root with access to create and delete files.

Now we need to give that same level of access to Others from a drop down menu as Others will only have authority to access and not create & delete files/folders.

You will also see a panel that will let you change permissions for enclosed files. That is useful if there are files already existing in the folder that we created when working as root.

After doing this you can create a folder within the first folder & copy files to and from the folder and folders in the folder. You can also create files and delete files when working as a standard user.

This method is only necessary when needing to store files on other partitions whether on the same disk drive or another disk drive. I base this information on the working of nautilus. A similar method must also apply to Dolphin but as I do not use it I cannot be accurate in my descriptions.

Regards

---

### Post by Bucky Ball on 2016-02-06
If you're using Ubuntu you have Nautilus file manager. Open it and start creating folders where ever you want. What seems to be the actual issue? Once the partitions are mountable (and we can help you auto-mount them at boot if you like) then you can do what you like, create/delete partitions, move files, whatever - same as you can in Windows. No need for opening Nautilus as root and then changing permissions back again or using a terminal to 'sudo' create every directory. Not sure why you would want to create the directories as root in the first place. 

If this is hypothetical I advise that, rather than read til your brain leaks out your ear and try to imagine how it works, you download the Ubuntu ISO (or Kubuntu), create bootable media from it, boot the media and when you get to the options choose 'Try Ubuntu'. That will take you to a desktop in a 'live' session which is running from the install media. This does not change anything on your hard drive or install anything on hard drive (unless you mount a hard drive and change something manually that is). 

Open the file manager and create a folder. It's that easy. As you are running a live session your partitions may not be automounted and whatever you do in there will be lost on reboot, but if you put a USB stick in that should automount and you can create a folder on that in a file manager. 

Bottom line: You don't need sudo/terminal anything to create folders and you also don't need to launch the file manager as root. You only need the partitions to be mounting with the correct permissions and that is that.

(PS: I don't use Nautilus myself, but think it gives you the option of viewing files/folders in tree or 'places'. You'll see the difference when you get there. Should be under 'View> Side pane> Directory Tree' or something like that (I'm using the lightweight pcmanfm so bit different).)

(PPS: Not sure Kubuntu uses Nautilus as default file manager, think it's Dolphin, but makes no difference. They're all pretty similar. Some are heavy, some are light is main difference really.)

---

### Post by incurablegeek on 2016-02-06
Thank you so much, all of you, for your thoughtful and well-articulated responses.

I gave myself until Friday (yesterday) to master Kubuntu and get on with my work. Not exactly working out as I planned. But then I should think back over the 25 years that I used DOS and Windows to those times when I felt helpless there as well.

I copied and am going through all your comments, so that I can make a literate response. 

I sure do hope I do not wear out my welcome on this forum by asking such silly questions. For what it's worth I do my best not to ask a question until I have gone through everything on the net and in the Kubuntu manual - and then am even more confused than ever. If I am anything, though, it is persistent - and I am now completely committed to Linux.

[CENTER]***[SIZE=3]I have seen the light!  :popcorn:[/SIZE]***
[/CENTER]

---

### Post by Bucky Ball on 2016-02-06
> **incurablegeek said:**
> I should think back over the 25 years that I used DOS and Windows to those times when I felt helpless there as well.

Good pick-up, nice insight. Indeed you should. This is a very valid point people seem to completely overlook. I have trouble using a Mac! I use Xubuntu, very minimal spin of that, so I find Windows too busy, even with nothing much installed manually.

The thing to remember is go in chunks of a feasible and achievable size with a realistic timeframe. Master Kubuntu by Friday? Sheesh, I been here eight years and nowhere near there. Mind you, that's not what I was ever going for. I was going for a fast, efficient, productive system that wouldn't crash every five minutes and I could customise.

I only needed to know how to do certain essential things to start. You probably do to. Helps if you have a goal. What do you need to do on the machine most that you don't know how to do now? Go for that and in the process you'll learn more about Kubuntu. 

Knowing all there is about Kubuntu doesn't achieve much. Knowing how to make it do what you need it to and what apps suit you best is more productive, and remember, 'Kubuntu' is just a pretty wrapper around Ubuntu. ;)

---

### Post by incurablegeek on 2016-02-06
@Bucky Ball

Quite true. That's actually what I meant - but said very clumsily.  ](*,)

Really all I need to do right now is:

[B]1) Pull all my work files (mostly Word .doc files) off of my main work computers
2) Organize them in Decision Trees (with lots of subdirectories) in Kubuntu - That, my friend, is Job 1[/B]
3) Open these .doc files into Libre Word and save them as Libre Open Document Text (yes, I do know that Linux does not have file extensions)
4) Work on these files in Libre

Why Kubuntu and Libre? My associates in India use Fedora and absolutely *[COLOR=#ff0000]**hate**[/COLOR]* (not a strong enough word) MS Word. Quite frankly, I do as well. Give me Word '97 any day. And as for an OS, Microsoft was at its best with NT 4.0, which ran quite happily on 64 Meg of RAM. Now my Win 7 computers all have 16 Gig. So I absolutely agree: Windows and all its Programs have become bloated, buggy and even more difficult to use.

Again, ***Oh Captain, My Captain*** (paying homage to your Forum Moderator position), you and so many Ubuntu users in this forum have really gone out of your way to help me. 

A bit of a sidelight: Every time I think that (rightfully so) educational systems all over the world are failing, I read the very precise wording of the posters on these forums. 
It brightens my day.  :guitar:

---

### Post by oldfred on 2016-02-06
It sounds like a ownership & permission issue. You should not need sudo for your data.

With Windows that normally is not an issue, but with multi-user systems it is important. And it helps keep Linux more secure as you must have ownership & permission to use a file or folder or even execute a file.

I like to use data partitions and mount at /mnt/data. But that mount point is inside / (root) and root defaults to ownership. Normally you do not change ownership nor permissions of system partitions or files as that can lead to total system corruption. But you can change your own data.

I typically manually mount my data partition once, to set ownership and permissions. But then add to fstab as default mount.

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

Use of -R or recursion can be dangerous. If used just on your data partition it is ok, but never on a system partition. In fact you should never change any ownership nor permissions of system folders or files.

I use the same permissions and ownership as /home which is a bit on the permissive side.
      
 Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by incurablegeek on 2016-02-06
@Oldfred

I think it's time for me to just the heck up and go back to reading - and also "playing with" Kubuntu.

As Bucky Ball said quite accurately, I am trying to build Rome in a day. To be perfectly honest, I have never been a big fan of reading manuals, but in this case I believe I must. 
Windows and Linux have about as much in common as Mars and the Moon. 

All in all, by just flailing around here in the dark the past couple of days, I am actually getting familiar with Kubuntu. 

And I promise you: I am not going back to Windows! My ancestry is German; and we are a stubborn people. 
As my Mama always liked to say, "You can always tell a German. You just can't tell him much."

I really think I should mark this thread "solved", because there certainly is enough information in it to get even complete idiot like me started down the right road.  #-o

@Bab 1

 > You don't need to use sudo to make all the directories you need as long  as you make the directories in your home directory or change the  ownership of the section of the file system you want to use (e.g. /srv  or /data or ...).

For me it must be take ownership of the _**entire partition**_, so that I can move files from Windows into it.
Putting all the folders in the Home Directory would be completely untenable - visual overload and a sorting/locating nightmare

Now here comes a really silly one: If I move an entire partition in Windows to a Folder in a partition on my hdd, will the complete Windows Tree Structure remain intact. (say yes and I'll buy you a beer)

................
@Bucky Ball

> Open the file manager and create a folder. It's that easy. As you are  running a live session your partitions may not be automounted and  whatever you do in there will be lost on reboot, but if you put a USB  stick in that should automount and you can create a folder on that in a  file manager. 


When I click on "Properties" (in Dolphin) and go to "Permissions", I am told "Only the owner can change permissions".

Kind of a road block.

...............
@old fred

> It sounds like a ownership & permission issue. You should not need sudo for your data.

100% correct. I will follow the links you gave me and see if they help. Thanks.

---

### Post by deadflowr on 2016-02-06
For what it is worth:
In KDE or Kubuntu you can invoke KDE's graphical sudo by running* kdesudo <program-name>*

I haven't used Kubuntu 15.10 extensively, but kde has had a basic command runner called krunner.
Simply press alt + F2 to start krunner, and then type;
```
kdesudo dolphin
```
It'll ask for a password, and then open start dolphin as root.

Normal Ubuntu has the same basic function, but they call it something like run dialog, and you would use gksu instead of kdesudo.

Again, a for what it is worth.

---

### Post by oldfred on 2016-02-06
You should be able to copy folders, but I would not select too much at one time. It can be slow copying from NTFS as Linux had to reverse engineer the NTFS driver. It is reliable, but not as fast in some cases as a native Windows driver. But you cannot use Windows to copy to a Linux formatted partition.

I copy photos from camera & iphone. But do not like any of the auto photo organizers. So I just use Nautilus to copy them. With camera I mount card in a card reader. My folder struture is each year, then quarters or major events, just so I do not get too many in one folder.

But I regularly copy entire folder structure using rsync from desktop to laptop & to flash drives.
In each case I have used my commands posted above to make sure I have ownership & permissions. Sometimes after a copy I have to redo something as sometimes some files, perhaps from downloads? do not end up with correct settings. Or it could be some program running as root, but saving in /home has not saved with correct settings. I turn on display in Nautilus so I can see who & what settings are on each file & folder.

---

### Post by incurablegeek on 2016-02-06
> for what it is worth

It's worth quite a lot. Thanks.

---

### Post by bab1 on 2016-02-06
> **incurablegeek said:**
> @Bab 1
```
You don't need to use sudo to make all the directories you need as long as you make the directories in your home directory or change the ownership of the section of the file system you want to use (e.g. /srv or /data or ...). 
```

 

For me it must be take ownership of the _**entire partition**_, so that I can move files from Windows into it.
Putting all the folders in the Home Directory would be completely untenable - visual overload and a sorting/locating nightmare

Now here comes a really silly one: If I move an entire partition in Windows to a Folder in a partition on my hdd, will the complete Windows Tree Structure remain intact. (say yes and I'll buy you a beer)

Yes.  Unfortunately, I don't drink beer.  If you want, you can have a beer instead.  ;-)

From a Linux point of view (Kubuntu after all is just a distro of Linux) you don't mount physical devices (hdd or ssd, etc.), nor do you mount partitions (sda1 or sda2 or sdb1, etc).  What does happen is that the file system on one partition is mounted (attached) to the local (root) file system.  Of course a file system must reside on a partition and the partition is created on the physical device.  This is the same whether you use Linux or Microsoft.  The names change but the concept is exactly the same.

If you had a HDD that had a partition that was formated NTFS and you wanted to mount that file system to to your Kubuntu local file system you could do that easily.  Once that was done you could view it in the folder you mounted the NTFS partition at (e.g. at /mnt/myNTFS).  I had to do this the other day.  I transfered about 35GB of to another partition that was formatted as ext4 (e.g. at /mnt/myNewExt4).

From a partitions point of view it looks like this```

/dev/sda1        19G   /
/dev/sda3        96G   /home
/dev/sdb1       500G  /mnt/myNTFS       <---NTFS formatted partition  (on a 2nd separate HDD)
/dev/sdc1        750   /mnt/myNewExt4   <-- ext4 formatted partition   (on a 3rd separate HDD)

```   
The above has 3 physical drives.  The root HDD is a SSD with 2 partitions (/ and /home).

Once you embrace the Linux way of managing you data the task is really very easy.  I would be happy to show you the steps.  If you have a couple of external devices (USB sticks or HDD or SSD) we can practice with trivial data.

This is best done done from the command line.  Once it is all set up you can manage the new data from the GUI file manager.  

FYI - There is a difference between "copying data" and "cut and paste data" and "creating new data".  Understanding this aspect will save you hours of frustration trying to resolve ownership and permissions issues with the subdirectories and files.  It is well worth you time to completely understand ownership and permissions used with native Linux file systems.

Let us know if you want to experiment with this.

---

### Post by Bucky Ball on 2016-02-06
Here's something. Yes, it does sound like permissions, but not the files, the partition and I think that's where the confusion is coming in.

Say your partition is mounted at /media/user/Data and you can't put files or folders in it nor create a file or folder in it. Open a terminal and:

> sudo chown -R username:username /media/user/Data

... replacing 'username' with your username. The folder being 'chowned' in the example should be changed to the correct mountpoint for the one you're attemting to 'chown'. For instance, if your username on your machine is the same as the one you use here. then:

> sudo chown -R incurablegeek:incurablegeek /media/incurablegeek/YourDataPartition

Again, correct the mountpoint you are 'chowning'. Now try ...

---

### Post by SeijiSensei on 2016-02-06
If you already have the files you need on an NTFS-formatted device, I wouldn't bother with copying anything.  You can just mount that device in Linux and read and write to it from there.  Writing to NTFS from Linux used to be dicey, but the [current driver]("http://www.tuxera.com/community/open-source-ntfs-3g/") is quite reliable.  If you do want to copy the files to Kubuntu, you can mount the NTFS device, then drag-and-drop the appropriate directories from that drive to the Linux destination using Dolphin.

My NTFS-formatted partition is automatically mounted at boot via a line in the file /etc/fstab that reads like this:
```
UUID=D054464154462A94 /media/BigNTFS  ntfs    defaults,umask=007,gid=46 0 0
```
That mounts the partition with the specified "UUID" at the "mount point" /media/BigNTFS. A mount point is simply an empty directory where the file system on the mounted device will be attached to the Linux filesystem.The "ntfs" designates the type of file system, and the set of options that follow determine access privileges to the file system's content.  I'll come back to that later on. The final two zeroes relate to an ancient backup program called "dump."  You can read about their purpose in the "manual page" for /etc/fstab by issuing the command "man fstab".*  

Now before I can mount the device, I have to create the mount point called /media/BigNTFS.  Every system comes with /media by default these days.  To create a mount point I just use the mkdir ("make directory") command:
```
sudo mkdir /media/BigNTFS
```
I've prepended an extra command, "sudo." That command tells the operating system that everything following it constitutes a command that you want to execute with "root" or administrative privileges.  The first time you run sudo you'll be prompted for your login password.  After that you'll have root privileges for a while until they expire when you'll be prompted for your password once again.

I need to have root privileges because ordinary users by default can only write to a small portion of the Linux filesystem, basically their home directories and /tmp.  Pretty much everything else is owned by the "root" user.  So in order to make a directory under /media, I must become the root user with sudo.  Also this directory will be owned initially by the root user, though we'll see in a moment how that becomes modified.

Now, going back to the /etc/fstab entry, the first item identifies the partition to be mounted.  Linux used to rely on "device" designations like /dev/sda1, which is the first partition (1) on the first hard disk (a).  Now best practice is to use the partition's UUID, a fixed identifier that won't change even if other drives are added to the machine.  So in order to create the /etc/fstab entry, I need to list the partitions on my drives with this terminal command
```
sudo blkid
```
It returns a list of partitions with their labels, UUIDs, and file system types.  Here's the corresponding record to the entry in /etc/fstab above:
```
/dev/sdb2: LABEL="BigNTFS" UUID="D054464154462A94" TYPE="ntfs" 
```
Here you can see the traditional device identifier, /dev/sdb2, meaning its the second partition (2) on the second hard drive (b).  (The "sd" used to mean "SCSI drive," but it has now been extended to all types of drives including SATA and USB devices.).  The partition is labelled "BigNTFS" with the UUID as specified, and a partition type of ntfs.  I used the UUID in /etc/fstab to identify the partition I want mounted.

Once the file system is mounted at /media/BigNTFS, you can navigate through it just as you would any other directory tree.  If it's the primary Windows filesystem, you'll see directories like Users which in Windows appears as "C:\Users".  If all your files and documents are on the mounted drive, you'll be able to access them from Dolphin just as you would from Windows Explorer.  If you want, you can copy them all to Linux by dragging-and-dropping the top of your documents directory from the NTFS device to some place in the Linux filesystem.  The entire structure will be copied intact.  Dolphin has a nice "Split" option that lets you split the directory window so you can have one half open to the source and the other half open to the target.

Now lets talk finally about permissions.  Unix has three types of permissions -- read, write, and execute -- and three groups with access rights -- users, group members, and everyone.  Because the BigNTFS file system is mounted using /etc/fstab, by default it is owned by root.  This would be a problem since no ordinary users could then write files there.  Ubuntu avoids this by assigning a pre-determined group called "plugdev" to the mounted filesystem and giving that group full access.  My user was assigned to the plugdev group when I installed Kubuntu.

In the file /etc/group, there is an entry the defines the plugdev group:
```
plugdev:x:46:seiji
```
It has group ID 46 with user "seiji" as an additional member.  Those options in /etc/fstab, "umask=007,gid=46," grant full read, write and execute privileges to the filesystem's owner, root, and to members of group 46.  No privileges are granted to any other users.

A directory listing shows 
```
$ ls -l /media/
total 16
drwxrwx---   1 root plugdev 4096 Feb  5 13:24 BigNTFS

```
which says that user root and group plugdev have full access rights ("rwx"), while everyone else has no rights ("---").  If more than one person has a login account on this computer, she can only access the files on this device if you add her to the plugdev group:
```
sudo adduser username plugdev
```.

I hope this hasn't been too detailed.  I tried to give you an overview about how Linux treats NTFS resources.  If you have questions, as I'm sure you will, please ask!  I doubt I've been transparently clear throughout this posting!


[size=1]*There are "man" pages for every command and many standard configuration files as well.  The man pages all read like they were written by computer nerds, which they were, so they can be a bit daunting at first.  Nevertheless they are the basic source of the documentation for the entire operating system.  Once you've gotten used to the style and organization you'll begin to see how useful they are.[/size]

---

### Post by bab1 on 2016-02-06
> **Bucky Ball said:**
> Here's something. Yes, it does sound like permissions, but not the files, the partition and I think that's where the confusion is coming in.

Say your partition is mounted at /media/user/Data and you can't put files or folders in it nor create a file or folder in it. Open a terminal and:



... replacing 'username' with your username. The folder being 'chowned' in the example should be changed to the correct mountpoint for the one you're attemting to 'chown'. For instance, if your username on your machine is the same as the one you use here. then:



Again, correct the mountpoint you are 'chowning'. Now try ...
This is not always true.  If you assume that the file system format is ext then it will work.  If it is NTFS the ownership of the file system is set at mount time.  In any event you mount file systems on partitions to a mount point in the local (e.g. root) file system.

---

### Post by Geoffrey_Arndt on 2016-02-07
Just some excellent posts in this thread by bab1, Bucky and SeijiSensei . . . have copied certain portions to my ZimWiki database on Linux HowTo's.    It seems the /etc fstab procedures have changed somewhat since I last used them to any degree (my Xandros days).

A question though . . . why wouldn't the /home directory be the easiest and most convenient way or place to transfer sections or all of the Windows NTFS file tree to . . . what would make it a bad target?   Maybe I don't understand, but what are the downsides to that?   Dennis wouldn't have to worry about permissions at all, as he would be the owner of each directory, and it's nested folders and files.   It wouldn't clutter or interfere with other /home top level directories (as each 1st level folder is the start of another valid, independent tree)?? 

Oh, and congrats to (IG) on his 3 year milestone (Feb 20'13) in Ubuntu forums . . . . way to stick with it!! \\:D/   Perseverance is rewarded!

Geoffrey

---

### Post by bab1 on 2016-02-07
> **Geoffrey_Arndt said:**
>  . . . why wouldn't the /home directory be the easiest and most convenient way or place to transfer sections or all of the Windows NTFS file tree to . . . what would make it a bad target?   Maybe I don't understand, but what are the downsides to that?  

Dennis wouldn't have to worry about permissions at all, as he would be the owner of each directory, and it's nested folders and files.  
It wouldn't clutter or interfere with other /home top level directories (as each 1st level folder is the start of another valid, independent tree)?? 
The only downside is managing multiple user access in a single users private section of the file system.  In a multi user environment you traditionally want to place a file system tree that is intended for multiple users outside of the /home branch.  It makes it much simpler to maintain user access controls (ownership and permissions.  

If the OP is the only user then it would be perfectly fine to just make a mount point inside his home directory and mount the NTFS formatted partition there (e.g. /home/<user>/NTFS_Partition or some such) the only additional thing you would see in the users home directory is a folder named NTFS_Partition.  Everything would be below that point.

Bottom line: it's all about user permissions and ownership + neatness.

---

### Post by Geoffrey_Arndt on 2016-02-07
Thanks bab1 . . . it's been a while since I've been on a networked or multi-user system . . . between my private /home directory and dropbox, I'm getting used to a simpler way to work.   Ain't syncing awesome!!:D

---

### Post by bab1 on 2016-02-07
> **Geoffrey_Arndt said:**
> Thanks bab1 . . . it's been a while since I've been on a networked or multi-user system . . . between my private /home directory and dropbox, I'm getting used to a simpler way to work.   Ain't syncing awesome!!:D
I run servers for multiple users so I normally keep all data at /srv/<some-dir> that multiple users gain access to.  I am the network dropbox.  ;-)

[COLOR="#0000FF"]Edit: If you use Linux and are attached to the Internet you are using a networked + multi-user system.  You're just not using all of the capabilities available.[/COLOR]

---

### Post by incurablegeek on 2016-02-07
@[**[COLOR=#000000]Geoffrey_Arndt[/COLOR]**]("http://ubuntuforums.org/member.php?u=1973436")

Two things:

1)> Oh, and congrats to (IG) on his 3 year milestone (Feb 20'13) in Ubuntu forums . . . . way to stick with it!! [IMG]file:///C:\Users\Laptop\AppData\Local\Temp\msohtmlclip1\01\clip_image001.gif[/IMG]Perseverance is rewarded!

I feel that I must be honest. Until now I have only been a window shopper. Now I am maniacally serious. Quite a difference actually.

2) > Just some excellent posts in this thread by bab1, Bucky and SeijiSensei . . . have copied certain portions to my ZimWiki database on Linux HowTo's. It seems the /etc fstab procedures have changed somewhat since I last used them to any degree (my Xandros days).

I wholehearted agree. There is some serious knowledge on this forum. It should not go to waste but rather be organized by subject into a helpful manual or wiki.

Quite frankly, you guys scare me with your knowledge, yet honor me by your acceptance of me and toleration of my silly "from Windows to Ubuntu" questions.  :D

---

### Post by Geoffrey_Arndt on 2016-02-07
IG:    

"Until now I have only been a window shopper" . . . nice play on words . . . ;)

But seriously, two points:

>   Did you note the response about putting data within /home . . . for the single user PC??   The top-level of directories in /home would have only 1 additional folder, and everything nested inside that . . _much simplifies life_.

>   To this point, have you actually installed any form of Linux to your PC's?   Live media doesn't really count . . . but any actual full installs?   Using what flavors of Linux?

IF you haven't and it sounds like it . . . then that would certainly explain why you seem to be running in *perpetual circles of confusion and frustration*.     The whole install process can have it's challenges, so, that may result in some very interesting future threads . . . 

Geoffrey

---

### Post by Bucky Ball on 2016-02-07
Indeed. Install or have a look at a live session so you can answer some of your questions and bounce the remaining ones off the forum. ;)

---

### Post by incurablegeek on 2016-02-07
> But seriously, two points:

>   Did you note the response about putting data within /home . . .  for the single user PC??   The top-level of directories in /home would  have only 1 additional folder, and everything nested inside that . . _much simplifies life_.

>   To this point, have you actually installed any form of Linux to  your PC's?   Live media doesn't really count . . . but any actual full  installs?   Using what flavors of Linux?

IF you haven't and it sounds like it . . . then that would certainly explain why you seem to be running in *perpetual circles of confusion and frustration*.     The whole install process can have it's challenges, so, that may result in some very interesting future threads . . . 

In response to your questions:

1) > have you actually installed any form of Linux to  your PC's? 
Yes, 4 times actually: BSD on my pfSense router/firewall box, Ubuntu 12, Ubuntu 14, and now Kubuntu 14. I currently have Kubuntu running on the computer next to me and have been playing with it.

2) > Did you note the response about putting data within /home . . .  for the single user PC??
Therein, I believe, lies my confusion. Still thinking from a Windows point of view, that sounds so much like MS trying to convince users to put everything in "Libraries".

Again, perhaps not understanding your suggestion, I like multiple partitions on all my hdd's. My Windows "Work" computer, which I will migrate to Kubuntu, has 8 hard drives and an SSD. It would seem to me then that loading everything in one place, e.g. "home", would only lead to a lot of looking before actually finding anything. With partitions, all neatly labeled, I can find things quickly.

One thing I seriously like about Ubuntu is I can read everyone of my Windows computers - partitions and directories, because Ubuntu can read NTFS. What I found shocking is that I have the (unsavory) options in Kubuntu of formatting my hard drives in NTFS.  

So at this point I can read and even open files on my Windows computers from Kubuntu - but cannot move those files into the 2 partitions I created (so far) on one of my 3TB drives in Kubuntu.

---

### Post by bab1 on 2016-02-07
> **incurablegeek said:**
> ...
Again, perhaps not understanding your suggestion, I like multiple partitions on all my hdd's. My Windows "Work" computer, which I will migrate to Kubuntu, has 8 hard drives and an SSD. 

In Linux "partitions" do not equate to drives.  In any event all partitions mount to a single file system that starts at /.  This is also true of Windows except it is hidden from the user.  A "drive" in Windows is equivalent to mounted file system branch in Linux.  The mountpoint folder name (directory) is the distinction (drive name).  It is entirely possible to replicate your current Windows file structure (data) using Linux.  What it looks like visually may be different.  Windows speak is not the same as Linux speak.  Using Windows terms when talking about Linux structure is also confusing the issues.   
> 
It would seem to me then that loading everything in one place, e.g. "home", would only lead to a lot of looking before actually finding anything. With partitions, all neatly labeled, I can find things quickly.

This is just another example of using previous Windows experience clouding the Linux discussion.  Lay out how your data is structured using Windows and we can provide you with a similar structure using Linux. 
> 
So at this point I can read and even open files on my Windows computers from Kubuntu - but cannot move those files into the 2 partitions I created (so far) on one of my 3TB drives in Kubuntu.
This has been touched upon earlier.  You have not responded with questions as to "how do I do that".  

At this point we have pretty much talked the subject to death.  It's time to do something.  What do you want to do?  Set up a structure to receive the data?  Or do you want to set the permissions on the 3TB partition (what you are calling a drive) so you can move the data (copy or cut and paste)?

---

### Post by incurablegeek on 2016-02-07
> It's time to do something.  What do you want to do?

I can feel your frustration with me. I must seem like a frog sunning himself on a lily pad.

Not exactly, what I want to do now is **drop out for a while and digest all the information** you folks have given me as well as what have copied off the net. I am just swimming in too much right now, such that I think it's important for me to learn the language, "Linux speak", if you will, so that I can communicate more efficiently.

Actually you folks are worse than me in your expectations. I tend to set seemingly unattainable goals and then work my behind off to attain them. As you know, I have only been in Linux a few days now. I was in DOS and every worthy iteration of Windows for 25 years. Huge difference.

I will now mark this thread as "solved" to take some pressure off of you kind-hearted people. And I will return only when my questions "make sense" in the Ubuntu world. And, heck no, I am not giving up. Perish the thought.

---

### Post by Geoffrey_Arndt on 2016-02-07
LG:

>   You have not been in Linux for days.   You've been using this forum under your current moniker for 3 YEARS . . . . yes, 3 years.  And who knows how long before that with another ID or at other Linux Forums?  

If I were in your place now, it would take me 15 to 20 minutes to test out a simple copy/paste migration from one of your NTFS directory branches into a top-level /home/NTFS branch.    Depending on the size (I would start small), the transfer would take anywhere from a couple minutes to maybe a half hour for a few gigabytes.   Once you do that, it should be a "piece of cake" to visualize the rest of the transfer process.

Another thing that would help is to for you to post a visual of your PC's file structure using Gparted or similar tools.   We can provide more step by step instructions then.   How in the world Dennis, are your Indian partners putting up with all this "Angst" , . . . ??  Many cities across the world have LUGS (Linux User Groups).   Maybe an IT intern or student at the local Uni?

Oh well, you can lead a horse to water, but . . .

---

### Post by Geoffrey_Arndt on 2016-02-07
Wow . . . there are issues here beyond the technical.    Mark me "Over & Out" . . .

---

### Post by incurablegeek on 2016-02-07
I just want all you guys to know that Geoffrey and I are all good. We have exchanged multiple PM's and now I understand what he was trying to do. He was trying to "motivate" me by making me angry. Well, he did indeed make me angry, but I never need external motivation. I am under a crushing schedule which is, quite frankly, motivation enough.

All my life I have been excellent at what I do, so it irks me that I am taking so much time to even be able to use Ubuntu in the most elementary of ways. As I mentioned before, however, I need to "drop out" for a while and just do some reading and digesting of the reading: Specifically all that you good people have shared with me plus the many pages I have downloaded, printed and copied from the Ubuntu site. I must also read the Kubuntu manual cover to cover.

Indeed, it is really hard, at least for me, to communicate my true self electronically. I do much better face to face, where there are more body language cues. 

As to what I am doing on the side? Well, a myriad of things, including being the Executor of our Estate - a thankless, extremely detailed but necessary responsibility, liquidating assets, counseling my colleagues on more effective marketing practices - not to mention, after having moved, unpacking, sorting and building a home. Also, because I am well-known in my field, I have much pressure on me to rethink what I have written in book form - actually many books in English and in Japanese, for use on hand-held devices. Hence, the on-going *angst*.

Anyway, thanks to all of you. When I return, I probably will be much more literate.

---

### Post by Bucky Ball on 2016-02-07
And with that,

*Thread closed.* 

If you have further support requests please post a new thread. Good luck.

---

