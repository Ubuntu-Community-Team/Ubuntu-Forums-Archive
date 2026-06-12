---
title: "Mount sharefolder"
date: 2024-03-12
forum: General Help
---

### Post by Barsoianu Radu on 2024-03-12
Hello,

VLC isn't able to play any movies from a smb location, so i understood going through this forum that making a permanent mount should solve the problem. This is what i have in fstab :

[FONT=monospace][COLOR=#000000]//192.168.50.1/Samsung_USB /home/radu/Sharefolder cifs credentials=/home/radu/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0 [/COLOR]

and i get in dmesg :

[/FONT][FONT=monospace][COLOR=#18b218][ 1169.768853] [/COLOR][COLOR=#b26818]CIFS[/COLOR][COLOR=#000000]: Attempting to mount //192.168.50.1/Samsung_USB [/COLOR]
[COLOR=#18b218][ 1169.773184] [/COLOR][COLOR=#b26818]CIFS[/COLOR][COLOR=#b21818]: VFS: cifs_mount failed w/return code = -22[/COLOR]


If i try to use the same line in fstab but with smb:// i get the following running sudo mount -a

[/FONT][FONT=monospace][COLOR=#000000]Mounting cifs URL not implemented yet. Attempt to mount smb://192.168.50.1/Samsung_USB[/COLOR]

I see no error in dmsg, however the mount does not work. I checked all the folders are correctly written, the .smbcredentials does exist and it contains the right user and password, and the user is added to samba. Accessing [/FONT]smb://192.168.50.1/Samsung_USB/ from Dolphin works correctly and opens the share. [FONT=monospace]Any ideas on what I'm doing wrong ?

Thanks,
Radu
[/FONT]

---

### Post by Morbius1 on 2024-03-13
The most common reason for the "-22" error is a missing package:
```
sudo apt install cifs-utils
```
This allows you to connect to the Linux in-kernel CIFS filesystem.

I think you would get a different error message but there may also be a samba dialect mismatch.

Install nmap
```
sudo apt install nmap
```
Then run this command to see what smb dialects the server understands:
```
nmap -Pn --script smb-protocols 192.168.50.1
```
By default cifs will use smb dialects between SMB2.1 to SMB3.11.

If nmap only comes back with something like NT1, SMB1, or SMB2.0X it will not be able to connect. 

You can override this default behavior by adding a "vers" directive to you mount statement, like this:
>  //192.168.50.1/Samsung_USB /home/radu/Sharefolder cifs credentials=/home/radu/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777,**[COLOR="#FF0000"]vers=1.0[/COLOR]** 0 0 

Or vers=2.0

*[COLOR="#0000FF"]Note: I'm assuming the space in "f ile_mode=0777" is a typo or that odd thing the forum software does and you meant to write "file_mode=0777"[/COLOR]*

---

### Post by Barsoianu Radu on 2024-03-13
Hi,

First of all, thanks for the reply, everything starts to make sense now :). For cifs-utils, i can confirm that it is installed. I know i've read somewhere about using version 1 of samba with cifs, completely forgot about it and i did not know that i can use nmap to interogate the version neither. Currently at work, will come back as soon as I get home and try to force version 1. 

p.s yes, the space is the odd thing of this forum, if I try to edit the initial post the space is not showing anymore.

Thanks again, 
Radu

---

### Post by Barsoianu Radu on 2024-03-13
[FONT=monospace][COLOR=#000000]Host script results: [/COLOR]
| smb-protocols:  
|   dialects:  
|     NT LM 0.12 (SMBv1) [dangerous, but default] 
|_    2.02 



Added vers=1.0 and everything worked. Many thanks !!!

As a note, trying to download torrents using either qbit or ktor directly into the mounted folder resulted in both torrent program and dolphin crashing. Modified to version 2 and everything works. 
[/FONT]

---

