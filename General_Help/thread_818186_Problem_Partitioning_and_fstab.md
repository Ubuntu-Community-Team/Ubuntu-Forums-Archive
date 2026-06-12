---
title: "Problem Partitioning and fstab"
date: 2008-06-04
forum: General Help
---

### Post by ppttpp on 2008-06-04
Hey guys, I am a ubuntu (in fact a kubuntu) noob. I just switched from windows this week. :D

I am really not sure if this topic has to go to the absolute beginner section or not .. to moderators, make yourself feel at home ;)

As I was installing, they asked for partitioning and mount points. And as a windows user not used to the Linux filesystem, I did not see the importance of the 'mount point' beforehand -in fact I could not understand how it works or its importance in the first place- so I just made a partition for / and one for /home and one for a swap and the rest were logical partitions made to mount /d /e /f /g

The reason I chose the name was to be somewhat similar to my old windows pc and so that I can transfer files easily from each windows drive to its kubuntu counterpart.

However, for my ignorance, I realized that mount /d /e etc. is a problem, because ubuntu unlike windows has no root, and these directories are part of root-  so when I tried to copy via LAN my old music and data files to these mounts .. Konqueror replied that I have no permission. (of course I can sudo, kdesudo etc. but it will be a pain in the *** to not have default read/write permissions on my partitions and data files)

Ubuntu apparently if I am not mistaken needs everything to go into the /home dir so that I can have the permissions by default and everything outside it makes root the owner by default.

Anyway, so my question is:
1) Is it a good practice to change my mount points of my four logical partitions (/d /e /f /g) to /home/usrname/Documents and /home/usrname/Music and /home/usrname/Download etc. in fstab
Noting that:
     a) they are still empty folders
     b) I have  a separate /home partition already

2) I in fact tried the above solution and I started playing with fstab but when I changed the mount points from /d /e etc. to the /home/usrname/subdirs scheme, they refuse to mount and Dolphin reports an error .. "Refusing to mount. Only root has the permission to mount "

It is mind-boggling because this error does not show up when I mount /d /e etc.!!

What is the best solution from your points of view?

Regards.

---

### Post by justleen on 2008-06-04
youre on the right track though.

Yes, you can move the mount point to any other place, as long as the changes are refelcted in the fstab.

And only root can mount. so add "sudo" in front of the mount command
```

sudo mount /dev/hda1 /home/user/d

```
to test wether your fstab is correct (and quickly mount all drives) 
```
 sudo mount -a
```
that will mount all un-mounted drives from fstab.


edit: its not "good practice" as such, mount points can reside any where.. to keep things logical and managable you might want to have them some where else ( /mnt, /media for example)

---

### Post by ppttpp on 2008-06-04
Thank you for your reply.

But if I have my fstab to mount on /mnt/Download /mnt/Documents etc. this will again be away from the home dir and I will have to sudo all the way again.

I want my data files to be native read-write and I don't want to sudo everytime I edit my word documents.

Is there a solution to this?

Number two:
you say I use sudo mount so that I can have the permission .. this is fair, but I don't want to type sudo mount -a everytime I login ;) There has to be a way to edit fstab so that he can carry out his job for good without me interfering every login, correct? :)

---

### Post by bingoUV on 2008-06-04
**1) Is it a good practice to change my mount points of my four logical partitions (/d /e /f /g) to /home/usrname/Documents and /home/usrname/Music and /home/usrname/Download etc. in fstab**

No, it is not a good practice, nor a popular practice. There are reasons for this, and if they do not apply to you, you can mount them inside /home without issues. Read this for reasons : [http://ubuntuforums.org/showpost.php?p=5105947&postcount=2](http://ubuntuforums.org/showpost.php?p=5105947&postcount=2).

Also, mounting in /home will not guarantee that your user will have write permissions to the mounted directory.

If you want other users to have the ability to mount those partitions, add the option "user" to fstab entry. If you want a specific user to have the ability to mount the partition, add the option "owner" in /etc/fstab, and add this line in /etc/rc.local
```

chown <username>:<username> /dev/<partition>

```

Post the contents of /etc/fstab if you have problems

---

### Post by ppttpp on 2008-06-04
Thanks Bingo, I read your post and it is very informative.

Note: they are not network drives but local partitions. (although I will be sharing them on my LAN eventually)

Ok then, now I need to mount to /media/Download /media/Documents respectively etc.

I will try to get a stab at fstab then and will post you the contents and results ;)

But the question now .. will I have native permissions on my files (without the bugging need for sudo everytime) .. and if this won't happen, is there a command that I will need to do so that my username will be the proud owner of the new partitions (media/Documents etc.) folders?

Other nooby questions:
What is the function of the chown? and what is the file "/etc/rc.local" and its function?

---

### Post by bingoUV on 2008-06-04
Even if they are local mounts, you will likely want backup and desktop search to stay away from those partitions.


Sorry, I should have explained the commands.

chown : Change owner. "chown <username>:<groupname> <filename>" changes the owner of the file <filename> to <username>, and group of the file to <groupname>. I asked you to do "chown <username>:<username>" because by default Ubuntu creates a group with the same name as the user, and the user is the only member of this group. Run "man chown" for more information.

/etc/rc.local : When the system boots up, it starts various services (e.g. network), mounts all partitions in /etc/fstab, and does various startup tasks. It finally executes this file /etc/rc.local. All commands in this file get executed at the end of the boot process, with root privileges.

By running "chown <username>:<username> /dev/<partition>" , <username> becomes the owner of the partition device. Now adding "owner" as an option in /etc/fstab file makes <username> able to mount this partition without sudo.

---

### Post by ppttpp on 2008-06-04
Thanks bingo ...

mounting to /media worked like a charm

It even appeared in Dolphin and the KDE start menu by default with space left indicators too .. cool!! :guitar:

But again there is this same problem that it is owned to root.

So this is what I did:
I entered a console and I committed a
sudo chown usrname:username /media/D
sudo chown usrname:username /media/E
sudo chown usrname:username /media/F
sudo chown usrname:username /media/G

and now ls- l and my username is written as the proud owner of these folders which will be mounted on my four local partitions from now then.

Question: Will these ownerships return to root after the reboot .. or will they persist indefinitely?

Any mistake with this? I did not waddle into rc.local though .. what do you think?

---

### Post by bingoUV on 2008-06-04
Ownership of /media/D will not return to root after reboot. But if you change ownership/permissions of anything inside /media/D, I am not sure what will happen. No idea about how permissions and ownership in NTFS is dealt with when mounted in Ubuntu.

If you can read and write in your mounted partitions, it should work after reboot also.

---

### Post by ppttpp on 2008-06-04
Can't get what you are getting at? What makes you assume that my drives are NTFS? ;) :p

---

### Post by bingoUV on 2008-06-04
Sorry, I thought you are sharing partitions from existing windows installation so they must be NTFS. My bad.

It should work, without problems. If you do not get write permissions on some directory inside it, just chown it to your user. If you want some directory inside these partitions to be secure from tamperings of mere users, chown them to root.

---

