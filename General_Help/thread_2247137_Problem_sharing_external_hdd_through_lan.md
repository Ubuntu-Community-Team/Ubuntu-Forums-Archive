---
title: "Problem sharing external hdd through lan"
date: 2014-10-05
forum: General Help
---

### Post by toto8 on 2014-10-05
Hi
I bought a odroid U3, it has lubuntu 14 installed.
The thing is I want to use to download torrents and then be able to take the torrents through lan to my windows machine.
The EHDD automatically mounts on /media/odroid/toshiba , but when I share it with samba I get permission errors (you dont have permission to access) in my windows machine and cant enter the folder /media/odroid/

What can I do to make it share the files, so I can move, cut, delete the files.

PD: I cant put it to auto-mount through the disk utility to another folder like /mnt/point/ because I get [COLOR=#333333][FONT=Lucida Grande]x-gvfs-show doesnt exist.

Greetings and thanks[/FONT][/COLOR]

---

### Post by T.J. on 2014-10-06
You need to configure the access permissions to the folder you want shared in the smb.conf file.

This may help: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---

### Post by toto8 on 2014-10-06
I have the same configuration I had with 13.04 (wich worked), but now it says I dont have permission.

---

### Post by T.J. on 2014-10-06
Does the directory have the same permissions, and did you read the update notes to see if the Samba conf files can be passed from one version to the next?  You may want to check the Samba log file for errors.

---

### Post by Morbius1 on 2014-10-06
> /media/odroid/toshiba
If it's automounting under /media/odroid then odroid is a user name. /media/odroid is by design controlled by an Access Control List that limits access to anything beyond it ( like toshiba ) to odroid.

So you've got some choices:

[1] Make the samba client user appear to be odroid by placing the following line within the share definition for that share:
```
force user = odroid
```
Then restart samba:
```
sudo service smbd restart
```
[2] Or do what you originally wanted to do just don't use Disks to do it. Disks is buggy and adds silly options. Edit /etc/fstab directly and add a real mount statement:

So for an ext4 partition something like this with the correct UUID:
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/point ext4 defaults,noatime 0 2
```
For an NTFS partition something like this with the correct UUID and uid:
```
UUID=DA9056C19056A3B3 /mnt/point ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
[COLOR=#0000ff]* **EDIT**: Probably should have posted how to get the correct UUID:*[/COLOR]
```
sudo bklid -c /dev/null
```

---

### Post by toto8 on 2014-10-06
Thanks very much for the answers.

Morbius1, the first solution worked great, but the second one didnt, it said something about windows_names that it didnt exist.

Greetings

EDIT: in fstab I put:
UUID=DOF2SC7SF25C6230 /mnt/point ntfs defaults,nls=utf8,umask=000,uid=1001,windows_names 0 0

EDIT2: Any real difference between both options?

---

### Post by Morbius1 on 2014-10-07
"windows_names" is part of the ntfs-3g "driver". From "**man mount.ntfs**":
 > **windows_names**
              This option prevents files, directories and extended attributes to be created with a name  not  allowed  by  windows,
              either  because  it  contains  some  not allowed character (which are the nine characters " * / : < > ? \ | and those
              whose code is less than 0x20) or because the last character is a space or a dot. Existing such  files  can  still  be
              read (and renamed).
In short, you will get an error message if you create and then try to save a file in Linux with a name that contains "weird" characters that windows cannot interpret.

Not sure why it's missing on your install. You can always remove the option as long as you remember the constraints:
```
UUID=DOF2SC7SF25C6230 /mnt/point ntfs defaults,nls=utf8,umask=000,uid=1001 0 0
```

---

### Post by toto8 on 2014-10-07
It finally mount!!
But now when I try to run qbittorrent or copy something to the HDD in mnt/point it says permission denied, I right clicked it and the permissions say anyone on the three of them.

---

### Post by Morbius1 on 2014-10-07
I don't know what's going on there. The mount itself is read / writeable to everyone. Just go back to the "force user" in the share definition.

Since it's an ntfs partition you are sharing the two will yield the exact same results.

---

### Post by toto8 on 2014-10-07
Both methods gave the same result with qbittorrent, permission denied while trying to download.

---

### Post by Morbius1 on 2014-10-07
Crickey,

Please post the output of each one of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
testparm -s
net usershare info --long
ls -dl /mnt/point
```

---

### Post by toto8 on 2014-10-08
Sorry for the late answer.

sudo bklid -c /dev/null
/dev/mmcblk0p1: SEC_TYPE="msdos" LABEL="BOOT" UUID="6E35-5356" TYPE="vfat"
/dev/mmcblk0p2: LABEL="trusty" UUID="e139ce78-9841-40fe-8823-96a304a09859" TYPE="ext4"
/dev/sda1: LABEL="TOSHIBA EXT" UUID="D0F25C75F25C6230" TYPE="ntfs"

cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM


UUID=e139ce78-9841-40fe-8823-96a304a09859       /       ext4    errors=remount-ro,noatime,nodiratime            0 1
UUID=6E35-5356  /media/boot     vfat    defaults,rw,owner,flush,umask=000      0 0
tmpfs           /tmp    tmpfs   nodev,nosuid,mode=1777                  0 0
UUID=D0F25C75F25C6230 /mnt/point ntfs defaults,nls=utf8,umask=000,uid=1001 0 0

testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[TOSHIBA EXT]"
Processing section "[point]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        guest account = avahi
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        guest ok = Yes


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[TOSHIBA EXT]
        path = /media/odroid/TOSHIBA EXT
        force user = odroid
        read only = No


[point]
        path = /mnt/point
        read only = No

net usershare info --long
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

ls -dl /mnt/point/
drwxrwxrwx 1 odroid root 20480 oct  8 08:31 /mnt/point


Thats all that came out.

Thanks for all the time you have wasted xD

---

### Post by Morbius1 on 2014-10-08
*** If this wasn't a share of an ntfs partition there are some things I would change for instance:
> guest account = avahi
That doesn't make a whole lot of sense. If it were me I'd just remove that line from smb.conf. The system will default to "guest account = nobody". But it doesn't really matter since ntfs doesn't care.

*** There is nothing wrong with this line in fstab:
> UUID=D0F25C75F25C6230 /mnt/point ntfs defaults,nls=utf8,umask=000,uid=1001 0 0
And it's mounting exactly the way you told it to mount.
> ls -dl /mnt/point/
drwxrwxrwx 1 odroid root 20480 oct  8 08:31 /mnt/point
That will allow anyone to read and add to that partition.

*** But you stated:
> But now when I try to run qbittorrent [COLOR=#0000cd]or copy something to the HDD[/COLOR] in mnt/point it says permission denied
I don't know anything about qbittorrent but you say you can't copy something to /mnt/point and I have no explanation. It's almost as if the ntfs-3g package isn't installed. You might want to see if it is:
```
sudo apt-get install ntfs-3g
```
[COLOR=#0000cd]*That might  also explain why it doesn't understand the "windows_names" option.*[/COLOR]

If that doesn't fix it then there is something wrong with your install or something is wrong with the Toshiba Ext.

*** The bizarre thing is when you didn't have the partition mounting through fstab you said everything worked with this share, correct:
> [TOSHIBA EXT]
        path = /media/odroid/TOSHIBA EXT
        force user = odroid
        read only = No
If it still does then I would remove the fstab entry so that the system mounts to /media/odroid/TOSHIBA EXT by itself again and just use this share.

[COLOR=#0000cd]**Edit**[/COLOR]: THis is the last post for me for the day so I hope things go well for you.

---

### Post by toto8 on 2014-10-10
Still with the same problem, even after installing the ntfs-3g.
Do you know of a good distro for torrentboxs?

Greetings and thanks for all your help

---

### Post by Morbius1 on 2014-10-11
I installed Lubuntu only once. It was a long time ago and although it lacked some features present on say .. Xubuntu it was till a functional OS. Did you install it yourself or did it come with the  odroid U3?

I noticed on their website that it comes with Xubuntu already installed - at least the current version does.

If you installed it yourself I would check the install iso to make sure the md5sum numbers match: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

It could be that you started with a bad iso. ntfs-3g has been part of the base install for years now so something doesn't seem right here.

---

### Post by mikewhatever on 2014-10-17
Toto8, you may want to check the user ID of the odroid user, it might be not 1001, but 1000. Just check the output of <id>.
I use a U3 as a torrent box with Ubuntu server and transmission daemon. Runs well indeed, but the external HDD has ext4, not ntfs.

---

