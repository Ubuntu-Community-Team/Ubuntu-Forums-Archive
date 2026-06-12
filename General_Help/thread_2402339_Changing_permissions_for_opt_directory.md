---
title: "Changing permissions for /opt directory"
date: 2018-09-28
forum: General Help
---

### Post by nonetheless on 2018-09-28
Is changing the permissions for /opt directory dangerous for the system ? 

Lately I was trying to install softwares  and found out that /opt diriectory was the best place to install them.
Tried to do so, but I don't have write permissions for /opt .
This is the current permissions for opt :
```
ls -al /opt
drwxr-xr-x  2 root root 4096 Jul 20  2016 .
```

I found some blogs telling to change the ownership of /opt, some telling to change the permissions for /opt, While some telling that changing permissions can mess up with the system. 

So, here I am confused. 

Personally I don't want to change the ownership at all, I will be happy if changing permissions do the work. 
But will it make my system unstable or something worse ?

---

### Post by Dennis N on 2018-09-28
Often you put a application folder in /opt if it's not being installed by the package manager. Changing the owner (that's usually all that's necessary to have full access if for a single user) is done on the next level down - the application folder itself. I always just change the owner (and group) to my user, not the permissions.

If your user name is tom and the folder is appfolder,
```
sudo chown -R tom:tom /opt/appfolder
```

---

### Post by nonetheless on 2018-09-29
I don't get it.

You are not changing the ownership of entire /opt directory, but the owner of  application folder, right ?

But, to make that application folder in the /opt directory, you need to either change the ownership of the entire /opt directory or change the permissions of the entire /opt directory ,isn't it ? 

If not then how do you install applications in /opt directory in the first place ?

---

### Post by QIII on 2018-09-29
By temporarily elevating your user privileges with su/sudo.

---

### Post by mc4man on 2018-09-29
> **nonetheless said:**
> Is changing the permissions for /opt directory dangerous for the system ? 

Lately I was trying to install softwares  and found out that /opt diriectory was the best place to install them.

What does that mean?  Prepackaged software will install to wherever  it's built/packaged to install, on some ocassions it will be to /opt

If installing yourself manually then just use sudo.
(- note that by default /opt is not in your $PATH so any software installed to /opt will not run unless full path'd in a command or linked via a file in your $PATH

---

### Post by nonetheless on 2018-09-29
> What does that mean?  Prepackaged software will install to wherever   it's built/packaged to install, on some ocassions it will be to /opt

No, it is not packaged software, I was trying to install jdownloader. That should be installed in /opt, no ?

> If installing yourself manually then just use sudo.

What will it be then ? Is it :
```
sudo chmod g+w /opt
```

Will that include me (user account)  in the root group ?
Will that allow me(user) to install files in /opt ?

---

### Post by mc4man on 2018-09-30
> **nonetheless said:**
> No, it is not packaged software, I was trying to install jdownloader. That should be installed in /opt, no ?



What will it be then ? Is it :
```
sudo chmod g+w /opt
```

Will that include me (user account)  in the root group ?
Will that allow me(user) to install files in /opt ?

Not sure why you'd want to do that. Just run the installer script as root. (to note: you can't do that if in a wayland session, only xorg
Ex., sudo Downloads/JD2Setup_x64.sh

When run as root it would by default pick /usr/local/jd2 as install target, that would be fine.  (unless installer was previously run, then it defaults to last choice.
It would also install a .desktop file to /usr/share/applications. It would be constructed to open jdownloader from wherever you installed to so that's best way to open

Edit: also note that it can use the systray so that would only work in an OS that supports the systray, Ubuntu currently doesn't

---

