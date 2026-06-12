---
title: "Mounting problem"
date: 2007-01-15
forum: General Help
---

### Post by pod25 on 2007-01-15
I've got 2 windows ntfs drives mounted at :
> /dev/hdg1  /media/windows  ntfs  suid,dev,umask=0222,exec,nls=utf8  0  0
> /dev/hdk1  /mnt/windows  ntfs  suid,dev,umask=0222,exec,nls=utf8  0  0

Now I want to mount 1 folder from hdg1
and
1 from hdk1 into  :
> /etc/skel/ftp-skel/

whats the command to do this ?

---

### Post by taurus on 2007-01-15
Just change the mount points for those two partitions to wherever you want to mount them in /etc/fstab!  However, you need to keep in mind that you cannot write to ntfs (unless you have installed ntfs-3g) right now.  So, don't try to write to those two partitions.

---

### Post by pod25 on 2007-01-15
> **taurus said:**
> Just change the mount points for those two partitions to wherever you want to mount them in /etc/fstab!  However, you need to keep in mind that you cannot write to ntfs (unless you have installed ntfs-3g) right now.  So, don't try to write to those two partitions.

No I will not be wanting to write to them, well not via ubuntu .

And your suggestion won't work, I only want and need 2 folders, 1 from each drive placing into the /etc/skel/ftp-skel/  folder . 
Reason being , I have a script that auto creates ftp accounts and adds the data into a mysql database, it copies the contents of the /ftp-skel/ folder into the users /home/ folder.
Which is why I do not need the entire hard drive mounting into the /ftp-skel/ folder.

---

### Post by bodhi.zazen on 2007-01-15
Mount the drives, make links:

suod ln -s /media/windows/folder_to_link /etc/skel/ftp-skel/folder_name
suod ln -s /mnt/windows/folder_to_link /etc/skel/ftp-skel/folder_name

---

### Post by sparky-steve on 2007-01-15
Could this be what you are after?

```
mount --bind olddir newdir
```

that's what I used to extend my home directory, by adding a dir called "Stuff" or whatever, then using mount:

```
mount --bind /mnt/newharddrive/directory /home/steve/Stuff
```

Hope that helps

Steve

---

### Post by pod25 on 2007-01-15
> **bodhi.zazen said:**
> Mount the drives, make links:

suod ln -s /media/windows/folder_to_link /etc/skel/ftp-skel/folder_name
suod ln -s /mnt/windows/folder_to_link /etc/skel/ftp-skel/folder_name

I will give that a go and post back if it works out ok.

---

### Post by pod25 on 2007-01-15
I tried using
> mount --bind /media/windows/MP3/  /etc/skel/ftp-skel/

But nothing happened !

I also tried 
> sudo ln -s /media/windows/MP3  /etc/skel/ftp-skel/

and again, nothing happened !

---

### Post by bodhi.zazen on 2007-01-15
What do you mean nothing happened ?

list the contents of /etc/skel/ftp-skel/ and see what we have.

---

### Post by pod25 on 2007-01-15
> **bodhi.zazen said:**
> What do you mean nothing happened ?

list the contents of /etc/skel/ftp-skel/ and see what we have.

My mistake, it took a refresh to see the contents.
What yours did was to copy the contents of /MP3/ rather than the entire folder.
Then when i use my script to create the account , it only copies 1 of 6 folders over !!!, but if the entire folder of /MP3/  was in the /ftp-skel/  then i'm sure i wouldn't have a problem.

So i'm almost there.

---

### Post by bodhi.zazen on 2007-01-15
It is hard for me to visualize ....

Unlink all that stuff and then remove it:```
sudo unlink <file_name>
sudo rm <file_name>
```

Now try this:

sudo ln -s /media/windows/MP3 /etc/skel/ftp-skel/MP3

Assuming I am following what it is you want ??

---

### Post by pod25 on 2007-01-15
> **bodhi.zazen said:**
> It is hard for me to visualize ....

Unlink all that stuff and then remove it:```
sudo unlink <file_name>
sudo rm <file_name>
```

Now try this:

sudo ln -s /media/windows/MP3 /etc/skel/ftp-skel/MP3

Assuming I am following what it is you want ??

You are assuming correctly  ...  however  ..   

Cannot unlink  ...  Read Only File System

---

### Post by bodhi.zazen on 2007-01-15
That should be OK.

Delete the file(s) from /etc/skel/ftp-skel

and see if the new link works [-o<

I think it should ...

---

### Post by sparky-steve on 2007-01-16
> **pod25 said:**
> I tried using

mount --bind /media/windows/MP3/ /etc/skel/ftp-skel/

But nothing happened !

I also tried 

sudo ln -s /media/windows/MP3 /etc/skel/ftp-skel/

and again, nothing happened !


I am suprised that the mount didnt either work or give you an error, and I'm quite certain this is the best command for you, given the explanation you've given of what you want.  I have had a few occasions where ln worked on the O/S level, but not at the FTP daemon level.

This command puts a hard link from the old dir to the new dir, so that they are identical; any changes made to one are reflected in the other, but with only one set of data, if that makes any sense.

Steve

---

### Post by pod25 on 2007-01-16
Right then.
I got both methods to work, must of been a stupid typo on my behalf.

Now this method won't work : ```
sudo ln -s /media/windows/MP3 /etc/skel/ftp-skel/
``` Reason being, once I run my script, that then creates another shortcut, then when I connect via FTP it is trying to view a shortcut to a shortcut to a mounted drive, I'm sure you can see the problem there.

This method will work : ```
mount --bind /media/windows/MP3/ /etc/skel/ftp-skel/
```  and both the folders I required which then contain several sub-folders are hard copied to the skeleton folder.

However when I run my script, it seems to randomly pick 1 folder and 1 sub-folder, WTF is going on there ?

Below is my script I'm using, if you find any faults in the script then please let me know.
```

#!/bin/bash
#BEGIN
MYSQL_PATH=/usr/bin
MYSQL_USER=root
MYSQL_PASS=password
MYSQL_DBNAME=ftp

FTP_HOMEDIRS="/home/ftp"
HOME_TEMPLATE="/etc/skel/skeleton"


SECURITY_MODE=0755

USERNAME=$1
PASSWORD=""

echo -ne "Password: "
read PASSWORD

$MYSQL_PATH/mysql -u $MYSQL_USER -p$MYSQL_PASS $MYSQL_DBNAME -e "INSERT INTO ftpuser(userid, passwd, homedir) VALUES('$USERNAME',('$PASSWORD'), '$FTP_HOMEDIRS/$USERNAME')"

cp -R $HOME_TEMPLATE $FTP_HOMEDIRS/$USERNAME
chmod -R $SECURITY_MODE $FTP_HOMEDIRS/$USERNAME

#END 
```

---

### Post by sparky-steve on 2007-01-16
I am glad that the mount command worked for you.

I'm sorry, but this is where I bail out - the mere sight of the letters S, Q & L together send shivers down my spine...... I know nothing about it.

Good luck!
Steve

---

