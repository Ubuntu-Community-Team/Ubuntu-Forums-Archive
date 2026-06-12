---
title: "External hard disk gone read-only"
date: 2007-12-07
forum: General Help
---

### Post by Roger D on 2007-12-07
Hi

I've a Western Digital My Book external hard disk - the file system is FAT32 and my OS is 6.06. It's worked reasonably well for over a year, but suddenly it's become read only. I can't add any new files to the disk, and I can't change the names of existing files and folders. There is nothing physically wrong with the drive - I've tested it in Windows XP, and it works.

Prior to this difficulty, I was having occasional problems getting the drive to appear on my desktop (mount). Following an earlier post to the Ubuntu forum I was advised that this was because I had failed to eject the drive properly. In /media, there were two entries for my drive: a file 'My' and a folder 'My Book'. Removing these, using 'rm' and 'rm -r', enabled the drive to appear on the desktop. Recently, I begun to suspect that this problem has been cropping up even when I had ejected the drive, but I can't be sure of this.

Now, when I look in /media, there is only the 'My Book' folder, and the 'My' file no longer appears. I don't know if this is relevant.

All help and adive much appreciated.

Roger D

---

### Post by viking777 on 2007-12-07
What do the file permissions and ownership say?

Go to a shell, cd to the external hard drive, and run sudo ls -l. The owner should be you and the permissions should be something like drwxr-xr-x.

If you are not the owner run 'sudo chown -R fred: /path to drive/' (substitute your user name for 'fred')

If the permissions don't include 'w' for user run:' sudo chmod u+w -R /path to drive/'

---

### Post by Roger D on 2007-12-07
Thanks for the reply. Here's the result of sudo ls -1

roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ sudo ls -l
total 36
lrwxrwxrwx  1 root  root      6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2007-03-13 12:41 cdrom0
drwx------ 11 roger roger 32768 1970-01-01 01:00 My Book
roger@roger-desktop:/media$

I think it says I'm the owner of My Book, and I have permission to write to this disk, so, seemingly, not much joy there.

---

### Post by stoodleysnow on 2007-12-07
Perhaps best to back up your data (you can still read it) and reformat with ext3 or jfs or something. FAT32 is... Proprietary.

---

### Post by geirha on 2007-12-07
What error message do you get when you try to copy something to it. Try with this command which should create an empty file on it:
```
touch /media/My\ Book/testfile.txt
```

Is there an entry for it in fstab? If so, how does it look? The following command should list such an entry, if any: ```
grep 'My Book' /etc/fstab
```

---

### Post by Roger D on 2007-12-07
Here's the first bit:

roger@roger-desktop:~$ touch /media/My\ Book/testfile.txt
touch: cannot touch `/media/My Book/testfile.txt': Read-only file system
roger@roger-desktop:~$ grep "My Book" /etc/fstab
roger@roger-desktop:~$


Here's fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Hope this tells you something

---

### Post by viking777 on 2007-12-07
> **Roger D said:**
> Here's the first bit:

roger@roger-desktop:~$ touch /media/My\ Book/testfile.txt
touch: cannot touch `/media/My Book/testfile.txt': Read-only file system
roger@roger-desktop:~$ grep "My Book" /etc/fstab
roger@roger-desktop:~$


Here's fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Hope this tells you something

It tells us that your device is not mounted through fstab - this is usual. It doesn't explain why it is read only though (at least not to me!). I did have this problem with a USB pen drive once and that was as a result of not unmounting it correctly. In that instance it didn't work in windows either though. Yours is working normally with windows you said including write permissions?

---

### Post by geirha on 2007-12-07
Let's try to mount it manually. That way we'll see any error messages it may give when we try to mount it in read-write mode.

Firstly determine which device node it's connected to. It's probably /dev/sdb1, but it could be something else. Running the following command while it's mounted should identify it.
```
mount | grep 'My Book'
```

