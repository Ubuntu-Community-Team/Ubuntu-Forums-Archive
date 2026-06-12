---
title: "Problems with mounted partitions on USB drive: Root owns them"
date: 2012-10-27
forum: General Help
---

### Post by mikodo on 2012-10-27
Not a descriptive title. I apologize.

I. I started with problems, when re-partitioning my USB drive, and wound up with 2 of my 3 partitions on it, owned by root.

2. I don't know how to fix that and started playing around with two GUI apps called mountmanager and pysdm.

3. I didn't get anywhere with the root ownership thing with the 2 partitions, and reinstalled them a few times with gparted, to no avail, still ownership by root, whatever I called them. I deleted the 2 partitions with Gparted .

4. Shut-down and went to bed at 04:00, confused.

5. When starting the computer this a.m., I was given the messages on screen:

"The drive for media/sdf5 is not ready or not present", I hit "s" to skip, and was given the second message, " The disk drive for /media/backup2 is not ready yet or not present", and again hit "s" to skip and was able to boot into Ubuntu.

6. I started up the USB drive and ran: gksu gedit /etc/fstab and uncommented the partitions, that are the offending ones.
```

UUID=1b3bf77f-702f-45fc-831b-404daba90305  /               ext4  defaults  0  1  
UUID=387dd97f-93e1-4edb-a9ef-8ab4aa5c4a13  /home           ext4  defaults  0  2  
UUID=05482d21-e398-4fd6-882c-1ecab0c146f3  swap            swap  sw        0  0  
UUID=b9cbb5e3-f00e-47a1-89d2-4e2c175faaf4  /media/VBox     ext4  defaults  0  0  
**/dev/sdf5                                  /media/sdf5     ext4  defaults  0  0  
**/dev/sdf6                                  /media/backup2  ext4  users     0  0  

```7. Closed the USB drive and rebooted the computer to receive these messages: "an error occurred while mounting /media/sdf5" and "an error occurred while mounting /media/backup2" and again for each I hit "s" to skip and booted into my OS.

8. I ran Gparted and repartitioned two new  partitions on the USB drive, and have Root ownership problems with them, too.

9.** I want to stop the errors on reboot, ** that I have to skip through. Are they mtab problems?

10. I used "gksu nautilus" and moved to trash, both the offending partitions, (/media/sdf5 && /media/backup2) and upon rebooting, they came right back, with the preceding messages on reboot "An error occurred while mounting both /media/sdf5 && /media/backup2, that I had to "skip" through. Again, are they "mtab" problems, that can be fixed?

11.  **Eventually**, I want to take ownership of the two new partitions on the USB drive.

12. Some results of things as they are now, as shown in: 

