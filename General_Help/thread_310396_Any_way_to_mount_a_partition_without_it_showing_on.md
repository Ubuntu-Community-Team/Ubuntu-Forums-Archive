---
title: "Any way to mount a partition without it showing on the desktop?"
date: 2006-12-01
forum: General Help
---

### Post by dbk927 on 2006-12-01
I'm running Ubuntu 6.06 Dapper, and when I boot up, my windows partition and a separate fat32 partition both mount and place icons on my desktop.  Is there any way to stop that from happening automatically?  I'm thinking its possible by editing fstab or something but I'm unsure how to do it.  Can anyone help me out with this one?

---

### Post by foofy on 2006-12-01
Try this:

> For example: sudo mount /dev/hda /home/foofy/Desktop

You can change the hda in the first path to whatever partition you want and the second path to where you want to mount it to.

In my example it will mount hda to the desktop.

Give it a try and give me a shout if it works.

---

### Post by bapoumba on 2006-12-01
Everything mounted in /media will show up on the desktop (ie your windows partition, but also usb drives, cdroms ...).

Just create another mount point 
**sudo mkdir /mnt** (for ex.)

backup your fstab file :
**sudo cp /etc/fstab /etc/fstab_bak**

edit /etc/fstab and change the windows partition mount point to the new one.  Will take effect next time you log in.

---

### Post by dbk927 on 2006-12-01
That worked perfectly, thank you both

---

### Post by JustDon on 2006-12-01
> **foofy said:**
> Try this:

For example: sudo mount /dev/hda /home/foofy/Desktop

You can change the hda in the first path to whatever partition you want and the second path to where you want to mount it to.

In my example it will mount hda to the desktop.

Give it a try and give me a shout if it works.

I have a similar problem. I have mounts named "Dell Utility", hda2 and hda3 on my desktop now. I want them to go away. If I understand correctly - I can open a terminal and do: 

sudo mount /dev/hda2/mnt

and that will cause hda2 to mount in the /mnt directory instead of my desktop?? Likewise I can substitute the other unwanted desktop mounts in the above command and do the same? Just want to make sure I understand completely before I do this.

Will this new modified mount point (/mnt) work each time I reboot or do I need to move them each time. Do I need to modify the fstab file still or does this above command do that for me?

---

### Post by koenn on 2006-12-01
read post #3 ...

---

### Post by JustDon on 2006-12-01
> **koenn said:**
> read post #3 ...

I'm asking because I can not perform post #3. I log in as root user, perform the prescribed entries and "save". I am then promptly informed that fstab is "read only" and cannot be saved with my modification. Any further suggestions?

---

### Post by bapoumba on 2006-12-01
@ JustDon : what is the output of **cat /etc/fstab** ?

---

### Post by JustDon on 2006-12-01
> **bapoumba said:**
> @ JustDon : what is the output of **cat /etc/fstab** ?

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by JustDon on 2006-12-01
Actually, for whatever reason I tried again:

sudo gedit /etc/fstab

and was successful. Now my hda2 and hda3 mounts are moved from my desktop to the /mnt directory. BUT I still have a mount on my desktop named "Dell Utility" that I cannot move to trash, open, access or unmount due to permissions. It matters not if I log in a root or user, I cannot modify this mount. Any ideas on this one? Also, how might I actually mount hda2 and hda3 to access files that are on them while in Ubuntu?

---

### Post by strabes on 2006-12-01
that's the hidden partition that dell includes with its computers so when windows dies on people, they can fix it. Can you boot from the live CD and delete the partition then resize the others?

---

### Post by JustDon on 2006-12-01
> **strabes said:**
> that's the hidden partition that dell includes with its computers so when windows dies on people, they can fix it. Can you boot from the live CD and delete the partition then resize the others?

Actually, I don't even know where I found it now BUT "DellUtility" is actually a partition called hda1, which I was able to gedit /etc/fstab to move to /mnt.

So, my desktop is clean but I still can't access any of these partitions. When I navigate to /mnt, I cannot even open the folder... 

How can I fix this? It would be nice to be able to get into my files that are on my Windoze partition (music, word docs, etc.)

---

### Post by futz on 2006-12-01
> **bapoumba said:**
> Everything mounted in /media will show up on the desktop (ie your windows partition, but also usb drives, cdroms ...).

Just create another mount point 
**sudo mkdir /mnt** (for ex.)

backup your fstab file :
**sudo cp /etc/fstab /etc/fstab_bak**

edit /etc/fstab and change the windows partition mount point to the new one.  Will take effect next time you log in.
If you don't want mounted devices to show up on the desktop, but don't feel like changing mount points, use gconf-editor. It shows up in the Applications/System Tools menu as Configuration Editor. Has an icon of a little red car with the hood up and a wrench. If you don't have it installed, a quick trip to Synaptic will fix that.

In gconf-editor, navigate to apps/nautilus/desktop and you can check/uncheck boxes for what gets displayed on the desktop. **volumes_visible** is the one for mounted drives.

---

### Post by futz on 2006-12-01
> **JustDon said:**
> Actually, I don't even know where I found it now BUT "DellUtility" is actually a partition called hda1, which I was able to gedit /etc/fstab to move to /mnt.

So, my desktop is clean but I still can't access any of these partitions. When I navigate to /mnt, I cannot even open the folder... 

How can I fix this? It would be nice to be able to get into my files that are on my Windoze partition (music, word docs, etc.)
Most likely you need to set ownership and permissions on your /mnt/hda1 directory so you're allowed to access it. Set file ownership to you, the user, instead of root and set permissions to 755. I usually start a root nautilus with "gksudo nautilus" to do this job, since I can never remember how to do it in the command line.

