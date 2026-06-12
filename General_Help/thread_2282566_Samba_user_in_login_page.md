---
title: "Samba user in login page"
date: 2015-06-15
forum: General Help
---

### Post by mayasl on 2015-06-15
Hi,

I created a samba share at home. I created a samba user for others at home to login to the share with their devices.

Now the issue is, 
the secondary account which I created for others at home, shows up in the Ubuntu login screen. Also, under the System Settings > User Accounts. I do not want that credential to be used to login to my system, but only for samba share.

Please help me!

---

### Post by nerdtron on 2015-06-15
> I do not want that credential to be used to login to my system, but only for samba share. 

Ok so you added another user to the computer right? I assume you use the "smbpasswd" command to declare the samba password of the other user right? Did you also declare the account password using "sudo passwd username" command?

passwd ----> command to set password for a user account on the system. If you did not declare a password for a user account, they won't be anble to login to the computer
smbpasswd -----> command to set the Samba password of a User. This is different from the user account password. This is only used to connect to samba shares. You won't be able to login to the computer using this password. (unless, of course, the user account password is the same as this)

---

### Post by mayasl on 2015-06-15
> **nerdtron said:**
> Ok so you added another user to the computer right? I assume you use the "smbpasswd" command to declare the samba password of the other user right? Did you also declare the account password using "sudo passwd username" command?

passwd ----> command to set password for a user account on the system. If you did not declare a password for a user account, they won't be anble to login to the computer
smbpasswd -----> command to set the Samba password of a User. This is different from the user account password. This is only used to connect to samba shares. You won't be able to login to the computer using this password. (unless, of course, the user account password is the same as this)

mm.. hmm.. I guess I have messed up there. :D

When I created the samba user I created as below.
```
addgroup [group-name]
adduser [user-name] -G [group-name]
smbpasswd -a [user-name] 
```

But, after sometime I forgot the password of that acc and changed it using "sudo passwd [user-name]". 

Is that the reason why it is showing as a system account?

Do we have a fix?

---

### Post by nerdtron on 2015-06-15
> **mayasl said:**
> mm.. hmm.. I guess I have messed up there. :D

When I created the samba user I created as below.
```
addgroup [group-name]
adduser [user-name] -G [group-name]
smbpasswd -a [user-name] 
```

But, after sometime I forgot the password of that acc and changed it using "sudo passwd [user-name]". 

Is that the reason why it is showing as a system account?

Do we have a fix?

You can reset the samba password by running the smbpasswd command again without using -a option. But in this case, you can just delete the user and start allover again.

Delete samba user and remove system user account along with home directory
```
smbpasswd -x [username]
deluser --remove-home [username]
```

Then recreate the samba user:
```
adduser [user-name] -G [group-name]
smbpasswd -a [user-name]
```

Don't use the "sudo passwd [user-name]" on this user so that he won't be able to login using a normal user account.

---

### Post by mayasl on 2015-06-16
> **nerdtron said:**
> You can reset the samba password by running the smbpasswd command again without using -a option. But in this case, you can just delete the user and start allover again.

Delete samba user and remove system user account along with home directory
```
smbpasswd -x [username]
deluser --remove-home [username]
```

Then recreate the samba user:
```
adduser [user-name] -G [group-name]
smbpasswd -a [user-name]
```

Don't use the "sudo passwd [user-name]" on this user so that he won't be able to login using a normal user account.

I was able to delete system & samba user accounts. But, when I executed "adduser [user-name] -G [group-name]" I got the following. 

