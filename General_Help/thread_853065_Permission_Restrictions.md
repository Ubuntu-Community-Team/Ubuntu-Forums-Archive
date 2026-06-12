---
title: "Permission Restrictions"
date: 2008-07-08
forum: General Help
---

### Post by jake1017 on 2008-07-08
I have Ubuntu HH 8.04 installed on my family desktop with two users, both administrators. On this desktop I have a partition (ext3) which is where pictures, music, videos, etc is stored. But if one user creates a file/folder the other user cannot modify it because of permission restrictions. Is there a way that any file/folder created on this partition by an user can be viewed and/or modified by another user?

Thank you in advance

NOTE: I do know that you can change permissions by right-clicking and choosing properties but this can become very annoying.

---

### Post by tszanon on 2008-07-08
I don't know if it would work, but have you tried changing the folder permissions? If both users have full access to the folders, then maybe all files created in those folder will have the same permissions.

---

### Post by jake1017 on 2008-07-08
I have tried something like that. The partition is owned by root and I have changes the permissions so that anyone that is in the root group can write/access files on the partition. This does work but only for the files that are on the partition at that time. New files created after the permission change still have permission restrictions to the user that created them.

---

### Post by robrmd9 on 2008-07-08
The restrictions placed on newly created files are set by [umask]("http://en.wikipedia.org/wiki/Umask").  

What I suggest you do is set the umask in a user's profile.

Keep in mind umask sets what permissions should _not_ be applied to newly created files.  If you aren't familiar with octal notation, then you should read up on chmod and UNIX file permissions.  It's not too complicated, but you have to get used to it.

---

### Post by jake1017 on 2008-07-08
How would you set umask in a user profile?

---

### Post by wdaniels on 2008-07-08
> **jake1017 said:**
> How would you set umask in a user profile?

You can set it system-wide in /etc/profile or per-user in /home/user/.bash_profile (where user should be the username).

However, this will affect all files, regardless of location. A better way might be to change just the ACL for the shared directory, in which case you can do something like:

```
sudo setfacl -d -m mask:007 /home/shared/
```

This would make the default umask for that directory allow write permissions to the group under /home/shared. Note that you would also need to set the default group for that directory for that to make any difference:

```
sudo chgrp groupname /home/shared/
sudo chmod g+s /home/shared/
```

(where groupname should be the name of the group to which all relevant users belong)

**But note that you will need to add the "acl" option to the relevant mount in the /etc/fstab file if you want to do it this way!**

Alternatively, since you say that the shared area is a whole partition, you could set the user/group/umask directly in the mount options in /etc/fstab (using uid, gid and umask options respectively).

The ACL method allows for fine-grained control, the fstab mount options is a good middle-ground, but the simplest and easiest way is probably to just set the system-wide umask as already mentioned.

---

### Post by jake1017 on 2008-07-09
How do you add the 'ACL' option to a mount in the /etc/fstab file?

---

### Post by wdaniels on 2008-07-09
> **jake1017 said:**
> How do you add the 'ACL' option to a mount in the /etc/fstab file?

First, one other thing I forgot to mention before is that the default 2.6 kernel only supports ACL for ext2, ext3, xfs and jfs filesystems. So, if you are using FAT32 or NTFS for example on the shared partition you would need to either convert it to a native Linux filesystem, or set the relevant options directly at the mount level for that partition (which still means editing fstab file anyway).

Refer to the [community documentation here]("https://help.ubuntu.com/community/Fstab#Options") for more information to help you understand the fstab file, which is a good investment of time. All you need to do is add "acl" to the list in the options field of the line(s) in fstab relating to whichever partition(s) you want to use the ACL extensions with. For example:

```
# /dev/sda1
UUID=abd6d0a9-d2b1-4f8b-abc5-033907b5b36d /home ext3 defaults,acl
```

...is a line in fstab that would mount the partition identified by that big long UUID (the more human-readable device name, such as "sda1" in this example, has usually been added as a comment above the line to help you know which is which). Your UUIDs will be different, so you should first familiarise yourself with the device names of your partitions ("sudo fdisk -l" ought to give you enough information), or perhaps identify them from the mount locations as shown in the fstab file.

In the example above, you can see that /home is given as the mount location, ext3 is the filesystem type and the mount options are in the fourth field, in this case  "defaults,acl", which basically just adds the "acl" option to the Ubuntu default options.

The change will not take effect until the next time the partition is mounted. If the partition concerned is not currently in use, you can mount it automatically in accordance with the fstab entries using the command:

```
sudo mount -a
```

...or simply just reboot.

