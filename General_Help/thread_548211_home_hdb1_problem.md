---
title: "/home hdb1 problem"
date: 2007-09-11
forum: General Help
---

### Post by American_Outcast on 2007-09-11
I first used gparted on the Ubuntu 7.04 live CD. I wanted to resize my hdb drive which had three partitions. The first partition is my /home. Ok, this didn't work well. After I deleted hdb2 and hdb3 I resized hdb1 to fill in the 76gb drive. I got an error message and it looked like it wiped the whole drive. 

So I booted the installed Ubuntu 7.04 hoping that it was just a weird bug. Well in part it was. All my files where there and it booted normally. So just for the hell of it I checked to see how much space is being used, it was saying around 50GB... that was wrong.

So I decided to copy my /home/myfolder to my back up Sata and I was going to reformat hdb and just copy that folder back. But.....

When I copied it the coping window said it was copying around 17217 files. When I right click /home/myfolder it is 5.6GB. So I waited until it was finished and checked both the original folder and then the copy I made on the sata drive:

/home/myfolder - 4991 items, totalling 5.6 GB
sata copy - 1561 items, totalling 5.6 GB

Note that the size is the same but the items numbers are different. Both are different then what the copy window said, which was 17217 files.

I am lost here on what to do. I don't want to loose my /home/myfolder or have to reinstall Ubuntu, etc. Does anyone know what is going on here? Is the back up good enough to use if I reformated hdb and then copied it back? What am I missing?

Thanks

---

### Post by American_Outcast on 2007-09-11
I think I am missing something here. When it says items and files, wouldn't that be the same thing?

---

### Post by merlinus on 2007-09-11
Have you made sure that Show Hidden Files is activated?

---

### Post by American_Outcast on 2007-09-11
Yes I did. I also went ahead and reformatted hdb1. I copied myfolder back to /home but, yep, permission problems now.

I can get to the log in screen with custom login picture I had there. It won't let me log in because of the permissions. The problem I am having is that the permissions seem ok on the sata back up drive but I have to copy them to hdb1 as root, so it changes the permissions of everything to root.

So my next word has to be HELP..... lol. I don't know how to copy the folder to hdb1 and keep the permissions from changing to root.

Edit: The only way I can log in is with failsafe. No DE will work.

---

### Post by American_Outcast on 2007-09-11
I am going to try copying this with Ubuntu rather then Parted  Magic. I noticed something different with the way the Ubuntu Live CD is copying them, well I hope I did anyways.


Edit: Never mind, everything I do keeps changing all the permissions to root and it is frustrating, to say the least.

---

### Post by American_Outcast on 2007-09-11
I think hdb is on its way out. I can use gparted to partition the last 40GB make an ext3 fs and all is well. When I try the first half of the HD I get error messages. If I try the whole HD I get an error message. If I use cfdisk to delete and then create a linux partition using the whole hdb it goes alright. Then I create mke2fs -j and it creates the filesystem and that works but when I check it with gparted it tells me that only 7.9GB is avaiable and the rest is used, though there is nothing there. I may be missing something or it just may be my HD is shot.

---

### Post by startlinuxtoday on 2007-09-11
you sound totally lost. you did not specify what your sata is for.... bu? raid? std hdd?  you need to read more about the purposes and uses of sata before you go experimenting.  #1. install the system onto a single drive. #2. run sata backup software or allow the system to raid it as a mirror. (i take it this is your home system). get your sata drivers correct from the board supplier.

---

### Post by American_Outcast on 2007-09-11
Sorry, I didn't explain the hd's correctly. My sata is just for storage and backing up files. hda and hdb are IDE HD's.

hda
swap
boot
root
var

hdb
home

---

### Post by American_Outcast on 2007-09-11
Well it is time for a break. Several hours of trying to figure this out has given me a headache. I really like Ubuntu, but I am frustrated here. Apparently it is not my hard drive, hdb. I have no idea at this point, I am not sure I care, I've been up all night. All my important data is backed up so if I have to reinstall any os I have what I need. In the mean time I am just going to install DreamLinux temporarily and use that instead of the livecd until I can get this figured out.

---

### Post by American_Outcast on 2007-09-11
Well since no one was able to help I just reinstalled Ubuntu, though I hated to do that. When I get the time I will research file permissions. I hope the couple of people that are now using Ubuntu, on my recommendation, do not have this problem. They are very, very new to Linux.

New set up

hda
swap
/
/home

hdb
Compaq XP

Sda1
Backup
sda2
XP Backup

---

