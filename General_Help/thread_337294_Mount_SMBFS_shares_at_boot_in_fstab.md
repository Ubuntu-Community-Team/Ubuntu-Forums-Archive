---
title: "Mount SMBFS shares at boot in fstab"
date: 2007-01-12
forum: General Help
---

### Post by mkw87 on 2007-01-12
Ok, I have two desktops and a laptop both running Edgy and one desktop and the laptop dual-boot Windows XP SP2.  My goal is to have the desktop without windows, an Edgy Server install, serve media files.  I have shares setup that work great in windows - can map them to automount.  However, in Ubuntu, I can't get them to mount properly using fstab.

My fstab file looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# root directory
/dev/sda5 / ext3 defaults,errors=remount-ro 0 1
# home directory
/dev/sda4 /home ext3 nodev,nosuid 0 2
# media directory (/home/media)
/dev/hda6 /home/matthew/media ext3 defaults,errors=remount-ro 0 1

# windows HD's
/dev/sda1 /mnt/C_Drive ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda2 /mnt/Programs ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda5 /mnt/Stuff ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda6 none swap sw 0 0

# CD/DvD Drives
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdd	/media/cdrom1   udf,iso9660 user,noauto     0       0

# Network Drive Mounts
# music
//server/music/  	/home/matthew/music/ 		smbfs  credentials=/home/matthew/.smbcredentials 0 0
# downloads
//server/downloads/    	/home/matthew/server/downloads/ smbfs  credentials=/home/matthew/.smbcredentials 0 0
# backup
//server/backup/     	/home/matthew/server/backup/ 	smbfs  credentials=/home/matthew/.smbcredentials 0 0
# movies
//server/movies/ 	/home/matthew/server/movies/ 	smbfs  credentials=/home/matthew/.smbcredentials 0 0
```

The error I get when executing "sudo mount -a" is:
```
matthew@bandersnatch:~$ sudo mount -a
Password:
6369: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
6370: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
6371: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
6372: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```

I have been using the forums and google to try to solve this for over 2 hours now with no success.  The shares are browseable over the network in Ubuntu, and I can mount them using a script that looks like:
```
sudo mount -t smbfs -o username=lan,password=lan //192.168.1.102/movies /home/matthew/server/movies

sudo mount -t smbfs -o username=lan,password=lan //192.168.1.102/music /home/matthew/music

sudo mount -t smbfs -o username=lan,password=lan //192.168.1.102/downloads /home/matthew/server/downloads

sudo mount -t smbfs -o username=lan,password=lan //192.168.1.102/backup /home/matthew/server/backup
```

but then they are not writeable.  So what I want is to be able to mount them as writeable.  I have tried substituding the IP of the server for its hostname (server) and neither makes a difference.  I have tried different usernames, a username without requiring a password, no username or password, NOTHING has worked.  I always get an error saying either no access or that the share doesn't exist.  The no access is a result of using no username, the samba share wants a username.   

Solution 1: Fix fstab so it mounts properly
Solution 2: Modify script to mount the drives as writeable. With the drives mounted, if I ls -l they show up belonging to root, which is why I don't have write access (I think).

Thanks in advance for any help.

---

### Post by Cryptic1911 on 2007-01-12
throw a "fmask=777,dmask=777" into your mount command and it will give you rwxrwxrwx access on everything

---

### Post by Cryptic1911 on 2007-01-12
do something like:
sudo mount -t smbfs -o fmask=777,dmask=777,username=lan,password=lan //192.168.1.102/movies /home/matthew/server/movies

---

### Post by mkw87 on 2007-01-12
Thanks a bunch, it works.

I'm still scratching as to why the fstab method won't work, because from what I read that is the most common way to do it.

Ahh well, I just spent two more hours trying to install mythtv on the server only to give up because MySQL is such a @!#O$&().  I have the common problem of not being able to properly set the password - it happened off of a fresh install when I installed MySQL for the server aspect of it.  I can complete the first line below, but not the second:

```
mysqladmin -u root password yourrootsqlpassword
mysqladmin -h server1.example.com -u root password yourrootsqlpassword
```

It shoots back an error saying that root is not allowed to connect with password = NO.  It took me a long time to get that far too - eesh.  I love ubuntu, but I'm a Mechanical Engineer who loves to tinker with things.  My grandfather would have shot his computer with a shotgun before he spent this much time 'setting it up' (note: windows isn't any better, thats for sure - just a small rant because I can't get mysql to work properly on a fresh x86 edgy install :(  )

Thanks again.

---

### Post by Cryptic1911 on 2007-01-12
well, i'm not sure how your system is setup, but it could be something as dumb as the fact that you cant resolve the server by name.. try putting in 

//**192.168.1.102**/movies/ 	/home/matthew/server/movies/ 	smbfs  credentials=/home/matthew/.smbcredentials**,fmask=777,dmask=777** 0 0

if that works, then add an entry to your /etc/hosts file with the ip & servername to make sure your machine can resolve it by name

---

### Post by malarky on 2007-02-08
How can I mount a windows share that has a space? eg: //server/stupid share name

Ugly, I know, but changing the share name is not an option

---

### Post by thejart on 2007-02-10
i'm not really sure, but no one has replied to you yet so i thought i'd give you some options.
-you could try putting the whole thing in quotes "//server/stupid share name"
-you could try escaping the spaces //server/stupid\ share\ name
-or you could try %20 in place of the spaces (prolly just a web thing, though)

i bet that the second one will work for you, though.

---

### Post by jizo on 2007-11-14
If you have a share name with spaces for example

//myWindowsMachine/share name

then the proper way to escape the spaces in the /etc/fstab would be with \040
so you would put

//myWindowsMachine/share\040/name

that's what I do on my machine and it works like a charm :)

---

