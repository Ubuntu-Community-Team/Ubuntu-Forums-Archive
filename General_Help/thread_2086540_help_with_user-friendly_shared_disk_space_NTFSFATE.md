---
title: "help with user-friendly shared disk space NTFS/FAT/EXT4"
date: 2012-11-21
forum: General Help
---

### Post by ex-oficio on 2012-11-21
Hi all.
 
For years I have had 3 partitions on my laptop:
 
/ : ext4 (was once ext3)
swap : swap
/mnt/Archive : fat32
 
This has worked like a charm for me and my good lady wife who also used the same laptop. In particular, this thread is about thew /mnt/Archive partition.
 
I originally had windows (Vista... ugh) as well, and at the time NTFS was a bit shaky in linux, hence I used fat32 as a go-between partition. I no longer have or use windows, but the partition is now a shared space for both users.
 
In essence I dont want to use a windows filesystem on there anymore, and especially not FAT32 as it is not very forgiving in the event of errors and it dopesnt support files bigger than 4gb, which the Mrs keeps forgetting...
 
We share it for things like downloads, music library, Photos etc. I categorically DO NOT want any permissions to deal with on this partition. Unix style pernissions work fabulously for the / partiton (and by extension, for our home directories), but are an irritation at best for this shared partition, where security is not required.
 
I have experimented with ext4, as this is what I have for the root partition, and it is notably faster than using fat32 or NTFS. However, mounting this with the same options as the / partition results in access problems between the two users (me and wife) on the system. If i create files and folders, she cant get into them and vice versa. I understand that there may be ways to deal with this using umasks, users, groups, etc but I am not sure how to. For me its just an annoyance as I have to keep recursively using chmod/chown as root to sort things out. For the wife its a deal breaker as she doesnt understand unix permissions, and in my view she shouldn't have to in this situation. 
 
We just want to use the drive as if it were a big usb flash drive, as we always have. Currently, I have the drive formatted as NTFS, as a compromise which gives better data integrity than fat32, but avoids the file/folder permissions/ownership issues that come with using a linuix-native filesystem.
 
The ideal would be to use ext4, but have all existing and future files handled with owner and permissions as root:root 777 like it does with NTFS or FAT.
 
Can anyone help me achieve this? Or is my current NTFS setup the best way to achieve this. I already know it's the easiest compromise....
 
I have been googling all morning and all I can find is threads on interoperability with windows (which I dont need) or between different distros that use different usid numbering (which I dont need) The issue is 1 distro, 1 disk, 1 laptop, 2 users.
 
the following are NOT solutions:
 
*any solution requiring user action on an ongoing basis to manage file/folder access and ownership.
* any solution which involves me creating special users or groups that are not already on my system. root:root 777 is fine.
* any "solution" along the lines of "why are you trying to do that? You should do it this way" or "what you are trying to do is wrong" etc. If you have such an opinion, please offer alternatives AFTER a solution has been found. Please consider the fact that I am trying to do this for good reasons, which have hopefully been explained.
 
A Big Thankyou in advance for any help I recieve.
 
partiton, permission, access, mounting, filesystem

---

### Post by coffeecat on 2012-11-21
> **ex-oficio said:**
> I have to keep recursively using chmod/chown as root to sort things out.

I'm surprised you had to do that more than once, but anyway...

It seems to be a little known thing that you can can chown and chmod an empty filesystem by chowning and chmodding the mountpoint **while it is mounted**. The mountpoint itself doesn't get changed - the fileystem does. So - create your ext4 filesystem and then mount it. Don't try to copy any files onto it with root privileges. Let's assume the mountpoint is /media/mountpoint - change as necessary. Then:

```
sudo chown yourusername:yourusername /media/mountpoint
sudo chmod 777 /media/mountpoint
```

In fact if you and your wife are working from the same Ubuntu account, and therefore have the same UID:GID, you can safely omit the chmod. If you have separate accounts and therefore different UIDs, you will need the chmod. After you run those commands, you can do drag and drop copies just as you did with the FAT32 partition, and you can make folders as needed without root privileges.

---

### Post by LiamOS on 2012-11-21
I'd echo the above.

As far as filesystems go, I'm a massive btrfs fan, but I don't think that you'd see the benefits of it on that partition. 
xfs is a good filesystem for large files and lots of small files, but has been known to be a bit shaky on bad disks. I've also had a few computers refuse to boot after a bad shutdown with xfs. It's a really easy fix(boot a live cd, mount partition, umount, shutdown), but it's irritating when it happens.
jfs and reiserfs are also pretty nice filesystems. I personally use reiserfs on a partition where I have hundreds of thousands on tiny files, and it uses only 1/4 of the space that xfs took on the same partition, and 3/4 of the space ext2 took.
I've never really used jfs, but I've heard good things, so it might be worth looking into.

