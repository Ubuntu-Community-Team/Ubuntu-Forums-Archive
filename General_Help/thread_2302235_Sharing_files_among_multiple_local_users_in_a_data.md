---
title: "Sharing files among multiple local users in a data partition."
date: 2015-11-08
forum: General Help
---

### Post by jjapol on 2015-11-08
Hey there everybody. Got a small issue that is driving me a little batty. Been picking away at it for two days now.

I've got a laptop running 12.04. There are two user accounts. The first is "Jason", the second is "Dan". There will be more user accounts coming later.

I partitioned the 500gb disk so that the bootable partition with the OS is 100gb, formatted EXT4. I created another 400gb partition and also formatted it EXT4. I labeled the 400gb partition "data". Data is mounted at /media/data

I created the 400gb partition using the directions here: [http://ubuntuforums.org/showthread.php?t=1734233](http://ubuntuforums.org/showthread.php?t=1734233), post #2 by Mark Phelps using Gparted Live. This was successful.

Neither Jason or Dan can create files in the Data partition, although the folder is viewable from both accounts.

I attempted to follow the instructions for changing permissions from this post: [http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

Post #6 by Morbius1 seemed straight forward, but I am not having any success.

I am looking for the Data partition to be fully usable by anyone that logs in to the laptop with an account. Any user can create / delete / read / write /  any and all files or folders in the data folder.

(I also attempted to format the Data partition as NTFS per mention in other posts. Other posts seem to elude that UNIX permissions don't exist with NTFS partitions.)

I would prefer to stay in EXT4 as data transfer seems to be significantly higher from the boot partition to the Data partition.

Any and all help very very much appreciated.

Thanks in advance!

---

### Post by CantankRus on 2015-11-08
Can you not just change the permissions using the file manager as shown [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://www.howtogeek.com/189508/how-to-share-files-between-user-accounts-on-windows-linux-or-os-x").

---

### Post by bab1 on 2015-11-08
> **jjapol said:**
>  I am looking for the Data partition to be fully usable by anyone that logs in to the laptop with an account. Any user can create / delete / read / write /  any and all files or folders in the data folder.
...
I would prefer to stay in EXT4 as data transfer seems to be significantly higher from the boot partition to the Data partition.

For you to accomplish the above you will need to have user group that all users are in.  You will also need to set the sgid bit on the root folder of this shared file system.  If you were to share /media/data (and everything below that) then the root folder would be /media/data.

Setting the permissions in not really your problem.  Setting the proper ownership (in this case the group ownership) and making sure that the _***ownership is inherited in all files and directories created***_ from then on.

FYI.  I would not use /media for anything other than temporary mounting of removable media (cd's dvd's, usb sticks or external drives on occasion).  I would start with /data and set the permissions to 2775.  Then set the group ownership to a user group of your choice.  Ubuntu has a user group that is named **users ** by default.  I use this group.  Add all users to that group.  If you have data the already exists you will need to recursively change the group ownership of that data.

Do you understand the commands needed?  Questions or comments?

---

### Post by bab1 on 2015-11-08
> **CantankRus said:**
> Can you not just change the permissions using the file manager as shown [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://www.howtogeek.com/189508/how-to-share-files-between-user-accounts-on-windows-linux-or-os-x").
Setting the file and directory permissions works only if you are not going to add more data.  If you have users creating or modifying files and directories.  The ownership will change and break the sharing.

---

### Post by Morbius1 on 2015-11-09
> I attempted to follow the instructions for changing permissions from this post: [http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
Post #6 by Morbius1 seemed straight forward, but I am not having any success.
That was from 2011. Linux is like the weather; if you wait 5 minutes it changes :) :
> Here's one way:
```
sudo chown :plugdev /home/share 


```[COLOR=#0000cd]All local users are members of the plugdev group by default in Ubuntu[/COLOR].
```
sudo chmod 2775 /home/share 


```The "2" makes it so every new folder / file "inherits the group.
The "7"'s make sure the group has add / delete access to the share.

But there's one more thing necessary to pull this off:

Edit /etc/profile as root:
```
gksu gedit /etc/profile 


```Find the line at the bottom that references umask and change it to:
```
umask 002 


```What this will do is change the permissions on newly created  folder / files from 755 / 644 to 775 / 664. Now members of the group  can write to the file.
THe problem may be with the highlighted line in my post back then. Add yourself and all the other users to the plugdev group ( BTW, it doesn't have to be plugdev it can be any group. You can even create a new one if you want):
```
sudo gpasswd -a username plugdev
```
Then logoff and logon again for the group membership to be applied to that user.

I'm trying to remember when the default umask changed to 002 so I'm not sure if you have to modify /etc/profile in Ubuntu 12.04.

---

### Post by Bucky Ball on 2015-11-09
Slightly off topic, but why is the / partition 100Gb if all you have in there is Ubuntu and your data is on the /data partition? Ubuntu install will take up maybe 15Gb, if that. :)

I would launch Nautilus from a terminal with 

```
sudo nautilus
```

Navigate to the partition wherever you have it mounted, right click> preferences, and make it read/writeable by all. But I am no expert and it looks like others have this in hand. Good luck. :)

---

