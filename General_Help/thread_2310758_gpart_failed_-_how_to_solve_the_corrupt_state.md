---
title: "gpart failed - how to solve the corrupt state?"
date: 2016-01-21
forum: General Help
---

### Post by Sky_Dog on 2016-01-21
Hi,

I have tried to expand my /dev/sda5 partition by deleting the next one and extending the size of /dev/sda5. During the process, GPART raised and error and now I have a corrupted state. What to do to resolve it?

[ATTACH=CONFIG]266877[/ATTACH]

Regards
SkyDog

---

### Post by ajgreeny on 2016-01-21
A few queries;

Are you trying to do this from within your installed Lubuntu or using a live system?  You will have to use a live system to do this as you can not work on mounted partitions.

What do you mean by "deleting the next one"?

Why is your root partition sda5 in a logical partition within an extended partition, but your swap outside that extended partition?  Very often that situation would be the reverse with swap as a logical partition and root a primary, though both can be logical within the extended partition with no problem.

Why such a large swap? How much ram do you have?

What was the gparted error?

We need more info before we can help you more.

---

### Post by Sky_Dog on 2016-01-22
> **ajgreeny said:**
> A few queries;

Are you trying to do this from within your installed Lubuntu or using a live system?  You will have to use a live system to do this as you can not work on mounted partitions.

What do you mean by "deleting the next one"?

Why is your root partition sda5 in a logical partition within an extended partition, but your swap outside that extended partition?  Very often that situation would be the reverse with swap as a logical partition and root a primary, though both can be logical within the extended partition with no problem.

Why such a large swap? How much ram do you have?

What was the gparted error?

We need more info before we can help you more.


1.- Are you trying to do this from within your installed Lubuntu or using a live system? 
-> I've performed this from my installed Ubuntu


2.- What do you mean by "deleting the next one"?
-> I had after the /dev/sda5 another partition for swap (SWAP_PARTITION). What I did was to delete the swap partition and extend /dev/sda5 till the end of the SWAP_PARTITION. Then Gpart raised an error and leaving a grey zone at the end of /dev/sda5 as you can see in the screenshot


3.- Why is your root partition sda5 in a logical partition within an extended partition, but your swap outside that extended partition? 
-> If I had to delete SWAP_PARTITION in order to extend /dev/sda5, then I thought that I had to create somewhere a new Swap partition. Then, what I did is to reduce the space of /dev/sda2 and put there a new Swap partition (/dev/sda4 in the screenshot)


4.- Why such a large swap? 
I wanted to make smaller the swap partition (/dev/sda4), but after the error in Gpart, I didn't change the swap partition.


5.- How much ram do you have?
8GB but I have to extend it to 16 GB because I have to use several RAM-consuming software.


6.- What was the gparted error?
As far as I remember, Gpart couldn't save the changes concerning the extension of /dev/sda5. Now I have a grey part in /dev/sda5 and it takes much longer to boot Ubuntu.


Please let me know if you have more questions.


Regards
SkyDog

---

### Post by ajgreeny on 2016-01-22
> **Sky_Dog said:**
> 1.- Are you trying to do this from within your installed Lubuntu or using a live system? 
-> I've performed this from my installed Ubuntu
[COLOR="#FF0000"]This Ubuntu is, I assume separate from the Lubuntu but on the same machine?[/COLOR]

2.- What do you mean by "deleting the next one"?
-> I had after the /dev/sda5 another partition for swap (SWAP_PARTITION). What I did was to delete the swap partition and extend /dev/sda5 till the end of the SWAP_PARTITION. Then Gpart raised an error and leaving a grey zone at the end of /dev/sda5 as you can see in the screenshot
[COLOR="#FF0000"]Did you use swapoff on the swap partition before deleting it?
Is the new swap partition listed in /etc/fstab of both Ubuntu and Lubuntu installations?[/COLOR]

3.- Why is your root partition sda5 in a logical partition within an extended partition, but your swap outside that extended partition? 
-> If I had to delete SWAP_PARTITION in order to extend /dev/sda5, then I thought that I had to create somewhere a new Swap partition. Then, what I did is to reduce the space of /dev/sda2 and put there a new Swap partition (/dev/sda4 in the screenshot)
[COLOR="#FF0000"]OK; That is a fair answer.[/COLOR]
4.- Why such a large swap? 
I wanted to make smaller the swap partition (/dev/sda4), but after the error in Gpart, I didn't change the swap partition.
[COLOR="#FF0000"]OK; That is also a fair answer.[/COLOR]