Unmount it like you normally do, then mount it manually with:
```
sudo mkdir /media/My\ Book
sudo mount /dev/sdb1 /media/My\ Book
```
Whatever output it gives from the mount command may give us a good clue of what is wrong.

You'll need to unmount it with: ```
sudo umount /media/My\ Book
``` since the previous command mounted it as root.

Also, it might be some error in the filesystem, so if you have access to a windows machine, connect it to that and do a filesystem check on the usb-drive.

---

### Post by Roger D on 2007-12-07
Here's the output:

roger@roger-desktop:~$ mount | grep 'My Book'
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid =1000,gid=1000,umask=077,iocharset=utf8)
roger@roger-desktop:~$
roger@roger-desktop:~$ sudo mkdir /media/My\ Book
Password:
roger@roger-desktop:~$ sudo mount /dev/sbc1 /media/My\ Book
mount: you must specify the filesystem type
roger@roger-desktop:~$

Yes, I do have access to a Windows machine - that's how I know the drive is working -I'll give the filesystem check idea if the above isn't helpful.

Thanks for all your great help to date.

---

### Post by geirha on 2007-12-07
> **Roger D said:**
> roger@roger-desktop:~$ sudo mount /dev/sbc1 /media/My\ Book
mount: you must specify the filesystem type You specified the wrong device node here, it's /dev/sdc1 not /dev/sbc1.

The output of the "mount | grep 'My Book'" command above says it was mounted in read-write mode though (rw) as opposed to read-only (ro). That's odd.

---

### Post by viking777 on 2007-12-07
geirha,  

does Roger have  a problem with the umask option here?

My entry for my external hard drive looks like this:

/dev/sdb1 on /media/FREECOM HDD type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower)

note no umask.

The intricacies of umask are beyond my level of knowledge and I wouldn't know how to change it for a device either perhaps you might know if this is a problem?

EDIT Just did a bit of research on this and it seems that others with the same problem have solved it by plugging into a windows machine and running scandisk. It appears to be filesystem corruption that is causing it in the majority of cases, but since it is a windows file system the linux fsck command doesn't work too well.

It would be interesting to know why your umask option is 077 the default is 022 although 077 represents stronger security. Perhaps you require that. In any case it shouldn't stop the file owner from writing to it even at 077. If you are interested to see what your default umask option is you can run:

'cat /etc/profile'  in a terminal (minus quotes) and it is on the last line.

---

### Post by Roger D on 2007-12-07
Oops - sorry about that.

I tried again. I ejected the drive, using the drop-down menu - the drive icon disappeared from my desktop. Here my terminal output:

roger@roger-desktop:~$ mkdir /media/My\ Book
mkdir: cannot create directory `/media/My Book': File exists
roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ ls
cdrom  cdrom0  My Book
roger@roger-desktop:/media$

As I thought, this seems to indicate that the drive isn't unmounting properly using the drop-down menu

---

### Post by Roger D on 2007-12-07
You're not going to believe this, but for reasons I can't understand my drive is now working properly.

Thanks for all the advice and help. I'll think about running scandisk in Windows, and maybe ditiching FAT32.

---

### Post by viking777 on 2007-12-07
WHAT

After expending all that brain power you tell me that it just works!!!

My solicitor will soon be in touch with your solicitor:lolflag:

---

### Post by Roger D on 2007-12-07
It sure does - sorry about that. I just wish I understood what's been going onl

Best regards

Roger D

---

### Post by HermanAB on 2007-12-07
The filesystem type must be "-t vfat", so the full command is:
$ sudo mount -t vfat /dev/sdc1 /media/My\ Book

Read "man mount" for details.

and by the way - don't use spaces and save yourself a lot of hair.  Spaces are delimiters in Unix.

Cheers,

Herman

---

### Post by Roger D on 2007-12-07
Thanks Herman

If I run into trouble again, I'll remember this.
Don't understand your point about spaces. My drive is specified as "My Book", with a space between the 'y' and the 'B' in  media. I can't just start calling it MyBook, can I?

