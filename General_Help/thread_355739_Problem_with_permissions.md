---
title: "Problem with permissions"
date: 2007-02-07
forum: General Help
---

### Post by Pedro84 on 2007-02-07
Hello Everyone!

I'm new to Ubuntu and to Linux at all. Everything I do myself cause I felt in Love with it:)

But now I got problem.

My Ubuntu doesn't boot at all. Seems like there're wrong permission. I tried to compile Hamachi and I did something wrong.

When I try to boot normally, splash screen shows for a moment and I get :
rcS process (something) terminated with status 2.
Some lines of something like that. I think 2.


When I try to boot into 'recovery mode' I cannot chamnge chmod: 'Permission denied'

Booting with LiveCD and mounting that partition doesn't help. I got 'unreadable' folder.


What I have to do?

Thanks in advance for any help.
Pedro

---

### Post by Pedro84 on 2007-02-07
When I try to boot normally I got

rcS process (1983) terminated with status 2

and

rs2 process (1989) terminated with status 2


ould anyone help?

---

### Post by llamakc on 2007-02-07
Boot into the LiveCD again, open a terminal, and this thread again. Post the output of:

sudo fdisk -l /dev/hda

We'll need to know where your root ( / ) filesystem is at on your harddisk(s). We'll be remounting the / filesystem so you can write to it, but need to know where it is first.

---

### Post by nickoli_02 on 2007-02-07
Sorry, can't help you but you might want to include a bit more information with your post, like:

is this a fresh install of ubuntu?
Has ubuntu booted fine before you encountered this error?
Were you playing with config settings before you encountered the error?

A little bit more info can go a long way in getting a response :)

---

### Post by Pedro84 on 2007-02-07
is this a fresh install of ubuntu?
Has ubuntu booted fine before you encountered this error?
Were you playing with config settings before you encountered the error?


Fresh install
Booted great!
I have done something wrong. I tried to copile Hamachi server, and I changed something. I think I wrote chmod 0660 -R /ets/sudoers in terminal.

CaN i FIX IT?

---

### Post by llamakc on 2007-02-07
Yes.

Are you in the LiveCD?

What is the output of 

sudo fdisk -l /dev/hda

---

### Post by Pedro84 on 2007-02-07
> **llamakc said:**
> Boot into the LiveCD again, open a terminal, and this thread again. Post the output of:

sudo fdisk -l /dev/hda

We'll need to know where your root ( / ) filesystem is at on your harddisk(s). We'll be remounting the / filesystem so you can write to it, but need to know where it is first.

After writing what You wrote I got

Disk /dev/hda7: 9960 MB, 9960781824 bytes
255 heads, 63 sectors/track, 1210 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hda7 doesn't contain a valid partition table


