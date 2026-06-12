---
title: "Screwed up user accounts"
date: 2007-10-28
forum: General Help
---

### Post by Zigi15 on 2007-10-28
Ok,hre's my problem. When I was considering convenience I changed my user account home directory from /home/users/(username) to /media/sda2/(username). Sda 2 is a non-bootable NTFS data partition. When I try to log on, errors occur and it throws me back to the login screen. 

Since I cannot log in as root and don't know the command line, **can anybody give me the code to create a new user account in the recovery mode**, so I can go in and log in as the new user and change the home directories back to normal without reinstalling ubuntu? Any help appreciated, since ubuntu is now unusable. I wrote this from windows, since I have  dual boot notebook (at least one thing that windows is good for:mrgreen::mrgreen::mrgreen:)

---

### Post by Vixis on 2007-10-28
For information: ```
man adduser
```
press **q** to quit back to the terminal.


To add new user:
```
adduser **username**
```

You may need to specify new user home directory:
```
adduser **username** --home /home/**username**
```

change **username** with your new user name

---

### Post by Sunforge on 2007-10-28
This looks like a good guide:

[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

The quick and dirty way culled from the above would be:

sudo adduser <username>

You should then be walked through the creation of a new account.

---

### Post by Vixis on 2007-10-28
better command usermod
```

usermod --home HOME_DIR -m USERNAME
```


--home HOME_DIR
          The user’s new login directory. If the -m option is given the contents of the current home directory will be
          moved to the new home directory, which is created if it does not already exist.

---

### Post by Zigi15 on 2007-10-28
Thanks guys. Really appreciate it. You make the ubuntu community live. Keep up the good work!:)

---

### Post by Zigi15 on 2007-10-28
DAMN! Now I don?t have admin priviliges to even access the settings! When I try to tick "users and groups it automatically unticks.

Now how about creating a new admin account?

---

### Post by Thyme on 2007-10-28
This is currently a critical  bug in Ubuntu. Check the following link for more info:

[[COLOR="Red"]https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/26338[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/26338")

---

### Post by Zigi15 on 2007-10-28
So what you're saying is that I won't be able to work my way out of this for a few months or even have to reinstall?

Maybe code for changing a users default directory?

---

### Post by Thyme on 2007-10-28
You can use the CD to boot into recovery mode and use "passwd" to change your password. 

Try:

passwd <username>

(where username is the account whose password you want to change).

Hope everything goes well :)

---

### Post by Zigi15 on 2007-10-28
You seem to have misunderstood. My password works well. The problem is that my default user directory is set on a NTFS partition! When I log on, it says: User must be the owner of $HOME folder and then: Your session lasted less than 10 seconds. If you didn't log off yourself, the problem might be in inadequate disk space...

Again:

**I need to somehow change the default home user directory from /media/sda2/(username) to /home/(username) with the command line!**

---

### Post by Thyme on 2007-10-28
Oh, sorry about that. The only way to sought it out is by logging in to a terminal and doing what vixis said in his second post. You have to log into a  terminal as root with control+alt+F5 or (some other F keys). Or use the CD to boot into recovery mode. You won't be able to use any of the X apps. The CD is probably your best bet ..

---

### Post by Zigi15 on 2007-10-28
> **Vixis said:**
> better command usermod
```

usermod --home HOME_DIR -m USERNAME
```


--home HOME_DIR
          The user’s new login directory. If the -m option is given the contents of the current home directory will be
          moved to the new home directory, which is created if it does not already exist.

Thanks, now that helped immediately. Now I'm up and Ubuntuing!:)

---

