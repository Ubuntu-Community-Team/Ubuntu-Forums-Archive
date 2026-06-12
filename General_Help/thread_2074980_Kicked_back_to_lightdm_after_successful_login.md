---
title: "Kicked back to lightdm after successful login"
date: 2012-10-22
forum: General Help
---

### Post by rotten777 on 2012-10-22
I start my 12.10 box up, toggle between terminals to get the decryption prompt up, then lightdm follows shortly thereafter. I login as myself with my normal session and get some text on a black screen then BAM I'm back at lightdm's login. 

[LIST]
[*]I've purged unity and compiz, no fix. 
[*]I've created a new user to see if it was the graphics environment or something else and it works normal in a testing user.
[*]I've installed different desktop environments and they still don't work with MY user, but they were just fine with the testing user
[/LIST]

I don't even know where to begin looking for a log to see what's killing my session.

SOLVED!!!
If anyone else runs into this, this is the culprit. 
```
matthew@hws:~$ ls -l ~/.Xauthority 
-rw------- 1 matthew matthew 48 Oct 22 20:44 /home/matthew/.Xauthority

```

It was owned by root and I did a quick 'sudo chown' and rebooted. :guitar:

---

### Post by ghostrecon on 2012-11-05
i have the same problem. Can you give me the command you used to change the ownership ?

Is it like this ? sudo chow 777 ~/.Xauthority 

Thanks

---

### Post by Wim Sturkenboom on 2012-11-05
> **ghostrecon said:**
> i have the same problem. Can you give me the command you used to change the ownership ?

Is it like this ? sudo chow 777 ~/.Xauthority 

ThanksThat will make user 777 the owner of the file ;)
Try
```

sudo chown youruser:yourgroup ~/.Xauthority

```
Replace youruser and yourgroup in above command with the actual username and primary group name of your user.

---

### Post by rotten777 on 2012-11-05
> **ghostrecon said:**
> i have the same problem. Can you give me the command you used to change the ownership ?

Is it like this ? sudo chow 777 ~/.Xauthority 

Thanks

exactly what the previous poster said. normally your group name is also your username. in my instance, it is my first name.

```
sudo chown matthew:matthew ~/.Xauthority
```

---

### Post by Wim Sturkenboom on 2012-11-05
Maybe I should have added how to find your group ID. In the below example the command is _id_, uid is your userid(username) and gid(groupname) is the id of the primary group that the user is a member of.

```

wim@i3-2120:~$ **[COLOR="Red"]id[/COLOR]**
uid=1000(wim) gid=1000(wim) groups=1000(wim),4(adm),24(cdrom),27(sudo),30(dip),33(www-data),46(plugdev),109(lpadmin),124(sambashare),125(vboxusers)
wim@i3-2120:~$ 

```
It depends on the distro if the primary group is the same as the user. Some distros use the group _user(s?)_ as the primary group for normal users.

---

### Post by rotten777 on 2012-11-05
> **Wim Sturkenboom said:**
> Maybe I should have added how to find your group ID. In the below example the command is _id_, uid is your userid(username) and gid(groupname) is the id of the primary group that the user is a member of.

```

wim@i3-2120:~$ **[COLOR="Red"]id[/COLOR]**
uid=1000(wim) gid=1000(wim) groups=1000(wim),4(adm),24(cdrom),27(sudo),30(dip),33(www-data),46(plugdev),109(lpadmin),124(sambashare),125(vboxusers)
wim@i3-2120:~$ 

```
It depends on the distro if the primary group is the same as the user. Some distros use the group _user(s?)_ as the primary group for normal users.

Do Ubuntu/Debian variants do this???

---

### Post by ghostrecon on 2012-11-05
ok I typed the command:

```
sudo chown suhaib:suhaib ~/X.authority 
```

however I was kicked out :confused:

the ls-l

```
-rw------ 1 suhaib suhaib 0 Nov 2 01:37 /home/suhaib/.Xauthority
```
.

Before upgrading to 12.10 I was using 12.04. I decided to install Lubuntu Kubuntu openbox and cinnamon desktops . I already had gnome installed.

So i wanted to use cinnamon instead of gnome. I logged in cinnamon and I was stuck there. Every-time I want to log out I was kicked back to cinnamon.

Now I upgraded to 12.10, I cannot even log back to cinnamon desktop environment

I think I will reinstall Ubuntu. :-))

---

### Post by Wim Sturkenboom on 2012-11-06
> **rotten777 said:**
> Do Ubuntu/Debian variants do this???Although not sure, I think they do. One of the one that uses 'users' is Slackware.

---