Roger D

---

### Post by Roger D on 2007-12-07
This is crazy

It's just gone read only again. I suspect that something is going wrong when I unmount/eject the drive using the drop down menus. Here's my terminal output - I did an eject before sudo mkdir

roger@roger-desktop:~$ mount | grep 'My Book'
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
roger@roger-desktop:~$ sudo mkdir /media/My\ Book
mkdir: cannot create directory `/media/My Book': File exists
roger@roger-desktop:~$

I'd just love to get to the bottom of this.

---

### Post by viking777 on 2007-12-08
Could it be to do with the way you are removing the drive? Do you have an option to 'safely remove' the drive rather than 'eject' it (which is something I associate with CD/DVD drives). If you don't you could always issue the command 

```
umount  /media/My\ Book
```

In a terminal to make sure it is unmounted before removing it or shutting down.

I have ruined a couple of USB pen drives by not unmounting them properly first (although I am not sure if USB hard drives are quite as vulnerable to that).

---

### Post by Roger D on 2007-12-08
Hi 
Many thanks for keeping an interest in my problem. I've just been through a pretty exhaustive test sequence, but I still can't see what's wrong. Here's what I did:

I started without my external hard disk or a usb stick plugged in. Here's the terminal output from running ls -l  on media and running the mount command:

roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-13 12:41 cdrom0
drwxr-xr-x 2 root root 4096 2007-12-07 20:04 My Book
roger@roger-desktop:/media$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-29-386/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
roger@roger-desktop:/media$


Now here's media and mount after external drives have been plugged in:

roger@roger-desktop:/media$ ls -l
total 52
lrwxrwxrwx  1 root  root      6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2007-03-13 12:41 cdrom0
drwx------ 12 roger roger 32768 1970-01-01 01:00 My Book
drwx------  2 roger roger 16384 1970-01-01 01:00 usbdisk
roger@roger-desktop:/media$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-29-386/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdc1 on /media/usbdisk type vfat (ro,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
roger@roger-desktop:/media$

I think this says My Book is read and write and mounted in the directory 'My Book, and my usb stick is also read and write and mounted in directory usbdisk. Both drives are owned by me, and have FAT32 file systems

However, when I try to write to My Book I get:

roger@roger-desktop:/media$ touch /media/My\ Book/testfile.txt
touch: cannot touch `/media/My Book/testfile.txt': Read-only file system

And when I try to do the same with my usb stick I get the same result:

roger@roger-desktop:/media$ touch /media/usbdisk/testfile.txt
touch: cannot touch `/media/usbdisk/testfile.txt': Read-only file system

I unmount both devices using the 'eject' option on the drop-down menus, both icons disappear from the desktop. Here's media:

roger@roger-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-13 12:41 cdrom0
drwxr-xr-x 2 root root 4096 2007-12-07 20:04 My Book

Next I try mounting My Book from the terminal using Herman's command


sudo mount -t vfat /dev/sdc1 /media/My\ Book

Drive appears on the desktop, but still read-only.

I thne unmount manually, and icon disappears from desktop.

As a last test,  I mount My Book manually, but it's still reaad-only.

So, for some reason, I can't save stuff to usb sticks or my external usb drive anymore. Is there anything in the above which indicates what's wrong?

If it could solve the problem, I'd be happy to abandon FAT32, changing to ext3. I could give this a try on the usb stick. but I don't know how to do it. Can you help?

Best regards

RogerD

---

### Post by viking777 on 2007-12-08
You have said that you started with the USB drive disconnected and yet when you run ls -l on /media/ you get the line:

drwxr-xr-x 2 root root 4096 2007-12-07 20:04 My Book

Which indicates that My Book is present and mounted and owned by root?? 

This can't be right, your USB stick is not present is it, neither should the drive be.

Here is the output of ls -l on my 'media' directory before I plug in the external drive:
```
lrwxrwxrwx  1 root   root      6 2007-11-17 19:12 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2007-11-17 19:12 cdrom0
drwxr-xr-x  2 root   root   4096 2007-11-22 11:40 disk
drwxr-xr-x 23 root   root   4096 2007-11-23 14:49 gutsy
drwxr-xr-x 22 root   root   4096 2007-12-06 10:03 hardy
drwxrwx---  3 graham graham 4096 1970-01-01 01:00 images
drwxrwx---  2 graham graham 8192 1970-01-01 01:00 othervm
drwxr-xr-x  3 graham graham 4096 2007-11-27 11:08 spare
drwxrwxrwx  1 root   root   8192 2007-11-21 17:08 windows_c
drwxrwxrwx  1 root   root   8192 2007-12-03 10:34 windows_d

