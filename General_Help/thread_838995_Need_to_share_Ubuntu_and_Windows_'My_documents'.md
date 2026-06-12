---
title: "Need to share Ubuntu and Windows 'My documents'"
date: 2008-06-24
forum: General Help
---

### Post by phoenixankit on 2008-06-24
Here is my current partition config:
[B]1. 20gb-Windows-FAT32
2. 20gb-Media-FAT32
3. 20GB-Games-FAT32
4. 20GB-Work-NTFS
5. 1.2GB-swap-FAT3[/B]2(it's from the remains of my last Ubuntu installation.)
I'll use the 1.2gig drive as swap, after formatting it and all.
I will not touch the Windows, Media and Games drives
How much space do you think I need for Ubuntu? Lets consider this to be 'x'gb(I can manage x to be up to 10gb)
Using the ubuntu installer, I will partition xgb from my Work drive. Then I install ubuntu in that xgb drive.

Now, I want to share the the main Ubuntu documents folder(Home folder, was it? I dont remember) and Windows 'My documents'.
Now,

1.Can windows write to the Ubuntu x gig drive's home folder? If yes, how to make windows change it's My docs' path to that home(or whatever it was) folder.
**_OR_**
2. Can ubuntu write to the Windows 20gig drive? If yes, then How to change the path of Ubuntu's home folder(or whatever it is) to the* c:/Documents and settings/admin/admin*'s folder?

---

### Post by lisati on 2008-06-24
It is possible to get Ubuntu to write to a Windows-formatted drive, but if it's NTFS partition, you might need to install the NTFS-3G tool (it's available in the "Add/Remove programs" menu)

I've heard that it's possible to get Windows to write to an Ubuntu folder, but haven't actually done it myself.

Have you considered using the Windows "Shared documents" as an alternative to sharing "My Documents"?


EDIT: I've just had another look at your specs & don't see a problem if the Ubuntu partition is FAT-flavoured. However, I'd be wary of touching the SWAP partition.

---

### Post by molotov00 on 2008-06-24
We just solved this (literally an hour ago) here:

[http://ubuntuforums.org/showthread.php?t=838937](http://ubuntuforums.org/showthread.php?t=838937)

That thread has a little more than you need, but basically you are dealing with 'mount' to make your fat32 partitions browseable to Ubuntu and you need to use 'ln -s' to create symbolic links, making your two home directories the same. Btw, Ubuntu uses /home/username (as do most other distros).

Hope that helps.

EDIT: Another option just came to mind. You can use this:
```
sudo usermod -m /whatever/folder username
``` to make Ubuntu use /whatever/folder as your 'home'. Or, as described above, you can use a symbolic link (ln -s).

Either way, you'll need to 'mount' the partition you want to use as home directory. 

The short explanation:
Use 'fdisk -l' to find out what partition you want to mount (assuming FAT32)
Add this line to /etc/fstab (sudo nano /etc/fstab)
Make a folder called 'windows' in /mnt/ (or wherever you want)
```
/dev/<partition from fdisk -l command i.e. hdb1> /mnt/windows vfat iocharset=utf8,umask=000 0 0
```
Then:
```
sudo mount -a
``` to 'run' /etc/fstab

Then go ahead with your symbolic links or usermod.

---

### Post by phoenixankit on 2008-06-24
I just named it Swap, for identification purposes.
I didn't really understand your answer. My windows formatted drive is FAT32.
Also, tell me, how much is the optimum size(x) of the ubuntu drive?

EDIT: That was to lisati, not to molotov

---

### Post by molotov00 on 2008-06-24
> **phoenixankit said:**
> I just named it Swap, for identification purposes.
I didn't really understand your answer. My windows formatted drive is FAT32.
Also, tell me, how much is the optimum size(x) of the ubuntu drive?

You asked a lot of questions. I ran with the last one:
> 2. Can ubuntu write to the Windows 20gig drive? If yes, then How to change the path of Ubuntu's home folder(or whatever it is) to the c:/Documents and settings/admin/admin's folder? and I fed you everything I could, given what I know about your situation.

The other question I see relates to the size. I'd go with the max. Install Ubuntu first and then worry about the home directory... because you might find that Ubuntu automatically locates and mounts that FAT32 partition. It might be as simple as the usermod command.

---

### Post by phoenixankit on 2008-06-24
Dude, that "I didn't really understand your answer" was to lisati, not you!

---

