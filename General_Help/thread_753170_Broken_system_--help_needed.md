---
title: "Broken system --help needed"
date: 2008-04-12
forum: General Help
---

### Post by anodizer on 2008-04-12
I was trying to backup my system using rsync like the method described here: [http://matthewhelmke.net/index.php/2008/04/08/48-using-rsync-to-back-up-my-laptop](http://matthewhelmke.net/index.php/2008/04/08/48-using-rsync-to-back-up-my-laptop)

the command I used was like 
```
sudo rsync --force --ignore-errors --delete --delete-excluded --exclude-from=/media/disk/matthew-exclude.txt --backup --backup-dir=`date +%Y-%m-%d` -av / /media/disk/backup/matthew-laptop
```

and I noticed some files getting deleted from /dev and /proc. Then the worse came, the power went out and the result is I can't log to my account anymore.
Ubuntu boots alright but this when I login i get the "session lasted less than 10 seconds" error. Notice that I cannot login using failsafe gnome either, console only.
The .xsession-errors file is this:

```
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'klaount' found
===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2008/04/12 18:34:02.0732 (sabayon-apply): No profile for user 'klaount' found
MainThread 2008/04/12 18:34:02.0734 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2008/04/12 18:34:02.0737 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 107, in <module>
    sys.exit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2008/04/12 18:34:02.0732 (sabayon-apply): No profile for user 'klaount' found
MainThread 2008/04/12 18:34:02.0734 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2008/04/12 18:34:02.0737 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 107, in <module>
    sys.exit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied

```

Is there any way to repair it?? ( I don't have any backups, and I really can't re-install right now)
thanks in advance!

---

### Post by ibuclaw on 2008-04-12
Have you tried creating a new user?

If you can boot into recovery mode, do it. And type in the command:
```
 adduser backup 
```
For example, and you'll be asked to enter in password, etc.
You can just hit enter through the Phone Numbers, etc.
```

root@fredbuntu:/home# adduser test
Adding user `test' ...
Adding new group `test' (1004) ...
Adding new user `test' (1004) with group `test' ...
Creating home directory `/home/test' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
	Full Name []: Test Account
	Room Number []:
	Work Phone []:
	Home Phone []:
	Other []:
Is the information correct? [y/N] y
root@fredbuntu:/home# ls
administrator  iain  lost+found  test

```

Then login to your new account in gdm.
**If it works**. Then the good news is that this is a "**user-wide**" failure, and **not** a "**system-wide**" failure. And I can say that this is most definitely fixable!

Else, well... We'll just have to wait and see...

Regards
Iain

[EDIT]
And as for backing up your system, wouldn't a cronjob be a suitable course of action?
You can have a script in /etc/cron.daily that checks the day, and gathers tarballs of precious directories into one file named "Backup-Sat.tar.gz" for Saturday as an example. And "Backup-Mon.tar.gz" for Monday.
It doesn't require a high knowledge of BASH scripts.
Off the top of my head. You'll need no more than the commands::
 - tar
 - mv
 - date
And an absolute minimum of one function.

There is a nice "Know-How" [here.]("http://www.desktoplinux.com/articles/AT2280165098.html")
It doesn't give any specific scripts, but it gives you an idea on what you should backup and what is probably best left.

Else, there are plenty of suitable software that can do it for you. And are (as so it seems in this case) "**safer**".

---

### Post by anodizer on 2008-04-12
Thanks for your reply, unfortunately adding a new user didn't work though. The error message is the same as above. :(
Any other ideas?

---

### Post by ibuclaw on 2008-04-13
Hmm... Not alot that I can help you with unfortunately. Fixing the Linux-System is not on my list of things that I'm good at.

Though, One thing I'd try would be to reinstall everything via the LiveCD.

It's a neat trick using **chroot**.

Basically, when you boot up, boot from the LiveCD.
And when the desktop loads, open up a terminal.

These are the general actions that you take to do this:

a) Mount your root partition to an empty directory in the LiveCD directories.
```
 ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt 
```
opt) If you have a separate home partition, mount it to home in the root partition.
```
 ubuntu@ubuntu:~$ sudo mount /dev/sdb3 /mnt/home 
```
b) chroot into your root partition.
```
 ubuntu@ubuntu:~$ sudo chroot /mnt 
```
opt) if you wish to be your own user instead of root. su your user.
```
 root@ubuntu:/# su administrator 
```
c) change to your home directory, you can type in **ls** to make sure that it is yours.
```
 administrator@ubuntu:/$ cd 
```
d) Get your list of installed packages and save them to a file.
```
 dpkg --get-selections | awk '{if ($2="install") print $1" "}' | tr -d '\n' > installedpackages 
```
If you are not already, get yourself connected to the internet. Ethernet preferred, as it's quick and doesn't require reboot.

opt) Get a list of updated packages from the repositories. This requires your password if you switched to your user in Linux.
```
 administrator@ubuntu:/$ sudo apt-get update
sudo: unable to resolve host ubuntu
[sudo] password for administrator: 
```
e) Re-install all your packages.
```
 sudo aptitude reinstall `cat installedpackages` 
```
Though if you have a general idea which package it belongs to, you will save alot of time (and space) just by reinstalling that one or couple of packages.

--------------------------------------------------------------------------------------------------------------------------------------
[EDIT]
I've just had a read through a few threads and found that someone with what appears to have a similiar problem.
He chmod'ed two files in the /dev folder to 666 to fix it.
```

sudo chmod 666 /dev/random
sudo chmod 666 /dev/urandom

```
I've just checked, and mine are set to those permissions. So give it a try.

Regards
Iain

---

### Post by anodizer on 2008-04-13
I thank you deeply for your effort here, that's why I love linux community.
In the end I used a live cd to backup my home folder/installed packages similarly to what you described here and reinstall ubuntu, I ran into a couple of more problems while restoring my settings but everything is ok now.
I believe that something like a "repair system" or "system restore" application is really needed on cases like this, but anyway the lesson I took is to be more careful while using "weird" commands :P

---

### Post by ibuclaw on 2008-04-13
Weird commands are good, as long as you don't use **sudo** infront of them. At least, that is my analogy of eveything :D

If I were to design a system restore app for ubuntu, I would go down the route of what Compaq does (or used to do) for Windows XP machines.

The idea is to have two independant Operating Systems.
OS1 **can't** see or touch OS2, but OS2 **can** see and touch OS1.
OS1 would be Ubuntu.
OS2 would be System Restore.

Lets say that we have one 80GB hard drive.
70-75GBs would go towards OS1 for the root and separate home partition.
1GB would be used as a swap.
And the rest would be there for OS2 to have a bare-bones or "mini" version of Ubuntu (or Ubuntu Server) installed on.

When your system breaks, choosing "System Restore" in the GRUB menu and OS2 automatically removes the sensitive areas (/boot, /usr, /etc, and others) of OS1 and copies over it's own files/folder to replace them.
while leaving the /home and maybe the /local and /opt directories intact, of course!

Maybe as a an extra friendly feature, you can have an option which allows it to get a list of all your apps and reinstall them after the System Restore (similiar to the method I described above).

Of course, there would also have to be a special app that would upgrade the System Restore from OS1 (implemented in a cronjob perhaps), else if you have the kernel 2.6.24-12, you may find that you've downgraded or gained a kernel in the GRUB menu!

If you like the idea, propose it to Launchpad. I'm sure they'll get something ready in-time for 8.10!

Regards
Iain

---

