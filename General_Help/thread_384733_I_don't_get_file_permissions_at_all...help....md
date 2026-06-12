---
title: "I don't get file permissions at all...help..."
date: 2007-03-14
forum: General Help
---

### Post by eitan_a on 2007-03-14
Hey guys, been using ubuntu for a good 3 months now and love it.  I don't get linux, or ubuntu's, way of handling file permissions.  I'm running 6.10 on a sony vaio laptop.  I can change my screen's brightness using the command

```

echo # > /proc/acpi/sony/brightness

```

I have setup a tiny script that makes it go up or down 1 value.  
Anyways, to even allow me to execute the command I need to execute

```

gksu chown eitan\: /proc/acpi/sony/brightness

```

everytime I boot my computer up.  This is a giant hassle and is due to me just never understanding how linux handles permissions. 

On a side note, I am having a bug with pkg_config_path where the config path is not saved after I reboot, causing me to do 

```

export PKG_CONFIG_PATH=/usr/lib/pkgconfig

```

Where is this saved?  I don't like having to do this everytime I want to compile something.

Thanks for all the help guys.
Eitan

---

### Post by lloyd_b on 2007-03-14
> Anyways, to even allow me to execute the command I need to execute
```
gksu chown eitan\: /proc/acpi/sony/brightness
```
everytime I boot my computer up. This is a giant hassle and is due to me just never understanding how linux handles permissions.

What you're getting nailed by is the fact the "/proc" directory is the mount point for a "virtual file system".  In short - your changes are being stored on a ramdisk, which is recreated each time you boot.  So, in that particular directory, you can't make permanent changes.

> On a side note, I am having a bug with pkg_config_path where the config path is not saved after I reboot, causing me to do
```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```
Where is this saved? I don't like having to do this everytime I want to compile something.


In your home directory, edit the file ".bashrc", and add that line to it.

Lloyd B.

---

### Post by llamakc on 2007-03-14
sudo echo # > /proc/acpi/sony/brightness

Now you don't have to chown it. Just run the command with sudo instead.

---

### Post by eitan_a on 2007-03-15
I don't want to run the command using sudo since I have it bound to keys on a keyboard.  In other words, I don't want to enter my password a second time after I boot up just to change brightness.

Is there a way to move brightness to a different directory and have it work from there?  Or do I need to install it elsewhere?  I still would like to fix this.  Thanks.

---

### Post by darrenm on 2007-03-15
try
```
echo "password" | sudo -S echo "#" > /proc/acpi/sony/brightness
```

You can bash alias that command, or script it, or assign a key to it.

---

### Post by eitan_a on 2007-03-15
Okay but isn't it un-secure to have your password not decrypted in a file?

---

### Post by mbeierl on 2007-03-15
> **llamakc said:**
> sudo echo # > /proc/acpi/sony/brightness

Now you don't have to chown it. Just run the command with sudo instead.

I don't think sudo echo works that way.  Breaking the command down gives the following:

[LIST]
[*]sudo echo #
This causes the echo command to run as root
[*]> /proc/acpi/sony/brightness
Redirect the output of the command to /proc/acpi/sony/brightness
[/LIST]

So, the echo command is run as root, but the redirect ">" is run as the user.  I keep getting permission denied whenever I've tried to do that sort of thing.

It's too bad that the group of all these entries is root.  If there were different groups and these entries had group write permissions, then you could just add yourself to the appropriate group.

The only workaround I can see is to put the chown command into /etc/rc.local  That script is executed as root with every boot.

---

### Post by eitan_a on 2007-03-15
That did it, thanks!

---

### Post by thejart on 2007-03-15
I'm having some file permission issues myself.  I'm trying to give my wife access to a folder for storage purposes.  Here are the contents of her home and storage (sara_ftp) directories:

```
sara@prussia:~$ ll
total 796K
-rw-r--r-- 1 sara sara    0 2007-03-15 15:12 bogus
-rw-r--r-- 1 sara sara 792K 2007-03-15 11:26 IFP-1XXT.HEX
lrwxrwxrwx 1 sara sara   16 2007-03-15 15:06 sara_ftp -> /mnt/g/sara_ftp/
sara@prussia:~$ ll sara_ftp/
total 0
drwxrwxr-x 1 thejart ssh 0 2006-05-03 21:22 2006.02 back-up
drwxrwxr-x 1 thejart ssh 0 2006-05-03 21:52 2006.05 back-up
drwxrwxr-x 1 thejart ssh 0 2006-12-19 12:22 2006.12 back-up
drwxrwxr-x 1 thejart ssh 0 2006-08-27 22:51 from axilla
sara@prussia:~$ groups
sara dialout cdrom floppy audio video plugdev lpadmin scanner ssh
```

