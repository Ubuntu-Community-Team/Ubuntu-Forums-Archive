---
title: "copying data from broken installation with LiveCD"
date: 2014-12-15
forum: General Help
---

### Post by bardu on 2014-12-15
Somehow I have messed up my Ubuntu 14.04 installation after fouling around with dpgk --purge. After logging in the system freezes.

First, before trying anything  I want to copy some data to an external hard drive via a LiveCD. I followed this instruction 

[http://askubuntu.com/questions/78691/recovering-user-files-with-a-live-cd]("http://askubuntu.com/questions/78691/recovering-user-files-with-a-live-cd")

but the insufficient permission persist.

Any help is much appreciated.

---

### Post by bardu on 2014-12-16
In the meantime I have fixed the broken dpgk in the recovery mode, but unfortunately, that didn't fix my installation. While booting I get an error message: malformed files.

---

### Post by Bucky Ball on 2014-12-16
You have tried opening a terminal and:

```
gksudo nautilus
```

? That *should* give you permission to do what you like. Are you getting the permission error when trying to access the internal or external hard drive partition?

* Ah, you ninja-ed me! Just saw your second post. ;)

How far do you get with the boot and when does this error appear? You mention you got to recovery mode. Could you try a:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... and report any errors, please. Might give more clues.

---

### Post by bardu on 2014-12-16
```
gksudo nautilus
```
Yes, I run nautilus this way and the permissions messages appears while preparing the copy from my machine to external hard drive.
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Did that too but to no avail, still same message shortly after start booting. The only other thing I noticed is that the login screen has a different resolution.

---

### Post by Bucky Ball on 2014-12-16
So you can get past the malformed lines error and login?

---

### Post by bardu on 2014-12-16
Login is successful but then I stuck with the Ubuntu background (not my custom background) but that's it no desktop.

---

### Post by sudodus on 2014-12-16
I suggest that you mount the target drive (where you want the backup copies of your personal files) with a command line

```
sudo mount /dev/sdxy /mnt
```

where x is the drive letter and y is the partition number. You may or may not need to fix the permissions with mount options.

Then you copy the files to **/mnt** (or to subdirectories in **/mnt**) using ***nautilus*** (*drag and drop* from one window to another window).

If still problems running nautilus (with superuser privileges), would you be able to copy/backup your important files with command lines? In that case you can use either of ***cp*** and ***rsync***. You can get tips from us and you can find detailed information in the manual pages ```
man cp
``` and ```
man rsync
```

---

### Post by bardu on 2014-12-16
Thanks, it's getting late here and I will look into that tomorrow morning.

I looked into /var/logs and /var/crash and it seems there is a crash report _usr_bin_Xorg.0.crash ...

---

### Post by bardu on 2014-12-16
I'm booting from LiveCD and have to install gksu in order to use 
```
gksudo nautilus
```
When running the command I get the following message:
> Unable to create a required folder. Please create the following folder, or set permission such that it can be created: /root/.config/nautilus
How can I create this folder from LiveCD?

---

### Post by bardu on 2014-12-16
Ok, I got that. Now nautilus starts properly and I'm able to save my data to the external hard drive.

---

### Post by sudodus on 2014-12-16
Good! Please let us know how it proceeds, 'share your results' :-)

---

