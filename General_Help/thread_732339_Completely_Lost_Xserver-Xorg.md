---
title: "Completely Lost Xserver-Xorg"
date: 2008-03-22
forum: General Help
---

### Post by rahduke on 2008-03-22
Thread Name is incorrect it should read: Completely lost Access to Xserver-xorg

please help, big problems:

after a ctrl+alt+bksp fiasco i lost access to xserver, I get the following error when trying to boot ""Could not start Xserver due to some install error, contact system admin restart when problem corrected"..... so far i have tried to reconfigure xserver via  dpkg-reconfigure xserver-xorg in diagnostic boot..... needless to say it didnt work

Everything was working fine for over a month. I've been trying our a few First Person Shooters today.  I might have ctrl+alt+bksp to many times or something.

Right now i'm on a Live CD, 

I have: 

onboard intel945g graphics.
Gutsy Gibbon

---

### Post by tvtech on 2008-03-22
is the xorg.conf file still there? 

/etc/X11/

---

### Post by rahduke on 2008-03-22
thanks for the quick response.... Yes xorg.conf is there along with 18 other xorg.conf files that are labeled like "xorg.conf.16"

---

### Post by Rocket2DMn on 2008-03-22
Here is how you can reconfigure X - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you need further help, post
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

### Post by rahduke on 2008-03-22
we'll Ive tried reconfiguring xserver several times with no success.  It doesn't automatically detect my onboard intel945graphics "card". I get the following error: 

"No Xserver found for your video hardware or "discover" program unable to determine which xserver is compatible with your card"

Any help would be appreciated...


btw

is there a way to re-install xserver?

Rocket2DMn I'm not sure what:


cat /etc/X11/xorg.conf
lspci | grep VGA


Is can you be more specific

---

### Post by Rocket2DMn on 2008-03-22
The method I listed doesn't use autodetection - you have to answer the questions yourself, during which you would select the "intel" driver.  i.e. you don't use the -phigh flag.
You can try reinstalling xserver-xorg-core or all of ubuntu-desktop (the GUI stuff)
Get to a TTY, not recovery kernel, so you have internet access (try CTRL+ALT+F1 from where you can't get into the GUI)
```
sudo apt-get install --reinstall xserver-xorg-core
```
Try that first, but you can try doing all the GUI stuff and programs that come with it (this should much larger)
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by rahduke on 2008-03-22
I get the following error when i try that:

root@rahduke-desktop:~# sudo apt-get install --reinstall xserver-xorg-core

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to wire to /var/cahce/apt
E: The package lists or status file could not be parsed or opened.


Thanks so much for your help so far :)

And when I try to reconfigure xorg after using Alt+Tab+F1 on black screen it freezes and does not allow me to do anything, I have to reset completely

---

### Post by Rocket2DMn on 2008-03-22
Read only lock file?!?
Please post
```
ls -l /var/lib/dpkg/lock
```
The command isn't Alt+Tab+F1, it's CTRL+ALT+F1.
FYI, from the recovery terminal, sudo is not be necessary since you already have root privileges.
Then do
```
(sudo) dpkg --configure -a
```
and post
```
ls -l /var/lib/dpkg/lock
``` so we can see if it changed.

---

### Post by rahduke on 2008-03-22
OK:

root@rahduke-desktop:~# ls l /var/lib/dpkg/lock

-rw-r----- 1 root root 0  Mar 22 18:46 /var/lib/dpkg/lock


then when i try to configure dpkg it says:

root@rahduke-desktop:~# sudo dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only filesystem


and obviously i get the same result when i rerun " ls l /var/lib/dpkg/lock"

p.s.

when i wrote alt+tab+F1 earlier it was a typo... I meant ctrl+atl+F1

