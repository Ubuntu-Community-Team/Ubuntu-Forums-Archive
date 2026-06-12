---
title: "How to have full access to other HD partitions"
date: 2014-10-19
forum: General Help
---

### Post by flix3 on 2014-10-19
Hello.

When I installed Ubuntu some year ago, as far as I can remember, I could see my unmounted Windows Partition on the left side of the screen. I could mount it and drag files inside.

Now I've reformatted that partition to ext4 (it's intended to be used as a data partition for now).
When I start Ubuntu, I can still see that unmounted partition on the left size of the screen, I can still mount it, but I cannot drag files into it any more, because I'm not "root".

I've read that the solution to have permanent access is to change the permission of the "mounting directory", but my intention is not to preserve the mounted state, I just want that, once mounted, I can be able to drag files into it (and this capability must be persistent). Basically I don't know if the mounting directory can have its permissions changed in a persistent way, even if it does not exist yet.

How can I do it ?

P.S. By the way: windows entries in grub2 are still the same, even if I reformatted my Windows partition. I don't know how to delete them (or to boot directly to Ubuntu).

Any help is welcome.
Thank you in advance.

---

### Post by Dennis N on 2014-10-19
> How can I do it ?

To have access to the new ext4 partition, you need to change owner and group of the mount point, not the permissions. When you made the partition, suppose you gave it the label 'data', so that when you mount it it mounts at /media/username/data.

Change owner and group with:

```
sudo chown username:username /media/username/data
```

(Substitute your user name for 'username' of course.)

Then, any folders or files created or copied in data will belong to you. The change is persistent.

---

### Post by nerdtron on 2014-10-19
Don't forget to add the -R option to go down recursively on all folders
```
sudo chown -R username:username /media/username/data
```

---

### Post by oldfred on 2014-10-19
If you want it automatically mounted whenever you reboot you can also do that. Best only if permanently attached drive not external drive.

I will not get into the discussion on where to mount it, I prefer /mnt/data, many use /media which has been the default mount for external devices. Although new versions now use /media/$USER.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

   [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If mounted at /mnt/data, I use these commands. $USER is you. Note -R is recusion and do not run on any system partition, only on your data partition(s). If accidentally run on a system partition assume a reinstall is required.

 sudo chmod -R a+rwX,o-w /mnt/data
      
 sudo chown -R $USER:$USER /mnt/data

Specific example of mounting in fstab for both Linux & NTFS partitions:

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by Dennis N on 2014-10-19
> Don't forget to add the -R option to go down recursively on all folders

@flix3;

Since you just made this new ext4 partition for data and say you have been unable to add (drag) any files to it, I assume the data folder is empty. If there is nothing in it yet, you don't need the -R in the command. Anything that you copy, move, or save or create inside the folder afterwards will belong to you.

But, in a case where you are changing ownership and group of some folder containing **existing** data, then nerdtron is corrrect, you need the -R option (added immediately after chown). This option changes the ownership of the folder and also all existing files/folders it contains.

---

### Post by flix3 on 2014-10-20
Thank you all for your answers :)

---