5.- How much ram do you have?
8GB but I have to extend it to 16 GB because I have to use several RAM-consuming software.


6.- What was the gparted error?
As far as I remember, Gpart couldn't save the changes concerning the extension of /dev/sda5. Now I have a grey part in /dev/sda5 and it takes much longer to boot Ubuntu.


Please let me know if you have more questions.


Regards
SkyDog

Can you still boot to both OSs?

---

### Post by Sky_Dog on 2016-01-22
1.- This Ubuntu is, I assume separate from the Lubuntu but on the same machine?
--> /dev/sda5 is the Ubuntu that it was running and which I wanted to extend. I thought that if I extend at the end of the running partition, no problem should occur. 
--> By the way, I dont use Lubuntu, only Ubuntu in /dev/sda5

2.- Did you use swapoff on the swap partition before deleting it?
--> I swapoff the initial swapp partition at the end of /dev/sda5

3.- Is the new swap partition listed in /etc/fstab of both Ubuntu and Lubuntu installations?
--> This is the output

```
$ cat fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=f9d66cef-c1a6-41e0-9213-94db644e759f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=eb0b8035-4ad6-40a7-9370-47c3ac365650 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

I dont know if the swap shown above is the old or the new one, but I supose that it's the old one



```
4.- Can you still boot to both OSs?
--> I only have Ubuntu and I can boot, but it takes much longer than before :-(

Any idea what to do?

---

### Post by ajgreeny on 2016-01-22
You appear to have an encrypted swap partition but I know nothing about encryption so can't help with any related to that.

However, how did you manage to use gparted to edit partitions that were in use by the OS that was running gparted? That is impossible to do so I am uncertain what you mean in your comment > --> /dev/sda5 is the Ubuntu that it was running and which I wanted to extend. I thought that if I extend at the end of the running partition, no problem should occur. 
I thought you were using Lubuntu as that was the OS listed in the tag box at the top; I have edited it now to read Ubuntu.

As your system now is slow to boot it may be worth running command ```
sudo touch /forcefsck
``` which will make the system run a filesystem check at the next boot.  That may find and fix any problems; if not I'm not sure where we can go from here.

---

### Post by Sky_Dog on 2016-01-23
> **ajgreeny said:**
> You appear to have an encrypted swap partition but I know nothing about encryption so can't help with any related to that.

However, how did you manage to use gparted to edit partitions that were in use by the OS that was running gparted? That is impossible to do so I am uncertain what you mean in your comment 
I thought you were using Lubuntu as that was the OS listed in the tag box at the top; I have edited it now to read Ubuntu.

As your system now is slow to boot it may be worth running command ```
sudo touch /forcefsck
``` which will make the system run a filesystem check at the next boot.  That may find and fix any problems; if not I'm not sure where we can go from here.

1.- However, how did you manage to use gparted to edit partitions that were in use by the OS that was running gparted? That is impossible ...
--> Possible. I have Windows and Ubuntun installed in the hard disk. I run GPart in Ubuntu (I only need to use the root password) and GPart opens. Then I can edit the partitions. Maybe I have this problem because I edited the partition where Gpart and Ubuntu runs. It seems that Gpart doesnt make any check if the partition to be modified is mounted or not, but it works.


2.- sudo touch /forcefsck
--> Thanks but it didnt performed any change. It showed no message concerning problems.


3.- if not I'm not sure where we can go from here.
--> Anyway, I thank to you for your help. I think I will have to reinstall Ubuntu again :-/

---

### Post by HermanAB on 2016-01-23
Uhm... while your system is still sortof working, do make a backup of all your data before doing anything else.

---

### Post by yancek on 2016-01-23
Partitions need to be "unmounted" for them to be "successfully" modified.  If you are running a system and trying to modify it, then it can not be unmounted.  As suggested above, when you are using GParted to modify partitions, use the Ubuntu installation medium or a GParted boot disk.

The fstab you posted shows the old entry for swap (sda6) which no longer exists.  It is also commented out so you could run the command:  sudo blkid and get the UUID for the current swap on sda4 and replace the old UUID with the new one and save the file.  I doubt this has anything to do with your problem.

---

