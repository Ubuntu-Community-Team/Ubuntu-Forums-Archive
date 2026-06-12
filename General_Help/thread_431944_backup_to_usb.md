---
title: "backup to usb?"
date: 2007-05-03
forum: General Help
---

### Post by Bashed on 2007-05-03
I'm trying to move files to my usb flash drive but it keeps telling me no permission. 

How do I create a folder on my usb drive via command line AND drag/drop via places > usb?

---

### Post by justin whitaker on 2007-05-03
Just right click on the USB drive and change the access permissions. 

Hmmmm, you might need to be root to do that. What I do is fire up a terminal, login as root, type in nautilus, then right click and change the permissions. 

Sure, you can chmod it...but I am LAZY. :) :)

---

### Post by Bashed on 2007-05-03
What am I doing wrong here?

chad@Secured:~$ su -
Password: 
su: Authentication failure
Sorry.
chad@Secured:~$ su
Password: 
su: Authentication failure
Sorry.

---

### Post by Bashed on 2007-05-03
Ok I need some command correction here too :)

root@Secured:/home/chad# ls
1  amsn_received  avant-window-navigator  Desktop  Febe  google-earth  Music
root@Secured:/home/chad# cp /Febe/ /media/Backup/
cp: target `/media/Backup/' is not a directory: No such file or directory


How do I copy Febe directory entirely to my usb drive (Backup is the title)?

I'd rather do a drag/drop too but it doesn't seem to work as I already mentioned

---

### Post by kub-fu on 2007-05-03
First, I don't think you can use su on Ubuntu since I believe there's no root user per se... You use either sudo or kdesu (on Kubuntu, for GUI programs) to run something with root permissions.

You can also run sudo bash to open a console session with root permissions.

As for your drive, you have to create the mount directory as root and assign it r/w access to everyone, so when you mount it you can access it without root permissions. This is what I do:

$ sudo mkdir /media/Backup
$ sudo chmod a+w /media/Backup
$ sudo mount /dev/sdh1 /media/Backup
$ cp -R ~/Febe /media/Backup

/dev/sdh1 changes accordingly to your system.

I'm no expert at this, but I hope that helps.

---

### Post by kub-fu on 2007-05-03
I think I might made an error there... if that doesn't work, you might want to edit /etc/fstab before running the mount command... try my previous reply first and if it doesn't work I'll tell you what to try next.

---

### Post by justin whitaker on 2007-05-03
> **TalkJesus said:**
> What am I doing wrong here?

chad@Secured:~$ su -
Password: 
su: Authentication failure
Sorry.
chad@Secured:~$ su
Password: 
su: Authentication failure
Sorry.

Did you set a separate ROOT password?

sudo passwd

Then it will ask you for your sudo password, then assign a new Root password.

---

### Post by ajgreeny on 2007-05-03
USB thumb drives are usually mounted as user mounted, not root, so I'm not sure what is going on here.  You ought to be able to write to it without problems as a user and it shouldn't need root access to do it. Are you simply plugging it in and trying to write, or are you mounting it with a sudo command in the terminal first?

---

### Post by Bashed on 2007-05-03
I simply plug in the usb drive and it mounts itself as "Backup" as that is the title I input in Windows for it.

Now, I cannot right to it at all no matter what I do.

Any suggestions?

---

### Post by justin whitaker on 2007-05-03
> **ajgreeny said:**
> USB thumb drives are usually mounted as user mounted, not root, so I'm not sure what is going on here.  You ought to be able to write to it without problems as a user and it shouldn't need root access to do it. Are you simply plugging it in and trying to write, or are you mounting it with a sudo command in the terminal first?

Usually that is true, but I recall having issues with Edgy where my external USB drives where mounted as Root instead of user. That does not happen in Feisty anymore...but that explains why I was non-plussed. :)

---

### Post by justin whitaker on 2007-05-03
> **TalkJesus said:**
> I simply plug in the usb drive and it mounts itself as "Backup" as that is the title I input in Windows for it.

Now, I cannot right to it at all no matter what I do.

Any suggestions?

TalkJesus, which version of Ubuntu are you using? UbuntuCE? 6.06?

---

### Post by Bashed on 2007-05-03
Then why is it happening to me? I'm using Feisty Fawn official release

---

### Post by Bashed on 2007-05-03
I tried another usb flash drive I have and it mounted as root as well.

Does this have anything to do with it being ntfs format?

---

### Post by jerrylamos on 2007-05-03
USB backup
Well in Applications, Accessories, Terminal I do:
df -h 
to see what device the USB is.  It can be /dev/sda1 or /dev/sdb1 or something else.  Then
sudo umount /dev/sdb1
or whatever the device name is.  
Now is the tricky part.  You absolutely have to get the device name right because this is a device format which wipes the device clean and takes a little while:
sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sdb1
If you goof up here you can wipe out your hard drive......I have.....don't say I didn't warn you.
Now when I boot there's an icon casper-rw on the desktop.
To backup home, I do Applications, Accessories, Terminal
sudo cp -au * /media/casper-rw
This will get home if that's where you were, and all subdirectories including Desktop.
It copies files but doesn't replace unless the file date is newer.
If you don't want subdirectories, then
sudo cp -dpu * /media/casper-rw

You can use a different label, that's just the one that Edgy and Dapper use for CD Live "persistent" mode which is broken on Feisty.

Cheers, Jerry

---

### Post by Bashed on 2007-05-06
I really need help here. I can't figure this out for the life of me

chad@Secured:~$ sudo mkdir /media/Backup
Password:
chad@Secured:~$ sudo chmod a+w /media/Backup
chad@Secured:~$ sudo mount /dev/sdb1 /media/Backup
mount: /dev/sdb1 already mounted or /media/Backup busy
mount: according to mtab, /dev/sdb1 is mounted on /media/Backups

---

### Post by strabes on 2007-05-06
To get into a root terminal session you can just do "sudo -i"

```
sudo umount /dev/sdb1
sudo mount /dev/sdb1 /media/Backup
sudo chmod -R a+rw /media/Backup
```

---

### Post by wearekosh on 2007-05-06
Could it be you are encountering several problems at once?

one may be......
I had a similar problem writing to my usb drive.
The problem was the USB drive was formated and given a 'Volume' name when it was plugen into a windows PC.
I plugged it into a windows machine again and removed the 'Volume' name and it all work ok.
(I also use NTFS-3G to write to the drive)

---

### Post by Bashed on 2007-05-06
> **strabes said:**
> To get into a root terminal session you can just do "sudo -i"

```
sudo umount /dev/sdb1
sudo mount /dev/sdb1 /media/Backup
sudo chmod -R a+rw /media/Backup
```

Doesn't work. First, not sure why your telling me to umount (when I already showed it was automatically mounted) then mount it.

But when I run the chmod command, I get this for each file on the USB

Read-only file system

---

### Post by Bashed on 2007-05-09
Trying to install systemimager from this link (auto script) but it won't work
[http://wiki.systemimager.org/index.php/Quick_Start_HOWTO#Download_the_required_packages](http://wiki.systemimager.org/index.php/Quick_Start_HOWTO#Download_the_required_packages)

```
chad@Secured:~/systemimager$ ./install -v --download-only --tag stable --directory . systemconfigurator \ systemimager-client systemimager-common \ systemimager-i386boot-standard systemimager-i386initrd_template \ systemimager-server \ systemimager-bittorrent systemimager-flamethrower
Using pre-existing package list: ./stable.list
Downloading: http://dl.sourceforge.net/sourceforge/systemconfig/systemconfigurator-2.2.9-1.noarch.rpm...done!

ERROR: package " systemimager-client" does not exist in ./stable.list


```

I also installed ntfs-3g via Synaptic, then rebooted. I still get the same error "do not have permission" to write to usb.

---