```

And here it is again after I plug in and mount the drive:

```
lrwxrwxrwx  1 root   root       6 2007-11-17 19:12 cdrom -> cdrom0
drwxr-xr-x  2 root   root    4096 2007-11-17 19:12 cdrom0
drwxr-xr-x  2 root   root    4096 2007-11-22 11:40 disk
drwxr-xr-x  8 graham root   32768 1970-01-01 01:00 FREECOM HDD
drwxr-xr-x 23 root   root    4096 2007-11-23 14:49 gutsy
drwxr-xr-x 22 root   root    4096 2007-12-06 10:03 hardy
drwxrwx---  3 graham graham  4096 1970-01-01 01:00 images
drwxrwx---  2 graham graham  8192 1970-01-01 01:00 othervm
drwxr-xr-x  3 graham graham  4096 2007-11-27 11:08 spare
drwxrwxrwx  1 root   root    8192 2007-11-21 17:08 windows_c
drwxrwxrwx  1 root   root    8192 2007-12-03 10:34 windows_d

```

You see that the FREECOM drive is now present. That is how it should look. It certainly should not be there when it is not plugged in!

Here is what I would do. Unmount and unplug your drive and then open the /media/ folder and see what is in there. It looks to me as if you have created a folder called My Book in there which is owned by root this is almost certainly confusing things. I think you will have to get rid of this as it should not be there. You will have to be root to do this so:


```
sudo umount /media/My\ Book
```

Just to make sure then
```
 sudo rm -r /media/My\ Book
```

Then see what happens.

NB IMPORTANT> If you have some other drive called My Book as well as the USB one don't do this.

---

### Post by Roger D on 2007-12-08
As you say, there's an entry for My Book, owned by root. I try to umount this:

roger@roger-desktop:/media$ sudo umount /media/My\ Book
Password:
umount: /media/My Book: not mounted

Which is a bit strange.

roger@roger-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-13 12:41 cdrom0
drwxr-xr-x 2 root root 4096 2007-12-07 20:04 My Book

roger@roger-desktop:/media$ sudo rm -r /media/My\ Book
roger@roger-desktop:/media$ ls -l
total 4
lrwxrwxrwx 1 root root    6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-13 12:41 cdrom0

Finally, got rid of the My Book entry. I now plug my external hard disk in, as I understand things, it should mount automatically.

The icon appears on my desktop, but it's still read-only

As you can see:

roger@roger-desktop:/media$ touch /media/My\ Book/testfile.txt
touch: cannot touch `/media/My Book/testfile.txt': Read-only file system
roger@roger-desktop:/media$

---

### Post by viking777 on 2007-12-08
Sorry, I am all out of Linux type ideas now. 

You could stick it into your windows machine and run scandisk on it and see if it picks up any errors and if that doesn't work I guess your best bet might be to do as another contributor suggested and reformat. 

Gparted could do that for you but I have never used it for that purpose so I don't know how reliable it is. If you still have access to a windows machine you might be better doing it from there. In fact you could use the windows 'convert' command to convert the filesystem to NTFS that way you don't lose any data. Instructions here:

[http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)

or look for 'convert' in windows help menu.

