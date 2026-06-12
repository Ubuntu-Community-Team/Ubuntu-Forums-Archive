---
title: "samba issues any help would be appreciated"
date: 2006-08-13
forum: General Help
---

### Post by xxFelixDCatxx on 2006-08-13
okay I'm absolutely miffed.  

Synopsis:  I'm trying to mount a server 2k3 directory to a local file in ubuntu 6.06 

using this command
sudo mount //192.168.2.2/D$ /media/sharename/ -o username=Felix,password=*******

I got this error message.
cli_negprot: SMB signing is mandatory and we have disabled it.
5175: protocol negotiation failed
SMB connection failed


after doing some reading [http://www.ubuntuforums.org/archive/index.php/t-8479.html](http://www.ubuntuforums.org/archive/index.php/t-8479.html).  I determined the error message has to be some issue with the handshake process between server 2k3 and samba. And the fix was *supposed* to be entering a -t cifs entry in mount.

so my most recent code looked like this

sudo mount -t cifs //192.168.2.2/D$ /media/sharename -o username=Felix,password=*******

and the output....

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


what in the world am i doing wrong here?!?!

---

### Post by vijirajan on 2006-08-13
It looks like you don't have smbfs installed.

```

sudo apt-get install smbfs

```

and try your command again.

---

### Post by xxFelixDCatxx on 2006-08-13
> **vijirajan said:**
> It looks like you don't have smbfs installed.

```

sudo apt-get install smbfs

```

and try your command again.

nope, just tried that, I already had smbfs installed....

I believe the issue lies in that server 2k3 is not complient with smbfs, but is instead complient with cifs... should i try to install something like that?

---

### Post by vijirajan on 2006-08-13
I think in your command above the parameters are out of order.

```

sudo mount -t cifs //192.168.2.2/D$ /media/sharename -o username=Felix,password=*******

```

Try this

```

sudo mount -t cifs -o username=Felix,password=******* //192.168.2.2/D$ /media/sharename

```

---

### Post by xxFelixDCatxx on 2006-08-13
> **vijirajan said:**
> I think in your command above the parameters are out of order.

```

sudo mount -t cifs //192.168.2.2/D$ /media/sharename -o username=Felix,password=*******

```

Try this

```

sudo mount -t cifs -o username=Felix,password=******* //192.168.2.2/D$ /media/sharename

```

okay tried it in that format, and got a new error code.... something is telling me that you were right and this is a move in the right direction though... I never got this one before.

input:felix@Ubuntie:~$ sudo mount -t cifs -o username=Felix,password=******** //192.168.2.2/D$ /media/sharename

output:mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

i think that error has nothing to do with linux, but has to do with server 2k3, google is activated :D

---

### Post by xxFelixDCatxx on 2006-08-13
the smiley face with sunglasses is actually supposed to be the ascii form of him eight ) i'd be afraid if code actually spat that out :)

---

### Post by vijirajan on 2006-08-13
> **xxFelixDCatxx said:**
> okay tried it in that format, and got a new error code.... something is telling me that you were right and this is a move in the right direction though... I never got this one before.

input:felix@Ubuntie:~$ sudo mount -t cifs -o username=Felix,password=******** //192.168.2.2/D$ /media/sharename

output:mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

i think that error has nothing to do with linux, but has to do with server 2k3, google is activated :D

Yeah, I agree it looks like a W2k3 error. Good luck!!!

---

### Post by xxFelixDCatxx on 2006-08-13
> **vijirajan said:**
> Yeah, I agree it looks like a W2k3 error. Good luck!!!

yea i agree, i'm going to play with permissions on that, thank you for your help, and when i get it to work I'll repost exactly how.... wish i was an admin so i could sticky this, wouldn't want anyone to go through the trouble I just did.

---

### Post by xxFelixDCatxx on 2006-08-13
aaand it's working, I just had to elevate Felix on my sever 2k3 to be a part of the administrators group and it worked straight off.  thanks for all the help.

---

### Post by vijirajan on 2006-08-13
Glad to know it worked.

---

### Post by cantormath on 2006-08-13
I have never seen it that way before...
Have you tried smbclient?
smbclient howto
```
http://info.ccone.at/INFO/Samba-2.2.12/smbclient.1.html
```

....Or smbmount
Mounting smbfs Shares Permanently Help File```

http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html
```
smbmount
```
http://webteam.waikato.ac.nz/guidelines/smbmount.shtml
```
man smbmount
```
http://www.linuxcommand.org/man_pages/smbmount8.html
```

Let me know if that helps.

---

### Post by xxFelixDCatxx on 2006-08-15
as I said the command I used up there worked, and when I applied it to the bood file /etc/fstab and changed around the .smbfcredentials in root I also got it to load on startup.

ubuntuguide.org is priceless, but one needs to keep in mind for server 2k3 and XP you must replace the 'smbf' tag with 'cifs'.

Once I did that it was cake really.

---