I'm real sorry I can't be more help I'm practically brand new to linux cmd's just switched from windows :(

---

### Post by rahduke on 2008-03-22
Attached is my current xorg.conf file

---

### Post by Rocket2DMn on 2008-03-22
Ahhhh, I think I see what is going on - your partition is mounting as read only.  Can you please post
```
cat /etc/fstab
mount
(sudo) fdisk -l
``` (that's a lowercase L).

---

### Post by rahduke on 2008-03-22
Ok this is alotta stuff:

**cat /etc/fstab **

# Entry for /dev/sda1 :
UUID=536e063f-eac1-42ef-953f-d69855ffe70 / ext3 defaults,errors=remount-ro 0 1
#Entry for /dev/sda5 : 
UUID=9abccb33f-f3ef-4b9c-9811-046419951d912 none swap sw 0 0 

**Mount**

/dev/sb1 on type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on sys type sysfs (rw,noexec,nosuid,nodev)
vavrun on vav/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
undev on /dev type tmpfs (rw,mode=0755)
devshm on dev/shm/type tmpfs (rw)
devpts on dev/pts type devpts (rw,gid=5,mode=620)
nfsd on proc /proc/fs/nfsd type nfsd (rw)
binfmt_misc on proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


**sudo fdkisk -l** (abbreviated)

Disk /dev/sda: 120 GB   (separate IDE windows Drive)

Disk Identifier: 0x1e1b1e1a

Device      Boot           Start          End                     ID            System
/dev/sda1  *                 1          14592                      7              NTFS


Disk /dev/sdb 400.0 GIG  (SATA Linux drive)
Disk Identifier: 0x00069197]

Device      Boot           Start          End                     ID            System
/dev/sbd1  *                 1           48267                   83              Linux
/dev/sdb2                 48268       48641                    5              Extended
/dev/sbd5                 48268       48641                   82          Linux swap / Solaris


Hope this helps!!

---

### Post by Rocket2DMn on 2008-03-22
OK, well that turned out not to tell me anything extremely useful.  So, this is what I want you to try:
First, we're going to add an option to your fstab file.  I want you to add the "noatime" option to your root filesystem by rebooting into the recovery kernel (the second option at the GRUB menu) and running
```
nano /etc/fstab
```
and changing the line 
```
UUID=536e063f-eac1-42ef-953f-d69855ffe70 / ext3 defaults,errors=remount-ro 0 1
```
to
```
UUID=536e063f-eac1-42ef-953f-d69855ffe70 / ext3 defaults,errors=remount-ro**,noatime** 0 1
```
I have made the change in bold, don't touch the other stuff.  Save and close with CTRL+X.
Now we're going to force a file system check on the next reboot by running
```
touch /forcefsck
```
Then reboot
```
reboot
```
Chooes your normal option at the GRUB screen and let it run its test.  Let me know if it  gives you any errors (or if it doesn't even run the test).  Also let me know if the problem is fixed.

---

### Post by rahduke on 2008-03-22
I can't save the change:

[ Error writing /etc/fstab:  Read-only filesystem ]


thanks for sticking with me :)

if possible IM me at rahduke2 on AIM....

---

### Post by Rocket2DMn on 2008-03-23
OK, you should be able to do this from the LiveCD (but you don't have to if you're not in it any more)
I need you to *look at* the output of
```
ls -l /dev/disk/by-uuid/
```
Does it match "536e063f-eac1-42ef-953f-d69855ffe70" for ../../sdb1 ?
That is the UUID listed for your root partition, as noted in your fstab file.  It seems like you added the NTFS drive later (or did other drive configuration), since fstab's comments say your root partition is on sda1, when it's actually on sdb1, as seen from the fdisk command.  Either way, that's one of the advantages of using UUIDs - the /dev location is less relevant :)
If the UUID doesn't match, then that means you will need to fix fstab, which can be done from the LiveCD.
As a side note, I don't remember if sudo/gksudo is needed when using the LiveCD, so I've included them below, but if you can do without them, then groovy.  You can clear it up for me when you respond :)
Mount your root partition with 
```
sudo mkdir /media/driveroot
sudo mount -t ext3 /dev/sdb1 /media/driveroot
```
Then edit fstab:
```
gksudo gedit /media/driveroot/etc/fstab
```
and replace
```
UUID=536e063f-eac1-42ef-953f-d69855ffe70 / ext3 defaults,errors=remount-ro 0 1
```
With
```
**/dev/sdb1** / ext3 defaults,errors=remount-ro**,noatime** 0 1
```

Since you're already in the LiveCD, we will run the disk check from there.  Make sure your root partition is unmounted first:
```
sudo umount /dev/sdb1
```
Then run
```
fsck /dev/sdb1
```
If you get errors, let me know.  After all this jazz, reboot normally and see if you can get it in.  Good luck.

---