I am not saying that will do it but if you have no other options it might be worth a try.

---

### Post by geirha on 2007-12-08
> **Roger D said:**
> 
roger@roger-desktop:/media$ sudo rm -r /media/My\ Book


CAREFUL! If your drive was mounted read-write there, you would have deleted all files on it. use "sudo rmdir /media/My\ Book" which will only remove the directory if it's empty, not all files contained inside it with it.

The /media/My\ Book dir was there because I told you to create it with "sudo mkdir /media/My\ Book". You see, in order to mount it manually, the directory to mount it to must exist allready. When you plug the drive in and let gnome decide to mount it, the directory will automatically be created, and removed when the drive is ejected.

The permissions on the directory itself is not important. When you mount something to it, the directory's permission will change to the permission of the filesystem you mounted there. Unmount it and they change back.

Hope that clarifies a bit.

From what I've read so far in the thread, I'm wondering, are there any switches or buttons on the usb-drive that could set the drive into write protected mode?

Could you also try to unplug your usb-drive then open a terminal and type ```
tail -f /var/log/syslog
```. Insert the usb-drive and there should pop up alot of lines in that terminal. Do you see anything that looks like an error message there? or any indication of why it doesn't mount it read-write?

Oh, and please use [code]-tags around output you paste from a terminal. Makes it a little easier to read.

---

### Post by Roger D on 2007-12-08
Thanks for all your help. I'm really at a loss what to do now too.

I don't really understand what is going on. When I do an eject, my hard disk icon disappears from my desktop, but I'm left with an empty directory, called My Book, in media and owned by root - is this what should happen?

Here's my terminal output:

roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-13 12:41 cdrom0
drwxr-xr-x 2 root root 4096 2007-12-08 13:47 My Book
roger@roger-desktop:/media$ cd 'My Book'
roger@roger-desktop:/media/My Book$ ls -l
total 0
roger@roger-desktop:/media/My Book$

I do have access to a Windows machine, but it's a bit of a let-down using Windows to sort out Linux - still, needs must, so I'll think about it.

Can I convert my drive to ext3 using Linux.

Best reg

---

### Post by geirha on 2007-12-08
> **Roger D said:**
> 
I don't really understand what is going on. When I do an eject, my hard disk icon disappears from my desktop, but I'm left with an empty directory, called My Book, in media and owned by root - is this what should happen?

Using eject is safe, it runs umount. The reason My Book is still there is because it was created with sudo mkdir eariler, which makes it owned by root, and cannot be removed automatically with your user. Whether there already is a directory there or not doesn't matter.

> **Roger D said:**
> 
I do have access to a Windows machine, but it's a bit of a let-down using Windows to sort out Linux - still, needs must, so I'll think about it.

Can I convert my drive to ext3 using Linux.

Well, FAT32 is created by microsoft, and is thus best supported in windows. That's why it's best to use windows to do a filesystem check on it. Converting to ext3 is not possible as far as I know. Not without losing all the data stored there allready. (Well, you can resize the fat partition, create an ext3, move some files over, then resize some more, move more files, until the fat partition is empty. Cumbersome though)

Using ext3 on an external usb drive is quite possible, but then you can't just plug it into any computer and read and write to it. Windows doesn't recognize ext3 out of the box, and there's a matter of permissions. In general, only use ext3 on external drives if you only intend to use the external drive on one computer. FAT32 is in most cases the best choice for external drives.

---

### Post by viking777 on 2007-12-08
As an aside to what geirha has just said, I have just done some experiments with a USB key, converting it to NTFS with windows 'convert' tool (which went fine) and then  plugging it into Linux - only to find that it could only be mounted by root whereas whilst it was Fat32 it could be mounted by a normal user, so I have changed my mind about NTFS, stick with Fat32 (and don't use ext3 as it is not compatible with windows and although you may not want to use it, in all probability most of your colleagues will be and you won't be able to read your usb key/disk on their computers - and you might want to do that one day).

