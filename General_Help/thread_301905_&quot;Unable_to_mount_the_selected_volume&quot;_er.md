---
title: "&quot;Unable to mount the selected volume&quot; error with Windows NTFS partition"
date: 2006-11-17
forum: General Help
---

### Post by EGE-FB on 2006-11-17
Hi, 

I went through the steps in making my Windows NTFS partition readable and writable following the steps on this site:

[http://everythingelse.wordpress.com/2006/07/19/89/](http://everythingelse.wordpress.com/2006/07/19/89/)

I can read and write on my NTFS partition when I access it through /media/windows, however when I try to access the partition through Computer> S3A3305D001 (Drive name), it gives this error:

Unable to mount the selected volume
mount: according to mtab, /dev/sda1 is already mounted on /media/windows

mount failed

---

### Post by taurus on 2006-11-17
Have you added an entry in your /etc/fstab to mount /dev/sda1?  What is your /etc/fstab look like then?

```
cat /etc/fstab
```

---

### Post by EGE-FB on 2006-11-17
This is what my fstab looks like.

---

### Post by EGE-FB on 2006-11-17
Here's a screenshot of my situation.

---

### Post by taurus on 2006-11-17
What's the output of this command then?

```
df -h
```

---

### Post by EGE-FB on 2006-11-17
<file system> <mount point>   <type>  <options>       <dump>  <pass>
root@ege:/home/ege# proc            /proc           proc    defaults        0     0
bash: proc: command not found
root@ege:/home/ege# /dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
bash: /dev/sda2: Permission denied
root@ege:/home/ege# /dev/sda4       /home           ext3    defaults        0     2
bash: /dev/sda4: Permission denied
root@ege:/home/ege# /dev/sda1       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
bash: /dev/sda1: Permission denied
root@ege:/home/ege# /dev/sda3       none            swap    sw              0     0
bash: /dev/sda3: Permission denied
root@ege:/home/ege# /dev/hda        /media/cdrom0   udf,iso9660 user,noauto 0       0

---

### Post by taurus on 2006-11-17
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of that command after you type it in at the prompt.

```
df -h
```

---

### Post by taurus on 2006-11-17
> **EGE-FB said:**
> <file system> <mount point>   <type>  <options>       <dump>  <pass>
root@ege:/home/ege# proc            /proc           proc    defaults        0     0
bash: proc: command not found
root@ege:/home/ege# /dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
bash: /dev/sda2: Permission denied
root@ege:/home/ege# /dev/sda4       /home           ext3    defaults        0     2
bash: /dev/sda4: Permission denied
root@ege:/home/ege# /dev/sda1       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
bash: /dev/sda1: Permission denied
root@ege:/home/ege# /dev/sda3       none            swap    sw              0     0
bash: /dev/sda3: Permission denied
root@ege:/home/ege# /dev/hda        /media/cdrom0   udf,iso9660 user,noauto 0       0

:confused:  :confused:  :confused:

---

### Post by EGE-FB on 2006-11-17
Sorry, mixed things up. 


Here's the output:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             5.0G  1.9G  2.8G  41% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  136K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  487M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sda4              41G  3.5G   36G   9% /home
/dev/sda1              45G   35G   11G  78% /media/windows

---

### Post by taurus on 2006-11-17
Well, your NTFS is currently mounted on /media/windows.  From a terminal again, what do you get when you run this command?

```
ls -la /media/windows
```
You should see a list of files and directories on your Windows XP partition.

---

### Post by EGE-FB on 2006-11-17
Actually, on the tutorial I used, I don't know if this command was carried out properly. 

Now, create a directory where your NTFS partition will be mounted

       sudo mkdir /media/<give a name to your mount point>"

---

### Post by taurus on 2006-11-17
> **EGE-FB said:**
> Actually, on the tutorial I used, I don't know if this command was carried out properly. 

Now, create a directory where your NTFS partition will be mounted

       sudo mkdir /media/<give a name to your mount point>"

It means

```
sudo mkdir /media/windows
```
in your case...

---

### Post by EGE-FB on 2006-11-17
Ye I can see all my files when I do that. 

My problem is, when I go to "windows" through media/windows/ , it works, I can edit anything in that folder. 

But, when I try to go to "windows" from Computer > S3A3305D001 it gives that error. Am I supposed to be able to access my NTFS partition from there or is it only from media/windows/ ?

---

### Post by EGE-FB on 2006-11-17
> **taurus said:**
> It means

```
sudo mkdir /media/windows
```
in your case...

Ye when I did that, this came up:

mkdir: cannot create directory `/media/windows': File exists

So I guess nothing went wrong there, since the file was already there.

---

### Post by taurus on 2006-11-17
> **EGE-FB said:**
> Ye I can see all my files when I do that. 

My problem is, when I go to "windows" through media/windows/ , it works, I can edit anything in that folder. 

But, when I try to go to "windows" from Computer > S3A3305D001 it gives that error. Am I supposed to be able to access my NTFS partition from there or is it only from media/windows/ ?
Looks like only from /media/windows since you mount your NTFS to /media/windows.

---

### Post by EGE-FB on 2006-11-17
So I will only be able to access it through media/windows/ ?

:neutral:

---

### Post by EGE-FB on 2006-11-17
It's not a big deal then, I just wanted to know if my error message meant i did something wrong while following the steps in the tutorial.

---