Strange:| Everything was ok. I saw this partition in Windows with one program [don't remember name].

---

### Post by llamakc on 2007-02-07
So did you install Ubuntu to a 10GB partition? 

cd /media/hda7

(or wherever the LiveCD has the drive mounted). Do an `ls` to make sure you see all of the standard Linux root directories.

---

### Post by llamakc on 2007-02-07
And as for permissions your /etc/sudoers should be:

-r--r----- 1 root root 403 2007-01-07 12:09 /etc/sudoers


Which is the numeric equivalent of `sudo chmod 440 /etc/sudoers` (but not until we have remounted the hard disk's root partition for Ubuntu.

---

### Post by Pedro84 on 2007-02-07
> **llamakc said:**
> So did you install Ubuntu to a 10GB partition? 

cd /media/hda7

(or wherever the LiveCD has the drive mounted). Do an `ls` to make sure you see all of the standard Linux root directories.

Yap. Partition has 10 GB. Is it to small?

---

### Post by llamakc on 2007-02-07
In the LiveCD Terminal, type:

sudo mount -o remount,rw /dev/hda7

Now you can edit that file /etc/sudoers

sudo chmod 440 /media/hda7/etc/sudoers

Bear in mind that this PATH to that last command must be where it is mounted. I don't have a LiveCD booted to check if I have that correct.

Are you sure you didn't muck up the permissions for the entire operating system?

After the above, do:

cd /media/hda7

ls -lh

and post the output.

---

### Post by Pedro84 on 2007-02-07
drwxrwxr-x   2 root root 4,0K 2006-12-08 21:53 bin
drwxrwxr-x   3 root root 4,0K 2007-02-07 00:06 boot
lrwxrwxrwx   1 root root   11 2007-02-06 21:15 cdrom -> media/cdrom
drwxr-xr-x   4 root root 4,0K 2007-02-07 08:49 dev
dr--r----- 116 root root 4,0K 2007-02-07 17:54 etc
drwxrwxr-x   3 root root 4,0K 2007-02-06 21:24 home
drwxrwxr-x   2 root root 4,0K 2006-10-25 13:26 initrd
lrwxrwxrwx   1 root root   33 2007-02-06 21:28 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxrwxr-x  19 root root 8,0K 2007-02-07 00:05 lib
drwxrwxr-x   2 root root  48K 2007-02-06 21:15 lost+found
drwxrwxr-x   9 root root 4,0K 2007-02-07 14:30 media
drwxrwxr-x   2 root root 4,0K 2006-10-19 22:49 mnt
drwxrwxr-x   6 root root 4,0K 2007-02-06 22:26 opt
drwxr-xr-x   2 root root 4,0K 2006-10-19 22:49 proc
drwxrwxr-x  22 root root 4,0K 2007-02-07 18:29 root
drwxrwxr-x   2 root root 4,0K 2007-02-07 18:24 sbin
drwxrwxr-x   2 root root 4,0K 2006-10-25 13:26 srv
drwxr-xr-x   2 root root 4,0K 2006-10-10 14:46 sys
drwxrwxrwt  10 root root 4,0K 2007-02-07 18:29 tmp
drwxrwxr-x  14 root 1000 4,0K 2007-02-06 21:46 usr
drwxrwxr-x  15 root root 4,0K 2006-10-25 13:39 var
lrwxrwxrwx   1 root root   30 2007-02-06 21:28 vmlinuz -> boot/vmlinuz-2.6.17-10-generic


etc
dr--r----- 116 root root 4,0K 2007-02-07 17:54 etc

---

### Post by Pedro84 on 2007-02-07
Is it ok?

---

### Post by llamakc on 2007-02-07
Cool. You figured out that what you did was change all of the permissions inside of /etc. Ugh.

/etc (in this case /media/hda7/etc) should look like:

drwxr-xr-x 143 root root 8.0K 2007-02-07 16:43 etc

which would numerically be 755, and I bet your errors are from the init scripts inside of there:

```

drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc0.d
drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc1.d
drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc2.d
drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc3.d
drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc4.d
drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc5.d
drwxr-xr-x  2 root   root      4096 2007-02-07 16:40 rc6.d
-rwxr-xr-x  1 root   root       306 2006-09-15 04:14 rc.local
drwxr-xr-x  2 root   root      4096 2007-01-07 12:46 rcS.d

```


and /etc/init.d/ (/media/dev/hda7/etc/init.d/ should be the same (755). The scripts INSIDE of init.d must also be 755.

---

### Post by Pedro84 on 2007-02-07
Tried do this with LiveCD ang got this

chmod 755 '/etc/init.d'
chmod: nie mo&#380;na zmieni&#263; uprawnie&#324; do `/etc/init.d': Operation not permitted

---

### Post by Pedro84 on 2007-02-07
Output looks like this:
drwxrwxr-x   2 root root 4,0K 2006-12-08 21:53 bin
drwxrwxr-x   3 root root 4,0K 2007-02-07 00:06 boot
lrwxrwxrwx   1 root root   11 2007-02-06 21:15 cdrom -> media/cdrom
drwxr-xr-x   4 root root 4,0K 2007-02-07 08:49 dev
dr--r----- 116 root root 4,0K 2007-02-07 17:54 etc
drwxrwxr-x   3 root root 4,0K 2007-02-06 21:24 home
drwxrwxr-x   2 root root 4,0K 2006-10-25 13:26 initrd
lrwxrwxrwx   1 root root   33 2007-02-06 21:28 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxrwxr-x  19 root root 8,0K 2007-02-07 00:05 lib
drwxrwxr-x   2 root root  48K 2007-02-06 21:15 lost+found
drwxrwxr-x   9 root root 4,0K 2007-02-07 14:30 media
drwxrwxr-x   2 root root 4,0K 2006-10-19 22:49 mnt
drwxrwxr-x   6 root root 4,0K 2007-02-06 22:26 opt
drwxr-xr-x   2 root root 4,0K 2006-10-19 22:49 proc
drwxrwxr-x  22 root root 4,0K 2007-02-07 18:29 root
drwxrwxr-x   2 root root 4,0K 2007-02-07 18:24 sbin
drwxrwxr-x   2 root root 4,0K 2006-10-25 13:26 srv
drwxr-xr-x   2 root root 4,0K 2006-10-10 14:46 sys
drwxrwxrwt  10 root root 4,0K 2007-02-07 18:29 tmp
drwxrwxr-x  14 root 1000 4,0K 2007-02-06 21:46 usr
drwxrwxr-x  15 root root 4,0K 2006-10-25 13:39 var
lrwxrwxrwx   1 root root   30 2007-02-06 21:28 vmlinuz -> boot/vmlinuz-2.6.17-10-generic


What is wrong :confused:

---

### Post by Pedro84 on 2007-02-07
I cannot change any chmods for /etc directory:|

---

### Post by llamakc on 2007-02-07
You are not following directions. I'll say it again.

You are currently using a LiveCD, so the directory

/etc

is ON THE CD. You can not edit that. You must have already done the command I had above about remounting /dev/hda7. Have you remounted /dev/hda7?

If you have, you need to be working on where it is mounted, which as I mentioned, I BELIEVE is at /media/hda7. If it IS at /media/hda7 your commands would be:

chmod 755 /media/hda7/etc

And continue with the contents of /media/hda7/etc/init.d, the contents of /media/hda7/etc/init.d, and the /media/hda7/etc/rc* directories.

To recap: /etc is on your CD, /media/hda7/etc is the directory on your hard drive that you messed up.

---

### Post by Pedro84 on 2007-02-07
Sorry, my false:(

But when I write
sudo mount -o remount,rw /dev/hda7

I got
mount: can't find /dev/hda7 in /etc/fstab or /etc/mtab



In Terminal, in LiveCD

---

### Post by llamakc on 2007-02-07
Do this: in the Terminal type:

mount

and post the contents please. If you received an error about the mount command before you should have said so. You need to run that command for the proper partition that has your root filesystem on it. Do you know what your disk layout is?

---

### Post by Pedro84 on 2007-02-07
I try once again do everything You post.

Very thank You for Your time!

---

### Post by llamakc on 2007-02-07
Do you have IM? I'm on ICQ as 24328596

---