EDIT I used Gparted to format it back to FAT32 and now it works normally again.

---

### Post by Roger D on 2007-12-08
OK, I think I'm beginning to understand the distinction between the directory 'My Book' and mounting my external drive in this directory. If all is working OK, I should be able to use 'rm -r 'My Book' to remove the empty 'My Book' directory, and then plug in my external hard disk; gnome should then create a new 'My Book' directory, and mount the drive in this directory. Selecting 'eject' from the pull-down menu should reverse this process, umounting the drive, and removing the directory.

This is what actually happens:

I plug in my drive, and the icon appears on my desktop. I click on one of the folders - as though to change a name, and I can see that this option is unavailable, i.e. the drive is read-only

Here's my terminal output:

'roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ ls -l
total 36
lrwxrwxrwx  1 root  root      6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2007-03-13 12:41 cdrom0
drwx------ 13 roger roger 32768 1970-01-01 01:00 My Book
roger@roger-desktop:/media$'

Which, as I understand things, is saying that I own 'My Book' and it's read-write. But it isn't.

Here's the teminal output after I eject the drive

'roger@roger-desktop:/media$ ls -l
total 4
lrwxrwxrwx 1 root root    6 2007-03-13 12:41 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-13 12:41 cdrom0
roger@roger-desktop:/media$'

Which is promising, at least there's no sign of 'My Book'

I turn off the power on my drive, and then switch it on again. Icon appears on my desktop, but still read-only. Do another eject, and, again, no sign of 'My Book'.

So the system seems to be ejecting OK, but my hard disk is being consistently mounted as read only.

As an experiment, I just tried the drive on my daughter's Windows laptop - it works fine, I can copy files to the drive without any problems. So it's not a matter of a switch setting on the drive.

Finally, I tried trail -f /var/log/syslog. Here's the result. There are a couple of lines with references to the file system being set to read only. Are these significant?

'roger@roger-desktop:~$ tail -f /var/log/syslog
Dec  8 15:42:50 localhost kernel: [17197765.196000] sd 8:0:0:0: Attached scsi di sk sdb
Dec  8 15:42:50 localhost kernel: [17197765.196000] sd 8:0:0:0: Attached scsi ge neric sg1 type 0
Dec  8 15:42:50 localhost kernel: [17197765.196000] usb-storage: device scan com plete
Dec  8 15:42:50 localhost kernel: [17197765.496000] FAT: utf8 is not a recommend ed IO charset for FAT filesystems, filesystem will be case sensitive!
Dec  8 15:42:50 localhost kernel: [17197765.556000] FAT: Filesystem panic (dev s db1)
Dec  8 15:42:50 localhost kernel: [17197765.556000]     fat_get_cluster: invalid  cluster chain (i_pos 0)
Dec  8 15:42:50 localhost kernel: [17197765.556000]     File system has been set  read-only
Dec  8 15:42:50 localhost kernel: [17197765.680000] FAT: Filesystem panic (dev s db1)
Dec  8 15:42:50 localhost kernel: [17197765.680000]     fat_get_cluster: invalid  cluster chain (i_pos 0)
Dec  8 15:46:31 localhost kernel: [17197986.068000] usb 2-1: USB disconnect, add ress 9
Dec  8 15:47:14 localhost kernel: [17198029.148000] usb 2-1: new high speed USB device using ehci_hcd and address 10
Dec  8 15:47:14 localhost kernel: [17198029.284000] scsi9 : SCSI emulation for U SB Mass Storage devices
Dec  8 15:47:14 localhost kernel: [17198029.284000] usb-storage: device found at  10
Dec  8 15:47:14 localhost kernel: [17198029.284000] usb-storage: waiting for dev ice to settle before scanning
Dec  8 15:47:19 localhost kernel: [17198034.316000]   Vendor: WD        Model: 8 00BB External    Rev: 0107
Dec  8 15:47:19 localhost kernel: [17198034.316000]   Type:   Direct-Access                  ANSI SCSI revision: 00
Dec  8 15:47:19 localhost kernel: [17198034.320000] SCSI device sdb: 156301488 5 12-byte hdwr sectors (80026 MB)
Dec  8 15:47:19 localhost kernel: [17198034.320000] sdb: assuming drive cache: w rite through
Dec  8 15:47:19 localhost kernel: [17198034.320000] SCSI device sdb: 156301488 5 12-byte hdwr sectors (80026 MB)
Dec  8 15:47:19 localhost kernel: [17198034.320000] sdb: assuming drive cache: w rite through
Dec  8 15:47:19 localhost kernel: [17198034.320000]  sdb: sdb1
Dec  8 15:47:19 localhost kernel: [17198034.324000] sd 9:0:0:0: Attached scsi di sk sdb
Dec  8 15:47:19 localhost kernel: [17198034.324000] sd 9:0:0:0: Attached scsi ge neric sg1 type 0
Dec  8 15:47:19 localhost kernel: [17198034.324000] usb-storage: device scan com plete
Dec  8 15:47:19 localhost kernel: [17198034.668000] FAT: utf8 is not a recommend ed IO charset for FAT filesystems, filesystem will be case sensitive!
Dec  8 15:47:20 localhost kernel: [17198034.736000] FAT: Filesystem panic (dev s db1)
Dec  8 15:47:20 localhost kernel: [17198034.736000]     fat_get_cluster: invalid  cluster chain (i_pos 0)
Dec  8 15:47:20 localhost kernel: [17198034.736000]     File system has been set  read-only
Dec  8 15:47:20 localhost kernel: [17198035.484000] FAT: Filesystem panic (dev s db1)
Dec  8 15:47:20 localhost kernel: [17198035.484000]     fat_get_cluster: invalid  cluster chain (i_pos 0)

