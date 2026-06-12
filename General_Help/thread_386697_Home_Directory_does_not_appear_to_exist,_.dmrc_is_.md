---
title: "Home Directory does not appear to exist, .dmrc is being ignored"
date: 2007-03-17
forum: General Help
---

### Post by zhabib on 2007-03-17
I was trying to give my self access to put some files into /home . after reading some instructions on for these forums i attempted to execute it.
After entering some commands in the terminal, which did not work, i  restarted. upon restarting and attempting to log in i was faced with the following error

"
 Your home directory is listed as: '/home/zhabib' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session"
after pushing yes i was prompted with this error
"  User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users."

Then AFTER that came
"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem"


the ~/.x session_errors file had these 2 errors

(gnome-session:4605): libgnomevfs-warning **: Unable to create ~/.gnome2 directory: Permission denied

and 

could not create per_user gnome configuration directory 'home/zhabib/.gnome2/": Permission denied



After this, i searched these forums for a while and came back with 3 methods to try.

1st was

chmod 644 /home/zhabib/.dmrc



then

chown -R zhabib /home/zhabib
chmod 644 /home/zhabib
chmod 644 /home/zhabib/.dmrc


then

sudo mkdir -m 755 /home/zhabib
sudo chown zhabib:zhabib /home/zhabib



after i tried the 1st, i tried to login, same errors, same with the next 2.

could anyone please tell me what i need to do fix this?

thanks.
zhabib

---

### Post by hal8000 on 2007-03-17
I have a feeling that your /home partition has not been mounted,dont panic yet, this is recoverable.
First you need to state what partitions you made during install, there would have been at least a / and /swap and possibly even a /home.

As root from a terminal can you first post back the output of

df -hT

Example lines below
anc@ubuntu:~$ df -hT
Filesystem Type    Size Used Avail Use% Mounted on
/dev/hda11          reiserfs    6.1G  2.1G  4.0G  35% /
/dev/hda12          reiserfs    2.1G   79M  2.0G   4% /home
/dev/hda1           ntfs     59G   45G   15G  76% /media/hda1




and then the partitions as seen by fdisk, like this

fdisk -l /dev/hda

(I am assuming that hda is your hard drive, it will be shown by  df see my example, above) 
OK, thats l as in "list" not one or pipe.

---

### Post by zhabib on 2007-03-18
..

---

### Post by zhabib on 2007-03-18
so df -hT gave me this:
(i omitted some of the fields for convenience)

File system  Type  size       used    Mounted on
/dev/sda5  ext3    12g      3.1G         /
varrun       tmpfs   248M   76k         /var/run
varlock      tmpfs   248M   0            /var/lock
procbususb usbfs  10M     132K       /proc/bus/usb
udev         tmpfs  10M     132K      /dev
devshm     tmpfs   248M   0            /dev/shm
lrn            tmpfs   248M   18M      /lib/modules/2.6.17-11generic/volatile
/dev/sda1 vfat      7.0G    4.4G     /media/sda1
/dev/disk/by-uvid/CAB4E1CBB4E1B9D9 fuse 150G 117G /media/sdb1
/dev/sda2 fuse     118G    87G      /media/PRESARIO


fdisk for sda5 showed

Disk /dev/sda5:12.9GB, 12951396864
255 Heads, 63 sectors/track, 1574 cylinders.
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk /dev/sda5 doesn't contain a valid partition table.


I shouldve mentioned this before
but when I entered sudo mkdir -m 755 /home/zhabib into  the terminal it said the directory already existed.

---

### Post by peabody on 2007-03-18
> **zhabib said:**
> I was trying to give my self access to put some files into /home . after reading some instructions on for these forums i attempted to execute it.
After entering some commands in the terminal, which did not work, i  restarted. 

Do you have any recollection of what the commands were, or what they might have looked like?

---

### Post by kopilo on 2007-03-18
*delete* ohh wait you've tried that.

---

### Post by zhabib on 2007-03-18
no recollection whatsoever. if i could somehow access my history i would tell you, but since i cant login i dont think ill be able to.

---

### Post by zhabib on 2007-03-19
help
anyone?
please?

---

### Post by 289Shelby on 2007-03-19
I can't help with the first part of your problem but I had exactly the same problem with the .dmrc file after I had messed something up. Have a look here and see if it helps:

[http://kubuntuforums.net/forums/index.php?topic=3080910.0](http://kubuntuforums.net/forums/index.php?topic=3080910.0)

One thing I noticed is that the error msg said to make the .dmrc file 644 that did not work for me and I had to do 600

Hope this may be of some help.

---

### Post by rewrittenfromscratch on 2008-05-17
I have received this same error myself on attempting to login. Unfortunately, I can't trace back exactly what would have caused it. I haven't installed any new packages or attempted to alter my install at all, and have been running Hardy without a hitch since Alpha 6.

I have been keeping up with all updates, and in fact, I think the last thing I did before rebooting that last time was to install updates.

I can't imagine installing standard Synaptic updates would somehow corrupt my home folder or do some other bizarre thing to cause this error, but all I've done for weeks is update; other than that, nothing's been changed.

Furthermore, I've since been booting into Windoze (dual-boot), which previously had the ability to read my Linux partitions (a very worthwhile program for dual-booting). Now, when I try to access the Linux partitions from Windoze, it informs me that the partitions need to be formatted. Also, as I imagine this is a question that might come up, no, I hadn't used Windows to alter anything in my Linux partitions; I haven't used Windows in months, and when I did view my Linux partitions, I only viewed - no editing.

---

