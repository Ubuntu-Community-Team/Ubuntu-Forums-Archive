---
title: "Accessing home partition of preveous install."
date: 2008-04-02
forum: General Help
---

### Post by djbsteart1 on 2008-04-02
After installing kubuntu on sda7, sda5 as home and sda6 as media I would like to access my preveos installs home folder on sda5 and the install before that on sda6, both of the preveous installs were Mandriva if that makes any difference. 
When I open sda6 and go to home, I can access guest but not donald, which is where my files are, and the same is true of sda5. Both the folders are locked and I cant see a way of opening them.

Thanks in advance.
Donald.

---

### Post by ibuclaw on 2008-04-02
I think that is because the permissions are still set to your old username. (Or root)

ie:
If your new username is different. Then you won't have access to it.

Have you tried changing the ownership and the permissions of the home folder?

```

chown **username:username** home -R
chmod 755 home -R

```

Where "username" is your current username for your current install of Linux.

Regards

---

### Post by djbsteart1 on 2008-04-02
No but the user name was the same and the password. However the root password wasn't the same, with *buntu not having one. 

The command gave an error 
"username:donald unknown"

So I tried ```
chown username: donald home -R
```

Which gave the error "cannot get the login group of a numeric UID"

Thanks.

---

### Post by ibuclaw on 2008-04-02
Sorry.

To explain it a bit better.

The way chown works is that it sets it by **owner:group**

So both inputs either side of the colon are a username followed by the groupname.

So the reason that the error you got happened was because there isn't a user named "username" on your system.

Also, "home" should be replaced with the name of the folder.

```
 chown donald:donald donald -R 
```
should will do it with no problems.

Also, make sure that you are in your home folder.

So do this beforehand.
```

cd /home

```

Regards
Iain

---

### Post by bodhi.zazen on 2008-04-02
If you just need access to the files, use root powers :

```
gksu nautilus
```

Navigate to the mount point.

If you change ownership and permissions of the old /home you will likely have difficulty booting.

If you no longer use the old distros, you can change ownership and permissions of the mount points.

Ex:

```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo chown user.user -R /media/sda5
chmod -R 770 /media/sda5
```

Change user.user to your (Ubuntu) log in name, ie
 
sudo chown donald.donald /media/sda5

---

### Post by djbsteart1 on 2008-04-02
Thanks thats done it. I see where I went wrong, No I needed read/write access which I now have, 
Thanks.

---

