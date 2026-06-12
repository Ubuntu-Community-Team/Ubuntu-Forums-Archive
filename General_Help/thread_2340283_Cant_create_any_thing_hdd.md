---
title: "Cant create any thing hdd"
date: 2016-10-17
forum: General Help
---

### Post by Arunomi on 2016-10-17
I formated a new hdd "Western digital 3tb hdd" its formated in ext4.
I have a hdd thats also the same brand and sizes and is formated in the same way.

I have mouned them in the same way but the new empty one i cant create any thing.

in the old one i can move files delete them, create foldres and files.

If I use sudo then i can create folders and file on it.

Of what I can see they have the same settings.

So could some one help me see what I have missed?

Best regards Sean

---

### Post by sed_faster on 2016-10-17
This happen when I formatted my usb drives! Normally I change the owner in /media/folder_correspondingly_drive! (chown user /path/to/folder) But I don't know if the best way to do this!

---

### Post by yancek on 2016-10-17
I'd suggest you check the owner:group again, particularly if you can modify with sudo.  That means your user does not own the directories. so use the chown command.

---

### Post by oldfred on 2016-10-17
Anytime I create a new ext4 partition, I give myself ownership & permissions to use it. I may manually mount if an external partition or permanently mount first with fstab. Example is manual mount of sda5, change to your partition(s).

 sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by sed_faster on 2016-10-18
Hello,

You can explain with more detail this command:
```

sudo chmod -R a+rwX,o-w /mnt/data

```
or where I can read more about this setup!

Thanks for explanation! When I formatted my pen drives, through gparted, I always freak out because I can't write on the folders! Always I needed run this commands! But now I know which I don't be alone :)

---

### Post by oldfred on 2016-10-19
With all Linux commands man pages may or may not offer good explanation or just some description
man chmod

The -R is recursion, so never ever use on a system partition, just data partition with only your data. Recursion walks down all the lower levels and changes them also.

 The big "X" will also not make files executable unless they were executable to begin with.

I used to suggest the octal numbers but a user who really understand configurations mentioned this:
 First, Octal chmods aways have to have odd values so that directories have the execute bit enabled.
But you don't want to do a "chmod -R 555 / path" either since that makes every file within it executable as well. It's best not to do a recursive chmod in octal at all but that's another discussion. 

        [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)

---

