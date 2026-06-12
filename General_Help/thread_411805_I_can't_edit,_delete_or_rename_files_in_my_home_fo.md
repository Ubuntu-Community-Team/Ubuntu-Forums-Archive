---
title: "I can't edit, delete or rename files in my /home folder (file permissions)?"
date: 2007-04-17
forum: General Help
---

### Post by ChrisUK on 2007-04-17
Hi all.

For some reason I cannot delete files in my /home folder anymore. The option to delete files is grayed out, and earlier it said I didn't have permission to delete the file I wanted to delete.
I have tried loads of different files in my /home folder, and I can't delete any of them.
I have a screenshot below of a file I was trying to delete as a test, and a screenshot of my file permissions incase it helps.
I am very new to Ubuntu so I don't know much about file permissions, etc.

[IMG]http://ocuk.blighter.net/imageuploader/files/17/permissions.png[/IMG]

Any help would be appreciated. I didn't have any problems before, so I'm not sure what has changed... :confused:

---

### Post by darrenm on 2007-04-17
```
sudo chown -R $LOGNAME:$LOGNAME ~
``` :)

---

### Post by ChrisUK on 2007-04-17
> **darrenm said:**
> ```
sudo chown -R $LOGNAME:$LOGNAME ~
``` :)

I just tried that command and nothing seems to have changed...
I just tried moving that file from my Music folder to my desktop and got the following error: 

""/home/My D..._Small.jpg" cannot be moved because you do not have permissions to change it or its parent folder."

My /home folder is on a seperate partition if that makes any difference.

Here is what my partitions are like:

Windows XP MCE (NTFS)
/HOME (EXT3, all my data (music, etc)  and this should be able to be read and written from Windows and Linux)
Ubuntu / (EXT3, main Ubuntu partition)
Linux swap

I installed FS-Drive on Windows so I can see my /home EXT3 partition, maybe I need to install something on Ubuntu to allow me to write to EXT3 or something?

I don't know... :(

---

### Post by taurus on 2007-04-17
What are the outputs of these commands from a terminal?

```
cat /etc/fstab
ls -la /home
id
```

---

### Post by ChrisUK on 2007-04-17
:o 

chris@INSPIRON:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ef98edcd-4829-4b36-b85f-bcd3d8bba5ce /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=f81218fb-1765-4c6a-b80d-ec4cab6ad5b8 /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D6-0B1E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=9068AF8E68AF7220 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=07D6-0B1E  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=4829f1eb-0c6d-4aa6-8b7b-c758a5c9c07a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
chris@INSPIRON:~$ ls -la /home
total 68
drwxr-xr-x  6 root  root   4096 2007-04-17 14:47 .
drwxr-xr-x 22 root  root   4096 2007-04-17 14:47 ..
drwxr-xr-x 42 chris chris  4096 2007-04-17 15:52 chris
drwxr-xr-x  2 root  root  49152 2007-04-10 23:56 lost+found
drwxr-xr-x  5 root  root   4096 2007-04-14 17:16 My Documents2
drwxr-xr-x  2 root  root   4096 2007-04-17 14:56 Recycled
chris@INSPIRON:~$ id
uid=1000(chris) gid=1000(chris) groups=4(adm),24(cdrom),25(floppy),29(audio),44(video),46(plugdev),109(lpadmin),114(admin),1000(chris)
chris@INSPIRON:~$

---

### Post by darrenm on 2007-04-17
Try changing the /etc/fstab file to this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda7
UUID=ef98edcd-4829-4b36-b85f-bcd3d8bba5ce / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6
UUID=f81218fb-1765-4c6a-b80d-ec4cab6ad5b8 /home ext3 defaults,uid=1000 0 2
# /dev/sda1
UUID=07D6-0B1E /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2
UUID=9068AF8E68AF7220 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=07D6-0B1E /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda8
UUID=4829f1eb-0c6d-4aa6-8b7b-c758a5c9c07a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

use ```
gksudo gedit /etc/fstab
``` to do it. (Note its only one line that changes slightly)

edit: You will have to unmount and remount the partition, rebooting is easier ;)

---

