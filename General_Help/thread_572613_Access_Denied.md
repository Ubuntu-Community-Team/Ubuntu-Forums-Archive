---
title: "Access Denied"
date: 2007-10-10
forum: General Help
---

### Post by messagesend on 2007-10-10
I just installed formatted and mounted a second HDD. like this:
sudo mount -t ext3 /dev/hdb1 /mnt/diskb
that seems to have gone smoothly. i see the disk there in the /mnt folder.

only trouble is, im not allowed to write anything to it. nothing but access denied messages. wont even let me make a new folder in it. its just sitting there, and every time i reboot it unmounts itself. i really appreciate anyones effort to help.

---

### Post by jocko on 2007-10-10
> **messagesend said:**
> I just installed formatted and mounted a second HDD. like this:
sudo mount -t ext3 /dev/hdb1 /mnt/diskb
that seems to have gone smoothly. i see the disk there in the /mnt folder.

only trouble is, im not allowed to write anything to it. nothing but access denied messages. wont even let me make a new folder in it. its just sitting there, and every time i reboot it unmounts itself. i really appreciate anyones effort to help.

To get it to mount automatically on boot, you'll have to add a line in /etc/fstab. This should do it:
```
gksudo gedit /etc/fstab
```Add this line:
```
/dev/hdb1 /mnt/diskb           ext3    defaults        0       2
```Mount it by this command:
```
sudo mount -a
```If you still don't get write permissions to the partition, try setting yourself as owner:
```
sudo chown -R [COLOR=Red]user[/COLOR]:[COLOR=Red]group[/COLOR] /mnt/diskb
```Where both [COLOR=Red]user[/COLOR] and [COLOR=Red]group[/COLOR] is your username.

---

### Post by messagesend on 2007-10-11
huzzah!
sudo chown -R user:group /mnt/diskb
that was exactly the code i needed to give me access privileges. thankyou for your assistance jocko.

---

### Post by georanma on 2007-10-21
Im having a similar problem...except when im in my gui for ubuntu gusty gibon. I tried to run the line of code that was posted above and i get an error of no such directory..im guessing thats cause im typing the wrong name...

My windows install however wil see it.

---

### Post by georanma on 2007-10-21
Im having a similar problem...except when im in my gui for ubuntu gusty gibon. I tried to run the line of code that was posted above and i get an error of no such directory..im guessing thats cause im typing the wrong name...

My windows install however will see it.

---

### Post by lavinog on 2007-10-21
> Im having a similar problem...except when im in my gui for ubuntu gusty gibon. I tried to run the line of code that was posted above and i get an error of no such directory..im guessing thats cause im typing the wrong name...

you have to make the folder that you will be mounting the drive too
```
mkdir /mnt/diskb
```
then do the above commands

> My windows install however will see it.
could this be a ntfs partition you are trying to mount instead of an ext3 partition?

---

### Post by georanma on 2007-10-21
yea...and thanks for the quick responses

---