---

### Post by ex-oficio on 2012-11-21
Hi, thanks for the reply coffeecat, but unfortunately it doesnt help.
 
when I experimented with ext4, I chmodded the mount point to 777 (didnt change the owner from root, as it doesnt effect who owns subsequent files and folders) so there was no isue with access to the partion at the top level. So ok that's easily fixed.
 
To clarify, we are using seperate accounts. If we were sharing, there would be no issue at all, but because we use two different accounts, the problems come when we start putting files and folders in the partition. we start running into problems with file access, in a way that just doesn't/can't happen when the partition is NTFS.
 
running chmod will fix access for whats there NOW, but as we add file and folders the problem comes back. I can fix it, but what I'm saying is I dont need this posix security and I want to do away with it on this partition.
 
NTFS is one solution, but I hoped I could use a fastrer native FS without getting all the encumberance of difference owners/permissions.
 
I hope that clarifies my problem.
 
I just want to filesystem to behave like a fat32 flash drive, but without actually BEING FAT32 or NTFS.
 
I can't be the only one wanting to do this.... surely?

---

### Post by coffeecat on 2012-11-21
> **ex-oficio said:**
> 
To clarify, we are using seperate accounts. If we were sharing, there would be no issue at all, but because we use two different accounts, the problems come when we start putting files and folders in the partition. we start running into problems with file access, in a way that just doesn't/can't happen when the partition is NTFS.

I'll assume you want to be able to access each other's files. Some married couples don't! :wink: Try this then. Create a new usergroup, say "shared", and assign both your user accounts to the new usergroup. Now:

```
sudo chown root:shared /media/mountpoint
sudo chmod 777 /media/mountpoint
```

I must admit I haven't tried this since I'm the only one using my computer, but I'm fairly confident this will work since whether you or your wife create folder or files, they will be owned by a usergroup you both belong to.

By the way, if you're using a recent version of Ubuntu, and you want to use a GUI tool to create a new usergroup and the rest, don't use the default "User Accounts" utility. It's - ahem - lacking in functionality. Install the package gnome-system-tools and then open the utility "Users and Groups". You'll find that somewhat more usable.

---

### Post by ex-oficio on 2012-11-21
Coffeecat,
 
that sounds promising.
 
yes, our home folders which are on the / ext4 partition are ... ahem.. private, as you say, but as you co0rrectly deduce, we want the shared partition to totally open, read/write etc on all current and future files and folders without having to manually correct/alter permissions ever. Like it would be if we permanently had a fat32 usb flash drive stuck in the side of the laptop.
 
So with your suggestion, if I reformat /mnt/Archive to ext4, two questions follow:
 
!) could I chown the /mnt/Archive (when it's mounted) to nobody:nobody, instead of creating a new user or group?
 
2) will these be "sticky" in the sense that if user "bob" (with default group "bob") enters that directory and creates a file or folder will it have ownership bob:nobody or bob:bob ? if the latter, I'm back to square one.
 
how would the suid option (in /etc/fstab) affect this? do I need to use a customised umask to ensure that both users will always be able to traverse the whole tree  or delete/create/modify any file or fiolder with impunity irrespective of who created specific files and folders (strictly within the /mnt/Archive) partition?
 
I really appreciate the help.

---

### Post by Morbius1 on 2012-11-21
You have 3 ( at least ) options:

**1** Leave it as NTFS since it does exactly what you want. You will get teased by the penguinistas in the playground but they will end up working for you when they grow up so ...

**2** You can use the classic method around this.

[1] Change the group of the ext4 partition to plugdev ( already exists on your system ):
```
sudo chown :plugdev /mnt/Archive
```[2] Set the setgid bit of that mountpoint so that any new file inherits that group:
```
sudo chmod 2775 /mnt/Archive
```You didn't tell us what version of Ubuntu you are using so you may have to add your wife to the plugdev group:
```
sudo gpasswd -a wife plugdev
```**3** You can use use bindfs that will create a "view" of that partition that will make it look a lot like an ntfs partition.

**[1] Install bindfs:**
```
 sudo apt-get install bindfs
```**[2] To see how this will work you can temporarily create this view:**
```
sudo bindfs -o perms=0666:+X /mnt/Archive /mnt/Archive
```That looks a little funny but what you are doing is mounting /mnt/Achive to itself with a view determined by the bindfs command. All old and any new files added while this view is in effect will have read / write permissions to everyone.

[COLOR=Blue]*Note: to undo this view unmount it:*[/COLOR]
```
sudo umount /mnt/Archive
```If that does what you want it to do then add the line without sudo to /etc/rc.local before the "exit 0" line:
```
bindfs -o perms=0666:+X /mnt/Archive /mnt/Archive
```Note: There may be a timing issue with using rc.local where the bindfs command is executed before the partition itself is mounted. If that happens then the best solution is to create an upstart job which I can help you with if there is an issue with using rc.local.