### Post by ChrisUK on 2007-04-17
> **darrenm said:**
> Try changing the /etc/fstab file to this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda7
UUID=ef98edcd-4829-4b36-b85f-bcd3d8bba5ce / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6
UUID=f81218fb-1765-4c6a-b80d-ec4cab6ad5b8 /home ext3 defaults,uid=1000 0 2
# /dev/sda1
UUID=07D6-0B1E /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2
UUID=9068AF8E68AF7220 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=07D6-0B1E /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda8
UUID=4829f1eb-0c6d-4aa6-8b7b-c758a5c9c07a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

use ```
gksudo gedit /etc/fstab
``` to do it. (Note its only one line that changes slightly)

edit: You will have to unmount and remount the partition, rebooting is easier ;)

Hi,

I just done that and rebooted, but when I tried to login it said 

> "Your home directory is listed as 'home/chris' but it does not appear to exist. Do you want to login with the / (root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session.

Obviously I don't want to login with the / (root) directory as my home directory, because they are on seperate partitions, and my root directly probably isn;t big enough to handle my home directory.

What do I do now?

---

### Post by taurus on 2007-04-17
Can you post the output of this command from a terminal?

```
cat /etc/passwd
```

---

### Post by darrenm on 2007-04-17
To get out of the poo, just boot into failsafe mode and put /etc/fstab to how it was.

I can't see that adding uid=1000 into it would cause this though, I think you may have made a typo or syntax error.

When you get back into working ubuntu try changing the file again but afterwards instead of rebooting do ```
cd / && sudo umount /home && sudo mount /home
```

---

### Post by ChrisUK on 2007-04-17
It's weird because all I did was copy and paste the code you posted above.

Is failsafe mode ctrl+alt+F1 ? I have only been using Ubuntu for less than a week, so I don't know these things.
I pressed ctrl + alt + F1, logged in as root, then typed /etc/fstab and it said permission denied. :confused: 

I'm not worrying too much because my Ubuntu install has had endless amounts of problems. I can;t install my wireless card, can;t install my network, printers, etc. After installing Beryl and my Nvidia drivers, my graphics are extrememly slow for some unknown reason which I have been unable to fix.
I think I will probably reformat and install Feisty in a few days when it is released, so I am not worrying. My first experience of Ubuntu hasn;t been too good, but I am not giving up, despite all these problems I still perfer it to Windows, because it feels so much smoother, more secure and I like the way that it works. I guess it just takes a little getting use to for a noobie to Linux like me.

---

### Post by darrenm on 2007-04-17
Failsafe is pressing escape when you get to the boot prompt if it says to press esc then selecting 2.6.xx-x (recovery mode) it will drop you at a root prompt so you can edit files.

But you will need to use nano instead of gedit.

Try adding a few options to fstab such as:

user,rw,uid=1000,gid=1000

and take the defaults option out (I think thats whats causing the problem)

---

### Post by ChrisUK on 2007-04-18
> **darrenm said:**
> Failsafe is pressing escape when you get to the boot prompt if it says to press esc then selecting 2.6.xx-x (recovery mode) it will drop you at a root prompt so you can edit files.

But you will need to use nano instead of gedit.

Try adding a few options to fstab such as:

user,rw,uid=1000,gid=1000

and take the defaults option out (I think thats whats causing the problem)

Hi.

It doesn't seem to ask me to press ESC, but at the login if I press ctrl + alt + F1, I can login as root and when I typed sudo nano /etc/fstab it did show the contents of the fstab file and I can edit them, but I don't know how to save the modifications.

---

### Post by darrenm on 2007-04-18
CTRL+X and follow through :) All the nano commands are at the bottom of the screen.

---

### Post by ChrisUK on 2007-04-18
> **darrenm said:**
> CTRL+X and follow through :) All the nano commands are at the bottom of the screen.

Thanks. I just removed uid=1000 and it logged into Ubuntu fine after removing it. I am now going to remove defaults and try it again.

I have tried unmounting using the commands you gave and it said 
"umount: /home: device is busy
umount: /home: device is busy"

Even though I closed all programs, etc. :o 


I have noticed since rebooting that I now see "Debian" in the menu under Applications... I never saw that before! :confused: 