```
Option g is ambiguous (gecos, gid, group)
adduser [--home DIR] [--shell SHELL] [--no-create-home] [--uid ID]
[--firstuid ID] [--lastuid ID] [--gecos GECOS] [--ingroup GROUP | --gid ID]
[--disabled-password] [--disabled-login] [--encrypt-home] USER
   Add a normal user

adduser --system [--home DIR] [--shell SHELL] [--no-create-home] [--uid ID]
[--gecos GECOS] [--group | --ingroup GROUP | --gid ID] [--disabled-password]
[--disabled-login] USER
   Add a system user

adduser --group [--gid ID] GROUP
addgroup [--gid ID] GROUP
   Add a user group

addgroup --system [--gid ID] GROUP
   Add a system group

adduser USER GROUP
   Add an existing user to an existing group

general options:
  --quiet | -q      don't give process information to stdout
  --force-badname   allow usernames which do not match the
                    NAME_REGEX[_SYSTEM] configuration variable
  --help | -h       usage message
  --version | -v    version number and copyright
  --conf | -c FILE  use FILE as configuration file
```

---

### Post by nerdtron on 2015-06-16
-G denotes add to secondary group.

If you are adding a new user and assign to a specific group. Then try: "sudo useradd [username] -g [groupname]"

---

### Post by mayasl on 2015-06-16
> **nerdtron said:**
> -G denotes add to secondary group.

If you are adding a new user and assign to a specific group. Then try: "sudo useradd [username] -g [groupname]"

That shows the new account under system user accounts.

---

### Post by nerdtron on 2015-06-16
It will. But if you don't declare a passwd for the user he won't be able to login. This is because the behavior for GUI systems.

---

### Post by mayasl on 2015-06-16
> **nerdtron said:**
> It will. But if you don't declare a passwd for the user he won't be able to login. This is because the behavior for GUI systems.

Does that mean there is no solution for my issue?

---

### Post by nerdtron on 2015-06-16
None that I'm aware of.  I haven't used samba for GUI systems.

---

### Post by mayasl on 2015-06-16
> **nerdtron said:**
> None that I'm aware of.  I haven't used samba for GUI systems.

Oh okay! Thank you so much for your assistance. :)

---

### Post by bab1 on 2015-06-16
> **mayasl said:**
> Hi,

I created a samba share at home. I created a samba user for others at home to login to the share with their devices.

Now the issue is, 
the secondary account which I created for others at home, shows up in the Ubuntu login screen. Also, under the System Settings > User Accounts. I do not want that credential to be used to login to my system, but only for samba share.

Please help me!
This is cetainly something that you can do.  It will be helpful for you to understand what types of Linux (Ubuntu) users there are.  The types of users are
[LIST]
[*]The root user -- The super user (administrator) uid=0
[*]System user -- users with no login uid 2 to 999 on Ubuntu
[*]Mortal user -- Users with login and home directories at /home uid 1000 >
[*]
[/LIST]
Usually system users are for processes that are running on the host (i.e. printer, web server, dns server etc).  You can create system accounts for for what you need.  Samba will provide the access to the share and a system account will allow the user to read and write to that share without the ability to log in directly to the host machine.

In the following example <user> is the user name you want to assign to the account and <UID> is the uid you want to assign to the user.  You can set the group with a GID if you wish.  I used the group *nogroup*  The system user UID's for Ubuntu are 2 to 999.  Rarely are the UID's above 500 are used.  You can use those to keep this type of system user separated from the other type of system users.  The following incatation will make the user you need```

sudo adduser --quiet --system --ingroup nogroup --no-create-home --disabled-password --uid <uid>  <user>

``` ...Now you just add that user to the Samba database with```
sudo smbpasswd -a <user>
```

I have added just such a user (smbtest) and it looks like this from the Linux perspective```
smbtest:x:500:65534::/home/smbtest:/bin/false
```...Note that there is a home directory listed but none has been created.  Also there is no shell so there is no ability to login.

The samba database shows the user with ```
sudo pdbedit -L

smbtest:500:
```

I created a file and directory as the Samba user ```
drwxr-xr-x  2 smbtest nogroup 4.0K Jun 16 11:59 smbtest
```... and a file in that directory```
-rwxr--r-- 1 smbtest nogroup 0 Jun 16 11:56 smbtest.txt
```

Some adjustments might be needed to get exactly what you want, but the basics are there.

---

### Post by mayasl on 2015-06-17
@bab1 Wow! Thanks for such a detailed explanation. I got it now! :)

---

