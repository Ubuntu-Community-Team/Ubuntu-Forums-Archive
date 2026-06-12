---
title: "Issues with USB drives"
date: 2023-05-21
forum: General Help
---

### Post by binaryhellstorm on 2023-05-21
I  am having an issues with USB flash drives on my Ubuntu 22.04.2 box. All  of a sudden I'm having issues writing data to sticks. Often times what  will happen is that I'll plug a drive in and the system will claim that  it's unable to read the drive, I'll format it in FAT or NTFS copy some  files to it, eject it, remove it, and then plug it back in and the OS  will see the drive, but will say "Unable to access Volume" Error while  mounting dev/sda and /media/user/(long ID number) Unknown error when  mounting /dev/sda.
This is happening on multiple drives including two that are new out of the factory packaging.

---

### Post by MAFoElffen on 2023-05-22
First do this (This is where USB's auto-mount to) :
```

ls -lah /media/
groups zzzz\ grep 'plugdev'

```
Check the ownership and permissions of. /media itself, where USB mounts to.... Write to it. Unmount and disconnect. Then plug it in and recheck.

Second command, that group allows users to mount (only with the options nodev and nosuid, for security reasons) and umount removable devices through pmount.

---

### Post by binaryhellstorm on 2023-05-22
The owner of /media is root, if I drill down into media/USERNAME/ I see the mount point for the USB I inserted and it does show my user account as the owner. 
The second command won't run but if I check the group membership of plugdev with getent I do see my user account listed as a member

---

### Post by MAFoElffen on 2023-05-22
QUOTE:
> 
Unless overridden by mount options GID= or UID= the owner and permissions of the mount point upon mounting become those of the filesystem tree being mounted...

If there is an ownership / permissions problem with the default mountpoint for removable media (/media/$USER), then if you delete /media/$USER, then the next time you plug in a USB flash drive, that directory recreates itself with the default ownership and permissions of the User.

---

### Post by binaryhellstorm on 2023-05-22
Deleted the folder user /media as root and then plugged a flash drive in, wrote files, ejected, same issue. 
Folders got remade but they still show root as owner

```

total 12K
drwxr-xr-x   3 root root 4.0K May 22 11:11 .
drwxr-xr-x  20 root root 4.0K May 21 19:20 ..
drwxr-x---+  2 root root 4.0K May 22 11:13 user

```

---

### Post by ajgreeny on 2023-05-22
You need to change the **zzzz** to your own username in that second command you say didn't work and it also needs the pipe character.
Try ***groups $USER | grep 'plugdev'***

It should show you all the groups that you are a member of including hopefully, plugdev.

---

### Post by MAFoElffen on 2023-05-22
From now on, please post any commands and output wrapped within CODE Tags (Forum Policy). Lets keep you out of trouble with the Moderators. If you need instruction on how to do that please ask.
Do you really have your username set as "user'? LOL. Okay.

Here are the explanations of why it is owned by root now:
[https://askubuntu.com/a/336580/138255](https://askubuntu.com/a/336580/138255)
[https://askubuntu.com/q/392154/138255](https://askubuntu.com/q/392154/138255)

---

### Post by binaryhellstorm on 2023-05-22
> 
You need to change the **zzzz** to your own username in that second command you say didn't work and it also needs the pipe character.
Try ***groups $USER | grep 'plugdev'***

It should show you all the groups that you are a member of including hopefully, plugdev.


Yup it does show me as a member of plugdev

---

### Post by binaryhellstorm on 2023-05-22
>  					From now on, please post any commands and output wrapped within  CODE Tags (Forum Policy). Lets keep you out of trouble with the  Moderators. If you need instruction on how to do that please ask.
Done, thanks for the headsup

---

### Post by MAFoElffen on 2023-05-23
What you could do, and what I do... Is mountpoints to /media/$USER will then name the next folder name associated with what kind of device it is... Lets say that comes up as a name like in the answer provides there, as '/dev/bob/EXT4-250GB-US/'. If you do list that folder now, then it should show up as bob as the owner and group of that and everything under that.

If not, then there is a problem with the acl lists...or udisk2. 

Remember me pointing out (discreetly), that a mount inherits the  ownership of the mountpoint (hint)? 

My disclaimer-- There is a 'hack' around that change to revert back to the 'older' mount method of /media, but it is felt that it is a security concern and should not be done... By just changing the ownership of /media/$USER back to the user, like this
```

sudo chown $USER:$USER /media/$USER
sudo chmod 750 /media/$USER

```

---

