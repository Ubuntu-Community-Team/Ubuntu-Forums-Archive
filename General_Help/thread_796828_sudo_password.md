---
title: "sudo password"
date: 2008-05-16
forum: General Help
---

### Post by hrvarakl on 2008-05-16
Hi all!

I was wandering if there is any way of inserting the user password
*inside* a sudo command, using an option [-something] for example, and thus not having to type it when prompted to(after the sudo command)...
Well,what I want to do is run a script at startup which would mount
one of my hard drives that is not mounted automatically and mount must be executed as root, so a sudo is needed... :)

---

### Post by Mr A Mouse on 2008-05-16
If you could do it that way, anyone who can see your screen (physically or via a remote session) immediately sees your root password. Double-plus ungood.

---

### Post by hrvarakl on 2008-05-16
That would indeed be a problem but let's say we don't care about that that much.. I am looking into other ways of mounting the disk at startup but I would like to make the script work(just for fun ;))

---

### Post by Mr A Mouse on 2008-05-16
Oh, simple--instead of manually mounting it, add it to your fstab file. Instructions are [here]("http://www.tuxfiles.org/linuxhelp/fstab.html").

---

### Post by Mr A Mouse on 2008-05-16
> **Mr A Mouse said:**
> Oh, simple--instead of manually mounting it, add it to your fstab file. Instructions are [here]("http://www.tuxfiles.org/linuxhelp/fstab.html").

Edited to add: Sudo was deliberately designed to not accept a password as an argument, so I don't think it can be done on a single command line. Doing it from a script may be possible, but I'm not good enough with scripts to know for sure.

---

### Post by da chicken on 2008-05-16
Edit your sudoers file with visudo and add the NOPASSWD flag for the user for those commands you want to script.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

However, why not run it as an init script?

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by ibuclaw on 2008-05-16
Is the hard-drive removeable?
If so, you can use **pmount** without the sudo command to mount it.

To test it, unmount the hard-drive and type in:
```
pmount /dev/sda1
```
Or whatever the device name is called.

Also, the bootscript is executed as root. So no sudo is required.

```
gksu gedit /etc/gdm/PreSession/Default
```
Scroll all the way down to the bottom, and before the "**exit 0**" line.
Put in this:
```

[ "$(ls -A /media/**MOUNTPOINT**)" ] && echo "device mounted" || mount /dev/**DEVICE** /media/**MOUNTPOINT**
```
Change everything in bold to what they should be.

Then save the file and reboot.

NOTE:
For the script to work, the folder where your hard-drive mounts in must be empty as a prerequisite.

Regards
Iain

---

### Post by Mr A Mouse on 2008-05-16
> **da chicken said:**
> Edit your sudoers file with visudo and add the NOPASSWD flag for the user for those files.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Oops! My bad--I didn't know you could do this. :)

---

### Post by ibuclaw on 2008-05-16
> **da chicken said:**
> Edit your sudoers file with visudo and add the NOPASSWD flag for the user for those files.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

But first, type in this:
```

export EDITOR=gedit
sudo -E visudo

```

Else you'll get a real shock when you open up into Vim!

[EDIT]
Just read the help docs... They are quoting me from a post I may last month! :D
> 
gedit ~/.bashrc

Add the lines :

export EDITOR=gedit
alias visudo='-E visudo'

That has made my day!
Although, I have to shamefully say that **that** doesn't seem to work anymore (I'm looking in a fix).


Regards
Iain

---

### Post by hrvarakl on 2008-05-16
> **Mr A Mouse said:**
> Edited to add: Sudo was deliberately designed to not accept a password as an argument, so I don't think it can be done on a single command line. Doing it from a script may be possible, but I'm not good enough with scripts to know for sure.

Well the script seems to run at startup but(I think because of the sudo) mount fails(I am not even prompted to enter a password...)

---

### Post by hrvarakl on 2008-05-16
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=400adf33-38d6-46c1-84ea-9130ee4e43bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=F0183C9E183C65AE /media/Data1    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=D5E6-FE3F  /media/Data2    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=C4C43810C4380768 /media/Vista    ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

This is the fstab file in /etc...
I want to mount /dev/sdb2, so aren't the above lines supposed to do the job?

---

### Post by hrvarakl on 2008-05-16
Thanks for all the advise!

I am trying to modify sudoers.tmp with visudo but I can't figure what I am supposed to write under the 'User privilege specification' section to bypass password prompt for the mount commands...

---

### Post by hrvarakl on 2008-05-16
> **hrvarakl said:**
> 
I am trying to modify sudoers.tmp with visudo but I can't figure what I am supposed to write under the 'User privilege specification' section to bypass password prompt for the mount commands...

To be specific:

I created a cmd_alias in the cmd section:
Cmnd_Alias MOUNT_CMDS = /sbin/mount.fuse, /sbin/mount.ntfs, /sbin/mount.ntfs-3g

and in the user privilege section I added the line:
<username> <hostname> = NOPASSWD: MOUNT_CMDS

but it still asks for password!

---