If you try to use the command setfacl without the ACL option having been applied, you will see an error along the lines of "operation not supported". But once the partition is set to be mounted with the "acl" option, you should be able to use the setfacl command as directed in my previous post. To learn more about setfacl, read the documentation given by the command:

```
man setfacl
```

(or Google it of course)

---

### Post by chrisccoulson on 2008-07-09
I recommend wdaniels suggestion above to use ACL's. I use ACL's quite extensively at home, and they are very flexible. There is also a graphical front-end for editing ACL's, which integrates with Nautilus - Eiciel:
```
sudo apt-get install eiciel
```

---

### Post by wdaniels on 2008-07-09
> **chrisccoulson said:**
> I recommend wdaniels suggestion above to use ACL's. I use ACL's quite extensively at home, and they are very flexible. There is also a graphical front-end for editing ACL's, which integrates with Nautilus - Eiciel:
```
sudo apt-get install eiciel
```

A very nice extension. I didn't know about it actually, so thanks!

---

### Post by newagelink on 2008-07-09
[COLOR="Indigo"]This thread is too complicated. All I want is [to save a shtml file in Bluefish]("http://ubuntuforums.org/showpost.php?p=5351233&postcount=5").[/COLOR] :( [COLOR="Indigo"]I can save (that is, write) some files in that folder but not others.[/COLOR]

---

### Post by wdaniels on 2008-07-09
> **newagelink said:**
> This thread is too complicated.

It is not your thread and is not intended to address your problem. Most things to do with computers are complicated at first - you have to be willing to learn about them.

> **newagelink said:**
> All I want is [to save a shtml file in Bluefish]("http://ubuntuforums.org/showpost.php?p=5351233&postcount=5").[/COLOR] :( [COLOR="Indigo"]I can save (that is, write) some files in that folder but not others.[/COLOR]

In that case you have permission to write to some files in that folder but not others. The solution can be to either change the file permissions or change the user. Which is the correct solution depends on two things. First, what is the location of the file you want to edit? Second, why do you need to/think you should be able to edit it as a normal user?

If you don't want to have problems with file permissions then don't try to edit files outside your home directory. If you have files in your home directory that you cannot edit, the you must have run some program as another user (probably root) and then saved a file from that program there, in which case the file will be owned by the root user, as is only logical.

If you need to edit a file outside your home directory then you have to learn about file permissions - there is a reason why these files are protected. You should not go changing file permissions all over the place just so that you can edit them with the wrong user. If you need to edit a file as root then you have to become root, in which case the commands you are interested in will be sudo and gksudo (for text-based and graphical programs respectively).

---

### Post by newagelink on 2008-07-09
[COLOR="Indigo"]Thank you for the reply. I do wish to learn, but my progress is typically made in steps, not in leaps and bounds. The chmod manual is a bit overwhelming. I replied here because the OP's issue was very similar -- if not the same -- as my own; is it not? It seemed better to join existing threads about an issue rather than create a new one regarding the same ...

I have web pages stored in my Windows partition due to size constraints of my laptop's hard drive. (A small hard drive, I allocated perhaps 10 GB for Ubuntu Linux, and now use it as my primary operating system.) I have already successfully configured writing permission from this Ubuntu partition to the Windows partition.

The issue appears to be that I already have permission to edit the file, yet am not allowed to do so. I added the User Switcher applet to the taskbar, and right-clicked on it to edit Users and Groups. (I know of no other means to edit them. After going into the Help menu, I learn I can simply "sudo users-admin".)

See the attached screenshot of the file's permissions. UGO all have read & write access, do they not? Isn't my "daniel" account a member of "Others"? Should I make 'daniel' a member of the 'root' group? Do any of these permissions matter once the file is uploaded to the internet? (Or do these permissions hold, and I'm opening myself to anyone in the world editing my webpages online?)[/COLOR]

---

### Post by timcredible on 2008-07-09
i would just create a new group that both users are members of and do a chgrp -R <that new group> on the partition

---

### Post by newagelink on 2008-07-09
> **timcredible said:**
> i would just create a new group that both users are members of and do a chgrp -R <that new group> on the partition[COLOR="Indigo"]I don't want to change every file; it's only a select few that cause a problem. I wonder what the problem truly is: see that screenshot: Is it not saying I have permission to write? I want to fix the problem, not do a work-around...

Thanks for the suggestion; it's good for me to learn.[/COLOR]

---

### Post by FuturePilot on 2008-07-10
> **chrisccoulson said:**
> I recommend wdaniels suggestion above to use ACL's. I use ACL's quite extensively at home, and they are very flexible. There is also a graphical front-end for editing ACL's, which integrates with Nautilus - Eiciel:
```
sudo apt-get install eiciel
```

Wow! Thanks for that. I've been looking for something like that for a long time. :)

---

