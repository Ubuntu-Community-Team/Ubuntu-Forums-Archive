---
title: "Mounting an FTP share at startup"
date: 2013-09-21
forum: General Help
---

### Post by XBNCPRk on 2013-09-21
Like the title says, Im having issues with mounting an FTP share at startup.

Its hosted by the wifi router as usb attached storage and is otherwise accessable if I look it up manually, or mount it from the terminal using curlftpfs, so its not a config issue with the share itself.

Ive tried appending ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo curlftpfs -o umask=0777,uid=1000,gid=1000,allow_other [/FONT][/COLOR][ftp://username:password@your.ftpserver.here]("ftp://username:password@your.ftpserver.here/")[COLOR=#000000][FONT=Ubuntu Mono] /media/ftpmountedhere [/FONT][/COLOR]
``` to the tail end of my rc.local file, as well as a comparable line to my fstab file. 

Neither work though, I assume because they both execute well before unity (and therefor the network manager and wifi connection) starts. Is this correct?

Im guessing the way to go about it then is to append a script to init.d to mount the share, but Im still iffy on how to go about that...any help would be appreciated.


EDIT: Marked as solved since the other issues are unrelated to the original problem

---

### Post by Morbius1 on 2013-09-21
I've never mounted an ftp share at boot before but if the only problem is a timing issue of having it execute before the network itself is established I may have something to try. 

Set this up in fstab like you had it before and make sure it actually works by running the following command:
```
sudo mount -a
```
If it works then create a file:
```
 gksu gedit /etc/network/if-up.d/fstabmount
```
With this content:
```
#!/bin/sh
mount -a
```
Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstabmount
```
Any script placed in /etc/network/if-up.d will be executed only after the network is up.

I have used this techinique in the past with samba shares.

---

### Post by XBNCPRk on 2013-09-21
Thanks for the quick reply! 
I didnt even think about tossing the script into the network folder like that.
 
Is there any reason though I cant just add the commands to mount the drive right in that script, rather than having it remount all the other drives as well from the fstab file? The FTP share is to maintain an offsite backup, so itd be nice to be able to mount it and rsync the necessary files all in the same script.

---

### Post by Morbius1 on 2013-09-21
I've never done it that way but I see no reason why it wont work.

I used to have several lines representing different servers in fstab so it was a convenient way to keep them all in one place. 

A "mount -a" isn't going to remount things that are already mounted only the one's that have failed to mount for whatever reason.

---

### Post by XBNCPRk on 2013-09-21
I went ahead and used the fstab commands to mount the FTP share (good call about keeping all the mounting commands and options in the fstab file), but am unable to add other things to the network/is-up.d script that mounts the share. 

Do other commands like ls, cp, rm, and rsync need to be prefaced with something else to make the shell execute them?

```
#!/bin/sh
mount -a #this line works
ls /list/some/files > /heres/the/list.txt #this line doesnt run
cp /heres/the/list.txt /ftp/share/list.txt #also doesnt run

```

---