Sorry, but what do code tags look like?

---

### Post by viking777 on 2007-12-08
'Invalid cluster chain' would say to me that it thinks the filesystem is corrupt. Run scandisk on it in windows with 'fix file system errors' checked. It may not do any good but it cant do any harm either.

If you are determined to do it in Linux run 

dosfsck -n /dev/sdb1

Which will check the disk but not fix any errors.

To fix them you would need

dosfsck -a /dev/sdb1

which fixes them automtically.

Look at 

man dosfsck 

for more details.

---

### Post by Roger D on 2007-12-08
OK

I plugged the drive into Windows XP and ran disk>properties>tools>error-checking, selecting both options. Restarted Linux, plugged in the drive, the disk icon appears, and a click on a folder indicates it's now read and write - great, real progress. Using nautilus, I copy and paste a file from my home directory into My Book - better still.

I eject My Book, have a look in media and 'My Book' isn't there - yet better still.

Repeat the whole process - just to be sure - and all is well.

Many thanks for everybody's  help. Have a good weekend, and a happy Christmas

Roger D

---

### Post by viking777 on 2007-12-09
HOORAY=D>=D>

Now I'll be able to sleep again:lolflag:

Good luck.

PS Don't forget to mark thread as SOLVED.

---

### Post by Roger D on 2007-12-09
HOORAY indeed.

How do I mark the thread as solved?

---

### Post by ellgor on 2007-12-09
Hi, If you are still having problems I have made a help which goes into alot of detail unfortunately, anyway its here if you want to use it, goodluck.


	      	The following aid is based on using Ubuntu, Dapper, 6.06 and the Gnome desktop with Nautilus manager.

Hi,


Step 1
	
	In order for the hard-drive etc. to interact with the computer, it needs its own space or office (in human terms) to operate from, this is what we will do here.

	Click on Places, from the drop down menu click on Home Folder, you should now have your Home Folder open in front of you.
	Right click anywhere on a blank space inside your Home Folder, from the drop down menu click on create folder.
	Right click on the new folder and from the pop-up menu select rename and do so with the name of your choice, now close your Home Folder.  
	

