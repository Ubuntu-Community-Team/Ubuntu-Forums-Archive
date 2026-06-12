---
title: "I can't figure out how to do something"
date: 2024-08-01
forum: General Help
---

### Post by jgw on 2024-08-01
I am running with Rhythmbox Audio Player.  I gave up on trying to get this to open my list of music to play.  So, I wonder if it is possible to sertup a little command line so that, when I start my machine, it will open my music folder.  If I can do that then Rhythmbox will immediately see it and its done.  Right now I just goto the drive its on and open it myself but I am lazy.  

Just thought I would ask - thank you............

---

### Post by grahammechanical on 2024-08-01
Just to be clear. You have your music folder on another drive/partition? If that is true, then you need to automount the drive/partition. This link explains how to edit /etc/fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Regards

---

### Post by jgw on 2024-08-01
Wow!  I was just getting ready to change my question and mention that my file is on another drive but, I think, you have found the solution.  I am going to give it a try!

Thanks again!  Will get back and report whether I succeeded or failed.

---

### Post by jgw on 2024-08-01
Since I am a coward I thought I had better ask   I am a question.

Here is my existing fstab as is:
[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=704193d7-3858-4289-9e3f-800b76c30957 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=88E5-D686  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
[/HTML]

Here is my fstab line to install: 9354305b-3831-4a1e-ac38-52fac40a1d4  /media/greg/misc/my_music  ext4  ro  0  1

I am not sure about the ro for option - will it freeze the whole folder so that it cannot be changed by something else later?  Should it be nouser which, I think, means only changes with sudo?  Just asking.......

I think all I have to do now is to sudo gedit fstab and enter my line and save the file?  Then I'm done?  (assuming my line is correct and I am where fstab resides when I do it)

Thank you!

---

### Post by Holger_Gehrke on 2024-08-01
Setting the file system to 'read only' on mount will not allow any writing, not even by root. You'd have to re-mount the file system to be able to write to it. The options used when mounting through udisks2 (which is what happens when you open the file system in your file manager or when auto-mounting after plugging a device in) are 'rw,nosuid,nodev,relatime,errors=remount-ro'. And I wouldn't use 'sudo gedit ...' for editing files, I'd use 'sudoedit' or 'sudo -e' with an appropriately set EDITOR variable, e.g. 'EDITOR=/usr/bin/gedit sudoedit /etc/fstab'. The advantage of this is that you're not running the editor with elevated privileges; sudoedit makes a copy owned by your account of the file, runs your chosen editor on that copy, and if the file was changed copies the changed file.

Holger

---

### Post by jgw on 2024-08-02
I did it.  My machine will no longer boot up.  I have attached a picture of what I get when I try to boot.  Continuing from this gets a few other things, but basically this is the end of the boot.  I really screwed the goose on this one.  I suspect that what I should actually do is take the 1 tb sdd, which is the main drive, out of the machine, edit and find fstab, and remove the line I inserted.  Put the sdd back into the computer and see if it boots.  If it does boot I then figure to either try again or just give up.

This is embarrassing.  I REALLY screwed up!!

Thoughts?

---

### Post by #&amp;thj^% on 2024-08-02
Will it get to grub if you use (Control +D)
If not your going to have to fix fstab or remove the lines you added.

EDIT: when I play around in fstab, I'll make a back-up first
```
sudo cp -a /etc/fstab /etc/fstab.bk

```
Always check with:
```
cd /etc && ls -la|grep fstab.bk
-rw-r--r--   1 root root     524 Aug  1 13:26 fstab.bk

```
And I still have my original as seen with:
```
nano /etc/fstab.bk

```

---

### Post by HermanAB on 2024-08-02
Boot with install media to desktop, mount the buggered disk, edit fstab and reboot without install media

---

### Post by Dennis N on 2024-08-02
Important: The mount point has to already exist when you mount with fstab.

Other tips:

Label the file system you are mounting. Then you can write the fstab entry without any uuid.
For the 'options' field, just use 'defaults' 

I like to mount my external data partitions on a subdirectory of /mnt By doing that, any snap application can access those files too.

As an example, here is the mount line for my data files, which exist on another disk partition. The file system I am mounting was labeled "Common-Files" beforehand. The mount point has the same name, but it doesn't have to.

```
# mount the data LV
LABEL=Common-Files /mnt/Common-Files ext4 defaults 0 2
```

The utility e2label will label an ext4 file system. Example:
```
sudo e2label /dev/sda6 Common-Files
```

---

### Post by yancek on 2024-08-02
> 9354305b-3831-4a1e-ac38-52fac40a1d4  /media/greg/misc/my_music  ext4  ro  0  1 

You did put UUID= at the beginning of that line, correct.  And as mentioned the directories music/my_music must already exist under /medi/greg.  You might add a comment line above the entry so you know what its purpose is, similar to the lines above the entries for the / and /boot/efi partitions.i

---

### Post by jgw on 2024-08-02
Thank you for all the replies!!
I just took out the ssd and put it into a different machine, went to it, and took the line out of the offended file (fstab - put '#' in front of the offending line so I didn't lose it, just in case) then put the ssd back in the computer.  It booted right up and looked good but, just in case, I rebooted, its still just fine (sending this from the machine I screwed up).   Nothing is wrong and nothing has changed.  My line was:
9354305b-3831-4a1e-ac38-52fac40a1d4  /media/greg/misc/my_music  ext4  defaults  0  1

My error, I think, was "defaults" which screwed it all up.  I went to fstab and there it was '#' but still there!  Not sure what I'm gonna do next.  I screwed up bigtime and I really don't want to do that again!  Figure I am just getting to damned old to do stuff I have been doing for years.  Perhaps its time to backoff a bit.....

Thanks again!!

---

### Post by Quarkrad on 2024-08-03
Assuming 9354........40a1d4 is the UUID of your hd then your line should read:

UUID=9354........40a1d4  /media/greg/misc/my_music ext4 defaults 0 1

As said above - the **my_music folder** should exist, you have to manually create it.  Before changing fstab make sure the folder /**media/greg/misc/my_music** is there.

---

