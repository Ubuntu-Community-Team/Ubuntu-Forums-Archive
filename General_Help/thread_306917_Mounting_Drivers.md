---
title: "Mounting Drivers"
date: 2006-11-25
forum: General Help
---

### Post by tehhaxorr on 2006-11-25
Thanks for below post, exactly what i needed.

---

### Post by pay on 2006-11-25
You need to add it to your fstab file
```
sudo nano /etc/fstab
```an example would be this```
/dev/hdc3        /home/$USER/multimedia       ext3    defaults                0 1

```but you will need to change /dev/hdc3 to your partition and ext3 to your filesystem.

---

### Post by junglepeanut on 2006-11-25
I think you could add something in your .profile

I am not sure exactly how you could do it, but the best way would probably be to make a script that does what you want, then have your profile run the script on log in every time. Or you could just make the profile do all the commands too. Might require a little research but should not be to difficult.

---

### Post by junglepeanut on 2006-11-25
Woops, missed the post above mine, sounds a lot better than mine.

---

### Post by syadnom on 2006-11-25
keep in mind your file permissions on the mounted drive will have to match your user rights.

chmod a+wrx /path/to/directory

will completely allow access to the drive but for all users.  otherwise you could

chmod -R a-wrx /path/
then
chmod -R 100+wrx /path (if you user id is 100, else use user id)

then only you and root can read,write,execute.

this stuff would only need done once unless root writes a file then  the last line would need run again.

---