[COLOR=Blue]**EDIT**: Don't know why but I should have added that /mnt/Archive has to be auto-mounted first by adding the appropriate line in /etc/fstab in order for bindfs to do it's thing. You didn't mention if you are or are planning to have this partition mounted at boot but it is a requirement.[/COLOR]

---

### Post by coffeecat on 2012-11-21
> **ex-oficio said:**
> 
 
!) could I chown the /mnt/Archive (when it's mounted) to nobody:nobody, instead of creating a new user or group?

Interesting idea. I assume you mean user = nobody and group = nogroup, so it would be nobody:nogroup. Tbh, I don't know. Try chowning to nobody:nogroup and chmod 777 and see if it works. Let us know! :)

I have to go out shortly for a few hours, but I'll come back to the other points later. Or I'm sure someone else will have commented before then.

---

### Post by Morbius1 on 2012-11-21
I'm going to be in and out of the forums the rest of the day so for completeness sake if you go the bindfs route I'll show you how I set up an upstart job to implement bindfs:

**[1] Create an upstart file:**
```
gksu gedit /etc/init/bindfs-mounts.conf
```**[2] Add this content:**
```
# Create a common directory using bindfs
description "Shared Directory"

start on stopped mountall

script
 bindfs -o perms=0666:+X /mnt/Archive /mnt/Archive
end script

```"start on stopped mountall" will insure that the bindfs command is executed only after everything else has been mounted at boot.

---

### Post by ex-oficio on 2012-11-21
Morbius1 and Coffeecat,
 
Thanks for your suggestions, and the effort and time you've put into providing them.
 
As Morbius1 points out, NTFS does exactly what I want already, with the two big caveats that A) I dont trust it like I trust ext4, and B) the fiddling I've already done shows that ext4 is considerably faster, while NTFS and FAT were not only slower, but required a lot more cpu usage when reading/writing, and this matters to me, especially when I'm out on battery power. I dont know if this is because the implementations are less efficient or if the filesystem is iherently less efficient, but either way I want to save time and battery juice.
 
I think you've both given me enough to occupy the whole of tonight and I'll report back to you what worked for me, or if indeed I ended up staying with NTFS (I hope not).
 
I want to go with whatever option gives me the desired effect with the minimum change to the system, partly because I just think this should be easier. I bet it's stuff like this that puts off newcomers to the linux world. I can't help but feel there should be a "nosecurity" option that can be placed on the appropriate line for the partition in /etc/fstab/, which basically makes the kernel treat any partition in the same way as it treats NTFS/VFAT. I'm surprised at the absence of a "standard" simple way to acheive this, but thats another matter for now....
 
Anyway, people, I don't know where in the world you are, but here in the UK its 13:50 and I'm supposed to be hard at work, so I'll be reporting back and hopefully marking this thread solved although not for at least 8 hours I expect...
 
Cheers for now.

---

### Post by ex-oficio on 2012-11-21
Oh, and finally, to answer your questions, I'm using 10.04 Lucid, and yes as has always been the case on my setup, /mnt/Archive is to be automatically mounted at boot via /etc/fstab

---

### Post by Morbius1 on 2012-11-21
Random thoughts in no particular order:
> As Morbius1 points out, NTFS does exactly what I want already, with the  two big caveats that A) I dont trust it like I trust ext4, and B) the  fiddling I've already done shows that ext4 is considerably faster, while  NTFS and FAT were not only slower, but required a lot more cpu usage  when reading/writing, and this matters to me, especially when I'm out on  battery power.If a mounted ntfs partition has that much of a performance hit on your system then bindfs may not be your best solution. Although the mechanism is slightly different bindfs is using the same method ( fuse ) to achieve a mounted ext4 partition with NTFS like immutable permissions. You can try mounting it through the terminal on a temporary basis to see if it does have an impact then abandon the idea if it does.
> I'm using 10.04 Lucid,If you use the setgid method:
> **2** You can use the classic method around this.

[1] Change the group of the ext4 partition to plugdev ( already exists on your system ):
```
      sudo chown :plugdev /mnt/Archive 
```[2] Set the setgid bit of that mountpoint so that any new file inherits that group:
```
      sudo chmod 2775 /mnt/Archive 
```You didn't tell us what version of Ubuntu you are using so you may have to add your wife to the plugdev group:
```
sudo gpasswd -a wife plugdev 
```You will need an additional step. You need to change the default umask of your system so that non root users save with 664 permissions instead of the default 644. Edit and change the umask value in /etc/profile to: umask 002. Later versions of Ubuntu have made the default 002 so no change is required. 
> I can't help but feel there should be a "nosecurity" option that can be  placed on the appropriate line for the partition in /etc/fstab/, which  basically makes the kernel treat any partition in the same way as it  treats NTFS/VFAT.Doing a chmod 777 will in fact allow anyone to read and write to the folder meaning that anyone will be able to add or delete a file. The question is what rights do you want to give users for the files themselves. If "wife" adds a file it will save as wife:wife 644. "Husband" can delete the file because of the 777 on the parent directory but he will not be able to edit the file itself.

