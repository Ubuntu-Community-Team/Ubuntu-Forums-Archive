---
title: "Windows XP + Ubuntu"
date: 2007-03-07
forum: General Help
---

### Post by KeReMiD4O on 2007-03-07
Hello from Bulgaria!

I don't know where else to ask and i would appreciate if u help me...
I'm sorry if this isn't the place for this post

I was thinking in installing winXP with ubuntu but i didn't install two OS's on a pc before...
And i was wondering could anyone describe to me the installation process and hopefully i do it right...

Now i have one hard disk (80gb) which is on two partitions C and D. C is 20 gb and D is 60 gb.
I have allready installed XP (on C) and i want to install Ubuntu if its possible without having to delete any info on my hard disks or if thats not possible i could delete some of it to free some space for the partition which Ubuntu will be on.

Um, if u can help me please do :)

Thank you for the time u took to read my post!

---

### Post by ubuntu27 on 2007-03-07
What do you have on your D partition?  Is it blanc (empty) or does it have any data such as a backup of C ?

---

### Post by KeReMiD4O on 2007-03-07
Oops i didn't mention it.  Um my stuff are on D and its pretty much to write it to disk's.

U have em to on u'r pc :)

---

### Post by kanha on 2007-03-07
look if you can find only 5 gb space on c drive or d drive,it will do the work.make a partition in windows of 5 gb and delete it (so effectively u will have 5gb empty space on ur hdd).
insert ubuntu live cd and click install on desktop.during 4th or 5th step it will ask about hdd then go for manually partition. use around 1 gb space as swap and 4 gb as /
i mean make two partition and mount one as swap and other as / from that empty 5 gb space.then proceed. In less than 20 minutes you will be dual booting devilxp+ubuntu
:popcorn: 
any problem ask here.also if it is your first time.back up important data,so if you do something wrong.................

---

### Post by KeReMiD4O on 2007-03-07
Um i have 20 gb C and free about 6 gb so i create a 3rd partition and i have C D & X for example.
Now i install ubuntu on the new one or do i have to uninstall (format) the C drive and install it on it?

P.S.
[Edit]
Um do i delete the install of winxp or it stays intact?
[/Edit]

---

### Post by mrmonday on 2007-03-07
If you have C, D, and X as your partitions - C as windows, D as your stuff, and an empty X you can put Ubuntu on X without affecting C or D, you can access these from Ubuntu if you would like :) If you use the Ubuntu installer to partition your disc, make sure that you do it properly (I messed up...) I think the easiest way for you to do this is just to put the disc in and see how it goes. If you don't understand something, ask us (if you can access the internet in Ubuntu), if not just reboot. 

Good luck:D

---

### Post by KeReMiD4O on 2007-03-07
Thank you guys :) I'll try that in a couple of days because i have a lot of work.

The nexct time i write here will be from Ubuntu :)
Thank u again! :)

---

### Post by ubuntu27 on 2007-03-08
> **KeReMiD4O said:**
> Thank you guys :) I'll try that in a couple of days because i have a lot of work.

The nexct time i write here will be from Ubuntu :)
Thank u again! :)

Good! Good luck KeReMiD4O :)

I recommend you to Refragment your harddrive before you partition or install Ubuntu.

In Windows:

Start Menu/(all) Programs/Accessories/Systems Tools/Disk Defragmenter



Here is a excellent[ Ubuntu Gude]("http://www.psychocats.net/ubuntu/index.php"):

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[Plan Partitions]("http://www.psychocats.net/ubuntu/installing")

[How to Install Ubuntu using the Desktop CD (Live CD)]("http://www.psychocats.net/ubuntu/installing")

[How to Install Ubuntu using the Alternate CD (Graphical Text Mode)]("http://users.bigpond.net.au/hermanzone/")

---

### Post by KeReMiD4O on 2007-03-10
Done!
Thank you again for the help.
But i did something not right :D i messed up C and deleted everything :)))
And i accidently made 4 partitions...
2 for ubuntu and C & D for win xp...
I't was hard work for me to find out how to set up my network... 
But, I did it :)
I so like Ubuntu now i'm going to learn it :D
Um i just can't get valknut running...
A friend told me i should write in the terminal:
sudo apt-get install valknut
and it doesn't work...
I'll edit my post to show u what it shows me...
Also i can't copy anythingin my hard disk's :-\
Bye for now.
And thanks again for the help.
U guys are so helpful :))

---

### Post by kanha on 2007-03-10
instead of valknut install linuxdcpp.it works better than valknut,howto can be found on forum,try searching.
regarding hdd,I think you do not have write permission....plz post output of
sudo nano /etc/fstab

best of luck

---

### Post by strabes on 2007-03-10
Windows likes to be installed on the first partition on your hard drive by the way. You should set it up like this:

15GB - Windows
15GB - Ubuntu
2GB - Swap
Rest of hard drive - shared fat32 data partition

It is much easier if you install windows first and then ubuntu after.

---

### Post by KeReMiD4O on 2007-03-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I don't understand it :) And have no clue why u need this... 
And yes i noticed that my C & D are nor writable. How can i change this?
:)

---

### Post by kanha on 2007-03-12
> **KeReMiD4O said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I don't understand it :) And have no clue why u need this... 
And yes i noticed that my C & D are nor writable. How can i change this?
:)

sudo apt-get install ntfs-3g

this will install ntfs read and write access to your system,then
follow this
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

when rewriting your fstab file, replace /dev/hda1 to hda2,hda5 in respective lines
:guitar:

---

### Post by KeReMiD4O on 2007-03-12
10q problem solved ;)
Much thanks!!!

---