[http://paste.ubuntu.com/1310412/](http://paste.ubuntu.com/1310412/)

cat /etc/fstab
sudo blkid ls -l /dev/disk/by-uuid
sudo fdisk -l
sudo mount -a

**Thank you, for reading this far.**

---

### Post by oldfred on 2012-10-27
Your listings of UUIDs do not show any sdf5 or sdf6.

In fstab always better to use UUIDs as drives can get renumbered.

Usually external drives are not in fstab as you get errors if external not present. But you need to power it up first so it is available. An external may not come up to speed and be available during boot.

I would use relatime unless you want noatime as parameters. see man mount.

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

And if you have sub-folders this will put correct permission on folders & files:
sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

---

### Post by ajgreeny on 2012-10-27
Firstly   USB partitions/disks do not need fstab entries in normal situations, and fstab should preferably use the UUIDs of partitions, not the device sdx# naming method.

However the partitions sdf5 and sdf6 definitely do not exist which is why the error keeps showing.  If you look at the sudo fdisk -l output you will see that you only have sdf1, sdf2, and sdf3;  so what makes you think you have sdf5 and sdf6?

I have no idea what you want to do with the /dev/sdf ext4 partitions which are showing in blkid as:-```
/dev/sdf1: UUID="0f7f47da-4739-403b-88b6-6a4ee18e1c22" TYPE="ext4"  /dev/sdf2: UUID="005db7cd-6b76-4f88-be85-25d1a8573578" TYPE="ext4"  /dev/sdf3: UUID="1b111bab-99cf-42cd-939d-daad8f0de282" TYPE="ext4" 
```but they can all be mounted read/write if you wish by editing fstab, deleting the entries for those partitions, and then changing mountpoint permissions using ```
sudo chown *username:username* /media/Vbox
```and repeated for each partition with the different /media/*foldername* for each mountpoint.

Come back again if this is all gobledegook to you and I'll try to walk you through things, but can you answer my questions first so I don't make you loose any data you have on the partitions at the moment.

---

### Post by mikodo on 2012-10-27
> **ajgreeny said:**
>   so what makes you think you have sdf5 and sdf6?

I have no idea what you want to do with the /dev/sdf ext4 partitions which are showing in blkid as:-```
/dev/sdf1: UUID="0f7f47da-4739-403b-88b6-6a4ee18e1c22" TYPE="ext4"  /dev/sdf2: UUID="005db7cd-6b76-4f88-be85-25d1a8573578" TYPE="ext4"  /dev/sdf3: UUID="1b111bab-99cf-42cd-939d-daad8f0de282" TYPE="ext4" 
```.
Thanks guys. It really is all foreign to me ...

/dev/sdf1 = is my backup partition with BIT app and is working fine, (I think).

sdf5 and sdf6 keep showing up in Nautilus FM again after reboot, even after removing them with gksu nautilus before reboot. See screenshot below. sdf6 is seen by the name I gave it last nite as backup2

What do I want to do with /dev/sdf2 & /dev/sdf3 ? = be able to write to them, with my normal user, they now are owned by ROOT.

VBox, is mounted on rebooting/starting the computer as mounted to a mount point, by me  and works fine, we can leave that alone.

I want to get rid of these errors when I start the computer complaining that /media/sdf5 and /media/backup2 are not ready, or are not present at boot with the message stating that "errors occurred mounting them". I want to delete them permanently from my system and not have the OS trying to mount them (?mtab) on boot.

---

### Post by oldfred on 2012-10-27
The only place you seem to show sda5 & 6 is in fstab. Best just to comment out with # as first character.

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

Either totally delete these:

```
**/dev/sdf5                                  /media/sdf5     ext4  defaults  0  0  
**/dev/sdf6                                  /media/backup2  ext4  users     0  0

```

Or put # to convert to comment
```
#**/dev/sdf5                                  /media/sdf5     ext4  defaults  0  0  
#**/dev/sdf6                                  /media/backup2  ext4  users     0  0
```

---

### Post by mikodo on 2012-10-27
Thanks Fred. I will do what you say. Please, give me a little time to read it through and follow your directions correctly.

---

### Post by mikodo on 2012-10-27
I am going to close and reboot now.

---

### Post by mikodo on 2012-10-27
Well, thank you Fred. No errors about the offending, non-existent partitions on reboot! Yes!!!!

When I opened Nautilus, I still had entries of those two partitions in /media, so I opened gksudo nautilus and deleted them again. Rebooted again, and they didn't show up again! Yes!!!!

All, that is left is to set up is the two partitions in my USB drive that are still owned by root, which started this whole fiasco in the first place. They are seen in the screenshot below of gparted as:

/dev/sdf2

/dev/sdf3

---

### Post by oldfred on 2012-10-27
Go back to post #2 on permissions & ownership issues. chmod & chown

---

### Post by mikodo on 2012-10-27
> **oldfred said:**
> Go back to post #2 on permissions & ownership issues. chmod & chown
You bet I will, after a cigarette (I guess I will start with the nicotine patches tomorrow, instead of as planned today), and a peek at the television, to see how the Saskatchewan Roughriders are doing against the Toronto Argonauts.

Thanks so much!!!!

---

### Post by mikodo on 2012-10-27
Well, all is good. 

To the partitions that had root permissions, I ran the code below, and now I can read/write in them and they run with execution. 

```
sudo chmod mikodo:mikodo /media/UUID
```Thank you, everyone.

---

### Post by mikodo on 2012-10-27
I will not be going near mountmanager or pysdm again.

```
sudo aptitude purge mountmanager 

sudo aptitude purge pysdm
```

---