Step 2

	Click on System, from the drop down menu click on Administration,  from the drop down menu select Disks and the application starts up, you will be asked for your password to continue, do so and let the application finish loading.
	
When the application has loaded you should see a list of all attached drives etc. (Storage List) on the left side and a big open space on the right (Storage Properties) with a  Properties tag and a Partitions tag.
	
In the storage list select the drive you want to mount  (this is assuming you can identify it by size etc.) clicking on it will highlight it and some info will appear over in the Storage Properties side, presuming you have the right one, click on the Partitions tag and more options will be made available, namely, Format and Enable.
	
Under the new heading Partition Properties will be the Device: hdc1 or sda2 and so forth (make a physical note of the device name for later use) and right next to this is the format option.
	
Now, unless you want some data off it  don't do the following (go to Once the formatting), if the Status reads as Enable leave it, if it reads as Accessible, disable it, either way the Format option should be highlighted ready for use.
	
Click on the Format panel (I think it's default is the Ext3 type) and off it goes,  during the process you will be asked if you want to continue, go ahead,and unlike Window's, it's done in a few minutes.
	
Once the formatting is done the next thing is the Access Path, which might read at the moment as None, click on the box marked change and a new panel marked as Select New Mount Point Path should appear, and, that file you made earlier should be in the list to choose from, select it.
	
Lastly here, the Status should be changed to Accessible, do so, and for those who are wanting data back, use the browse option  ( if it says you are not allowed, or similar, follow the next part and then try again).

Step 3
	
	Because of the way the Linux system works, Root controls most of what goes on in the computer, now it would be nice if we the user also had a piece of that as well, we can, with this.

	Click on Applications, from the drop down menu click on Accessories, from the drop down menu click on Terminal and let the application start.
	Type in the following:-

	sudo chown “ YourUserName:YourUserName” don't include the quote marks /home /Your User Name/The name of the file you made

	which is the path to the file you made and should look like this, mine personally, me being Gordon and the file called  hardtwo

	sudo chown gordon:gordon /home/gordon/hardtwo

	I've put the username twice as this will stop Root from interfering as part of group.

	Also this to set the permissions type:-

	sudo chmod 777 /home/YourUserName/the name of the file you made

	If all has gone accordingly there will be no error messages and you can proceed, further use of your system will bring enlightenment as to the whys and wherefores of what was done , for now we want things to work.


Step 4 

	Because what we did previously was temporary we need to make it permanent  i.e. you will want it to auto load and be there at all times, we also need to make a copy of the original file and to do this we do the following.
	In your terminal  type in the following:-
	
	sudo cp /etc/fstab /etc/fstab.backup
	
	Which will copy fstab and be named backup(to differentiate) then type in
 
	sudo gedit  /etc/fstab    (Gedit is the default editor in Gnome) 

	You will see a new panel which lists the current state of drives etc. attached to your comp, use the arrow keys and come down to the bottom of the list ready to start a new line.

	The first part is to enter in the drive name/file system, this is the one from the Disk Manager which should be something like  /dev/hdc1 which if you look at the list is similar to the other entries, use the one I asked you to make a note of.
	
Done that, then leave a space and enter in the Pathname/mount point, which is /home/YourUserName/the file you made.
	Leave a space and enter the filesystem/type   ext3(or Ntfs etc)
	Leave a space and enter the options     defaults
	Leave a space and enter these two numbers with a space between 0 2 (don't ask)

	Your finished line should look like this:-

	/dev/hdc1 /home/gordon/hardtwo ext3 defaults 0 2 

	Everything done then close the window and you will be asked if you want to save it, do so and that's about it.

	To check things, open up your home folder and open up the file you made and click on properties (it may need a reboot to sort things out) you should be the Owner and Group with full permissions throughout.
	You should also see if the size matches what you put in and there will be a folder already in there called lost+found, its your folder.

	 Hope this helps, Regards Ellgor.

---