If you enable the setgid bit, change the group, and change the default umask then when "wife" adds a file it will save as wife:plugdev 664. Both husband and wife are members of the plugdev group so both have edit access to individual files.

---

### Post by ex-oficio on 2012-11-21
> You will need an additional step. You need to change the default umask of your system so that non root users save with 664 permissions instead of the default 644. Edit and change the umask value in /etc/profile to: umask 002. Later versions of Ubuntu have made the default 002 so no change is required.....

....If you enable the setgid bit, change the group, and change the default umask then when "wife" adds a file it will save as wife:plugdev 664. Both husband and wife are members of the plugdev group so both have edit access to individual files.
 
Great stuff Morbius1, I think your option 2 will probably work for me. These last two bits of info you've provided above seem to address my lingering concerns, but I'll ned to check tonight to confirm.

---

### Post by ex-oficio on 2012-11-21
By the way, can i set a umask of 002 in fstab entry for /mnt/Archive, and achieve the same result?

---

### Post by ex-oficio on 2012-11-21
never mind, i now realise that umask in fstab is only for filesystems that dont natively support the unix security model. I will set umask to 002 in /etc/profile and do a reboot.

---

### Post by ex-oficio on 2012-11-21
So, option 2 was the solution for me. Incidentally, I use /media/Archive and not /mnt/Archive not sure why I said /mnt earlier when I meant /media/. Strictly, /mnt/ is supposed to be used for permanent mounts, but using /media/ causes the mount to be shown on the desktop and in "places" in the places menu and in nautilus, as if it were a removable drive, which is the behaviour I want.
 
I did the following, which I am writing out in full for the benefit of others who might want this:
 
formatted and labelled the partition in gparted. I like gparted, but there are of course other ways.
 
created mount point:
```
 sudo mkdir /media/Archive 
```set up fstab:
```
 sudo gedit /etc/fstab &  
```adding the line:
```
 UUID=caa348d4-ec6b-45c1-8e9b-c2cc9f653cde /media/Archive  ext4    errors=remount-ro 0       2 
```obviously your uuid, options and pass number will/may vary...
 
Partition needs to be mounted at this point...
```
sudo mount -a
```
 
I also removed the reserved space on this partition, as there's no need to it. I have 1% reserved on / so I dont need anything reserved on this one:
```
sudo tune2fs -m 0 /dev/sda3
```again milage varies on partition id.
 
set group and sgid permissions as 
```
sudo chown :plugdev /media/Archive
``````
sudo chmod 2775 /media/Archive
```didnt need to add anyone to plugdev as I already did that in the past. it can be done many ways, including like so:
```
sudo gpasswd -a wife plugdev
```change the umask value in /etc/profile to: umask 002:
```
 sudo gedit /etc/profile &  
```in mine it was the last line, changed to:
```
umask 002
```reboot e.g.
```
sudo reboot 
```Now, it turns out that even though it had no effect, linux finds a way to shoe-horn its own permissions into NTFS, so when I copied all my files from my backup usb drive (also NTFS) the files had all sorts of incorrect permissions, I suspect partially due to having been on fat32 previously (although the right group id, thanks Morbius1 ;) )
 
So I ran the following commands on my Archive partition, (and my NTFS usb drive for good measure....). The second one is because I have windows and linux executables on there and I want them set executable, and the second command also fixes the directories as they are also regarded as executable objects by linux, :D The IFS=$'\n'; is really important as if there are files or folders with spaces in their names things will go badly if you leave it out....
 
```

IFS=$'\n';  for i in `find /media/Archive/ -type f`; do chmod 664 $i ; done
``````
IFS=$'\n'; for i in `find /media/Archive/ -executable`; do chmod 775 $i ; done
```
 
Obviously, for anyone following this, change /media/Archive to whatever is correct for you...
 
And that's it!
 
I've been testing it between the two different user accounts, and the usid gets set according to who creates files and folders, but the gid is always plugdev and there are no access issues.
 
MUCH RESPECT TO MORBIUS1 for the solution, and a tip of the hat to coffeecat for his help too.
 
I hope this helps someone.
 
.

---

### Post by oldfred on 2013-01-14
I do not fully understand all of it either. But saved a few threads of users that seem to:

       user-friendly shared disk space NTFS/FAT/EXT4 - posts by Morbius1
[http://ubuntuforums.org/showthread.php?t=2086540](http://ubuntuforums.org/showthread.php?t=2086540)

    
       Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