> **taurus said:**
> Can you post the output of this command from a terminal?

```
cat /etc/passwd
```

I tried pasting the code to that command on the forums, but the forums said it included over 31 images (smilie's I guess, because of all the :/ etc) so it couldn't post it.
How can I post it then?

---

### Post by taurus on 2007-04-18
Or just paste the last 10 lines.

---

### Post by ChrisUK on 2007-04-18
syslog: x:101:102:: /home/syslog: /bin/false
klog: x:102:103:: /home/klog: /bin/false
messagebus: x:103:107:: /var/run/dbus: /bin/false
avahi: x:104:108:Avahi mDNS daemon,,,: /var/run/avahi-daemon: /bin/false
cupsys: x:105:109:: /home/cupsys: /bin/false
haldaemon: x:106:110:Hardware abstraction layer,,, :/var/run/hal: /bin/false
hplip: x:107:7:HPLIP system user,,,: /var/run/hplip: /bin/false
gdm: x:108:113:Gnome Display Manager: /var/lib/gdm: /bin/false
chris: x:1000:1000:Chris,,,: /home/chris: /bin/bash
vdr: x:109:115:VDR user,,, :/var/lib/vdr: /bin/false

It wouldn't let me post these either, so I put spaces in between them.

---

### Post by akshaysrinivasan on 2007-04-18
As i see it ,all your files are now belonging to root.Not to worry though ,one or two simple commands will resolve the problem.Open the terminal and issue the commands:-

$sudo find -exec chown {your username} '{}' \;
$sudo find -exec chgrp {your username} '{}' \;
$sudo find -exec chmod u+r+w,g+r,a+r '{}' \;

Note:After issuing the sudo commands , you will be asked for your password

---

### Post by ChrisUK on 2007-04-18
> **akshaysrinivasan said:**
> As i see it ,all your files are now belonging to root.Not to worry though ,one or two simple commands will resolve the problem.Open the terminal and issue the commands:-

$sudo find -exec chown {your username} '{}' \;
$sudo find -exec chgrp {your username} '{}' \;
$sudo find -exec chmod u+r+w,g+r,a+r '{}' \;

Note:After issuing the sudo commands , you will be asked for your password

I tried those commands and I still can't move or delete any files in my /home.

Here is what it said in terminal:
chris@INSPIRON:~$ $sudo find -exec chown chris '{}' \;
chown: changing ownership of `./Examples': Operation not permitted
chown: changing ownership of `./.mozilla/firefox/07fnyjga.default/lock': No such file or directory
chown: changing ownership of `./.kde/socket-INSPIRON': No such file or directory
chown: changing ownership of `./.kde/tmp-INSPIRON': No such file or directory
chown: changing ownership of `./.wine/dosdevices/z:': Operation not permitted
chown: changing ownership of `./.googleearth/instance-running-lock': No such file or directory
chris@INSPIRON:~$ $sudo find -exec chgrp chris '{}' \;
chgrp: changing group of `./Examples': Operation not permitted
chgrp: changing group of `./.mozilla/firefox/07fnyjga.default/lock': No such file or directory
chgrp: changing group of `./.kde/socket-INSPIRON': No such file or directory
chgrp: changing group of `./.kde/tmp-INSPIRON': No such file or directory
chgrp: changing group of `./.wine/dosdevices/z:': Operation not permitted
chgrp: changing group of `./.googleearth/instance-running-lock': No such file or directory
chris@INSPIRON:~$ $sudo find -exec chmod u+r+w,g+r,a+r '{}' \;
chmod: changing permissions of `./Examples': Operation not permitted
chmod: changing permissions of `./.wine/dosdevices/z:': Operation not permitted

---

### Post by akshaysrinivasan on 2007-04-18
That's funny , from your terminal outputs ,it seems to have worked.Try 
$ls -l 
and post the output

---

### Post by darrenm on 2007-04-18
> **ChrisUK said:**
> Thanks. I just removed uid=1000 and it logged into Ubuntu fine after removing it. I am now going to remove defaults and try it again.

I have tried unmounting using the commands you gave and it said 
"umount: /home: device is busy
umount: /home: device is busy"

Even though I closed all programs, etc. :o 


I have noticed since rebooting that I now see "Debian" in the menu under Applications... I never saw that before! :confused: 



I tried pasting the code to that command on the forums, but the forums said it included over 31 images (smilie's I guess, because of all the :/ etc) so it couldn't post it.
How can I post it then?

Im sure the problem is due to the defaults option. If you remove that and add the other stuff I posted (uid=1000,gid=1000, user,rw) it should work. The problem is due to it mounting the partition as root.

---

### Post by ChrisUK on 2007-04-18
> **akshaysrinivasan said:**
> That's funny , from your terminal outputs ,it seems to have worked.Try 
$ls -l 
and post the output

It said:

bash: -l: command not found 

EDIT: When I typed sudo -l it said
 "User chris may run the following commands on this host:
    (ALL) ALL"



> **darrenm said:**
> Im sure the problem is due to the defaults option. If you remove that and add the other stuff I posted (uid=1000,gid=1000, user,rw) it should work. The problem is due to it mounting the partition as root.

I did remove the defaults option and put user,rw,uid=1000,gid=1000. Then I tried to mount and unmount the partition but it said my /home was busy or something...
When I rebooted my PC and tried to login again, it had the same message as before, saying it could not find /home existed and it wanted to add /home to my / partition again.

---

### Post by darrenm on 2007-04-18
You will need to reboot then.

---

### Post by vlad_x2 on 2007-04-18
You got a typo there ;). You should type "ls -l" (without quotes and without the $ sign) and it should output the name of the files in your home directory, their owner and permisions.
ps: The $ sign means that the command should be run as a normal user, while # means you should run the command as root. It's harder to copy them though.

---

### Post by ChrisUK on 2007-04-18
> **vlad_x2 said:**
> You got a typo there ;). You should type "ls -l" (without quotes and without the $ sign) and it should output the name of the files in your home directory, their owner and permisions.
ps: The $ sign means that the command should be run as a normal user, while # means you should run the command as root. It's harder to copy them though.