---

### Post by JustDon on 2006-12-01
OK, I'm lost. I did:

sudo gedit /etc/fstab

I modified the mount points on hda1, hda2 and hda3 to /mnt. The problem is that I (as user) have no access to /mnt. SO - I modified fstab again and moved the mount points to /home/hda1, /home/hda2, and /home/hda3. I restarted and when I navigate to the /home files I see the hdaX folders but they are empty.

The actual hda1, 2 and 3 icons (little drive looking gizmos) are in /dev and have a little "lock" symbol to the upper right of each one. I right click on them pick "properties" and they are owned by "root", PLUS "root" does NOT have "execute" authority either. Obviously no one can access these partitions. How do I modify the properties on each of these such that I can access them as "user"?

When I ran "gksudo nautilus" as prescribed a couple of replies ago I only have two things in the "root" folder and neither of them have to do with these partition mounts. I also get this crazy message:

[COLOR="Blue"]**dhatcher2@dhatcher2-desktop:~$ gksudo nautilus**[/COLOR]

[COLOR="Red"](nautilus:6377): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

** (nautilus:6377): WARNING **: No description found for mime type "x-special/de vice-block" (file is "hda1"), please tell the gnome-vfs mailing list.

(nautilus:6377): Eel-WARNING **: Error starting command ''/dev/hda1'': Failed to  execute child process "/dev/hda1" (Permission denied)

(nautilus:6377): Eel-WARNING **: Error starting command ''/dev/hda2'': Failed to  execute child process "/dev/hda2" (Permission denied)


(nautilus:6377): Eel-WARNING **: Error starting command ''/dev/hda3'': Failed to  execute child process "/dev/hda3" (Permission denied)[/COLOR]

No clue where to go now...

---

### Post by futz on 2006-12-01
> **JustDon said:**
> OK, I'm lost. I did:

sudo gedit /etc/fstab

I modified the mount points on hda1, hda2 and hda3 to /mnt. The problem is that I (as user) have no access to /mnt. SO - I modified fstab again and moved the mount points to /home/hda1, /home/hda2, and /home/hda3. I restarted and when I navigate to the /home files I see the hdaX folders but they are empty.
If they're empty then the drives aren't being mounted properly (or there's nothing on the drives).


> The actual hda1, 2 and 3 icons (little drive looking gizmos) are in /dev and have a little "lock" symbol to the upper right of each one. I right click on them pick "properties" and they are owned by "root", PLUS "root" does NOT have "execute" authority either. Obviously no one can access these partitions. How do I modify the properties on each of these such that I can access them as "user"?
Don't mess with stuff in the /dev directory. That's not for you to play with.


> When I ran "gksudo nautilus" as prescribed a couple of replies ago I only have two things in the "root" folder and neither of them have to do with these partition mounts. I also get this crazy message:

[COLOR="Red"][B](nautilus:5921): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B][/COLOR]

Not sure where to go from here...
Ignore the warning. It's harmless.

When you start a root nautilus like that, you should get a view of your file structure exactly the same as starting a non-root nautilus. It may start out in a different directory, but then you simply navigate to the desired directory, right click and select Properties/Permissions. Change ownership of your mount point directory (/home/hda1, etc) to your username (from root). Owner gets read/write/execute permission. Group gets read/execute permission. Others get read/execute permission. That's 755.

---

### Post by bapoumba on 2006-12-02
> **futz said:**
> 
In gconf-editor, navigate to apps/nautilus/desktop and you can check/uncheck boxes for what gets displayed on the desktop. **volumes_visible** is the one for mounted drives.
Yes, I do agree with that, but cds, dvds, usb devices and such will not show up on the desktop anymore. This is why I always favor mounting other partitions to some other mounting file, so that you can still access them, but won't see them on the desktop.

@ JustDon : please post your current fstab file (**cat /etc/fstab**)

---

### Post by JustDon on 2006-12-02
> **bapoumba said:**
> Yes, I do agree with that, but cds, dvds, usb devices and such will not show up on the desktop anymore. This is why I always favor mounting other partitions to some other mounting file, so that you can still access them, but won't see them on the desktop.

@ JustDon : please post your current fstab file (**cat /etc/fstab**)

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /home/dhatcher2/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /home/dhatcher2/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       /home/dhatcher2/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Actually, everything is working perfectly now. I can access hda2, which is my Windows XP partition. I can play my music (coutesy VLC Media Player, which plays WMA files nicely). Thanks for all of your help. I had the mount point set up as /home/hda2 and the directory was actually in /home/dhatcher2/hda2, my own oversite. Your help was most valuable!

---

### Post by bapoumba on 2006-12-02
Welcome :)
Just keep in mind that writing on ntfs partition is somewhat ... experimental ;)

---

### Post by strabes on 2006-12-02
Justdon: did you sudo mkdir /mnt/yourdirectory? You have to manually create the directories when moving mount points. I would also like to reemphasize bapoumba's point, which is that writing to ntfs is still experimental. I've heard some good things about ntfs-3g though. Try it if you want. That dell partition is useless anyway.

---

### Post by futz on 2006-12-02
> **bapoumba said:**
> Yes, I do agree with that, but cds, dvds, usb devices and such will not show up on the desktop anymore. This is why I always favor mounting other partitions to some other mounting file, so that you can still access them, but won't see them on the desktop.

@ JustDon : please post your current fstab file (**cat /etc/fstab**)
Well, that's just a matter of taste. I hate my desktop cluttered with crap like that, and almost always have nautilus running somewhere, so I know what's mounted anyway. Each to his own... :)

---

### Post by bapoumba on 2006-12-02
> **futz said:**
> Each to his own... :)
Absolutely ;)

---