I have created two users, thejart and sara.  Each of them also belongs to a group called ssh.  It seems like all of the permssions are setup correctly, but maybe I'm misunderstanding how groups work.  If sara tries to copy a file into her storage folder it says:
```

sara@prussia:~$ cp bogus sara_ftp/
cp: cannot create regular file `sara_ftp/bogus': Permission denied
```

but if I do it, it's cool:
```
thejart@prussia:/home/sara$ ll
total 796K
-rw-r--r-- 1 sara sara    0 2007-03-15 15:12 bogus
-rw-r--r-- 1 sara sara 792K 2007-03-15 11:26 IFP-1XXT.HEX
lrwxrwxrwx 1 sara sara   16 2007-03-15 15:06 sara_ftp -> /mnt/g/sara_ftp/
thejart@prussia:/home/sara$ cp bogus sara_ftp/
thejart@prussia:/home/sara$ groups
thejart adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin ssh
```

You can see the groups that I belong to, too.  Any thoughts on how I can give her write access to that folder?  What am I doing wrong?  I'm not sure what the adm and admin groups specifically do, although I have a hunch that one group or both is required for super user access.

---

### Post by darrenm on 2007-03-15
> **eitan_a said:**
> Okay but isn't it un-secure to have your password not decrypted in a file?

Yes it is. chmod the file 600 or don't do it if you have security concerns.

---

### Post by mbeierl on 2007-03-16
> **thejart said:**
> I'm having some file permission issues myself.  I'm trying to give my wife access to a folder for storage purposes.

You should really start a new post, but, seeing as we're here:  what is the output of
```

ls -al /mnt/g

```
I'm interested in the ownership and permissions of /mnt/g/sara_ftp itself...

---

### Post by thejart on 2007-03-17
sorry about the non-new post thing.  here's the output:

```
thejart@prussia:~$ ls -al /mnt/g/
total 4
drwxrwxr-x 1 thejart ssh     0 2007-03-08 10:53 .
drwxr-xr-x 5 root    root 4096 2007-02-20 17:47 ..
drwxrwxr-x 1 thejart ssh     0 2007-01-07 14:36 1974.12.20 mom and dad's wedding audio
drwxrwxr-x 1 thejart ssh     0 2006-10-08 22:22 -  DVD  Raw
drwxrwxr-x 1 thejart ssh     0 2007-03-08 10:55 from axilla
drwxrwxr-x 1 thejart ssh     0 2006-12-28 10:34 LOOK AT ME
drwxrwxr-x 1 thejart ssh     0 2007-03-15 15:14 mp3 archive
drwxrwxr-x 1 thejart ssh     0 2005-06-22 12:08 MSOCache
drwxrwxr-x 1 thejart ssh     0 2007-01-09 21:01 -  my pix (05.12.19)  -
drwxrwxr-x 1 thejart ssh     0 2006-09-12 20:32 RECYCLER
drwxrwxr-x 1 thejart ssh     0 2007-03-15 15:32 sara_ftp
drwxrwxr-x 1 thejart ssh     0 2005-02-23 13:01 System Volume Information
```

it seems like she should have write access to me...but here we are :)

just so you understand, although i don't think this is the issue, g is mounted at bootup with this command in the fstab:
```

//hare/g /mnt/g cifs credentials=/home/thejart/.smbpasswd,iocharset=utf8,file_mode=0775,dir_mode=0775,uid=thejart,gid=ssh 0 0
```

---

### Post by darrenm on 2007-03-17
Surely you want file_mode and dir_mode to be 0777 ?

---

### Post by mbeierl on 2007-03-17
> **thejart said:**
> 
just so you understand, although i don't think this is the issue, g is mounted at bootup with this command in the fstab:
```

//hare/g /mnt/g cifs credentials=/home/thejart/.smbpasswd,iocharset=utf8,file_mode=0775,dir_mode=0775,uid=thejart,gid=ssh 0 0
```

cifs.  Hmm.  Does that mean it's a Windows box that owns the share?  And if so, does user 'sara' and group 'ssh' map properly onto the Windows system?  Does the share have proper write permissions on the filesystem itself?  I'm thinking it might be a remote permission problem, not local, because it looks like you've done everything right locally.

---

### Post by thejart on 2007-03-19
> **darrenm said:**
> Surely you want file_mode and dir_mode to be 0777 ?

well, i don't want other users to have write access.  i have a ssh ftp server running to share some images with a few friends of mine, and their account is not a member of the 'ssh' group with write access to those mount points.


[QUOTE=mbeierl]cifs. Hmm. Does that mean it's a Windows box that owns the share? And if so, does user 'sara' and group 'ssh' map properly onto the Windows system? Does the share have proper write permissions on the filesystem itself? I'm thinking it might be a remote permission problem, not local, because it looks like you've done everything right locally.[/QUOTE]

you're right it is a windows box.  i thought of that, but there is also no user called 'thejart.'  my creditials file contains my login info for a user 'jarrett,' and as 'thejart' i still have full access.

hmmm...

---

### Post by thejart on 2007-03-20
i figured it out!  i had inadvertently created a second group called 'ssh' when i set up the permissions for my wife and i.  it didn't occur to me that openssh had created it upon install.  the way i figured it out was with tiger.  it saw the two separate instances of ssh in the /etc/groups file and reported it as a warning.  i created a new group for my purpose and it works...woohoo!

---