Ooops, here you go:

total 120
drwxr-xr-x   2 root root  4096 2007-04-11 13:40 bin
drwxr-xr-x   3 root root  4096 2007-04-11 13:42 boot
lrwxrwxrwx   1 root root    11 2007-04-10 23:57 cdrom -> media/cdrom
drwxr-xr-x  12 root root 13720 2007-04-18 21:51 dev
drwxr-xr-x 116 root root  8192 2007-04-18 21:53 etc
drwxr-xr-x   6 root root  4096 2007-04-18 11:37 home
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 initrd
lrwxrwxrwx   1 root root    33 2007-04-11 13:42 initrd.img -> boot/initrd.img-2.6.17-11-generic
lrwxrwxrwx   1 root root    33 2007-04-11 00:08 initrd.img.old -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x  18 root root  8192 2007-04-13 21:16 lib
drwxr-xr-x   2 root root 49152 2007-04-10 23:57 lost+found
drwxr-xr-x   6 root root  4096 2007-04-18 14:30 media
drwxr-xr-x   2 root root  4096 2006-10-19 23:49 mnt
drwxr-xr-x   3 root root  4096 2007-04-13 21:09 opt
dr-xr-xr-x 129 root root     0 2007-04-18 22:51 proc
drwxr-xr-x   2 root root  4096 2007-04-17 18:19 Recycled
drwxr-xr-x  13 root root  4096 2007-04-18 21:53 root
drwxr-xr-x   2 root root  4096 2007-04-13 21:15 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 srv
drwxr-xr-x  11 root root     0 2007-04-18 22:51 sys
drwxrwxrwt  14 root root  4096 2007-04-18 21:53 tmp
drwxr-xr-x  13 root root  4096 2007-04-13 20:59 usr
drwxr-xr-x  15 root root  4096 2006-10-25 14:39 var
lrwxrwxrwx   1 root root    30 2007-04-11 13:42 vmlinuz -> boot/vmlinuz-2.6.17-11-generic
lrwxrwxrwx   1 root root    30 2007-04-11 00:08 vmlinuz.old -> boot/vmlinuz-2.6.17-10-generic

---

