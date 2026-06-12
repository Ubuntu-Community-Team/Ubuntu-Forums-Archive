---
title: "Sudo with graphical application help"
date: 2022-03-16
forum: General Help
---

### Post by mongo42 on 2022-03-16
Hi all,

I have a general question concerning the use of sudo to invoke a graphical application from the command line with root privileges.  From my reading, I find that that the use of sudo with a GUI is dangerous, in that it could potentially allow root to take ownership of system files I need to own.  The rub is, that I read this too late, and already opened the app in question and made the needed changes:  I needed to open VMWare Workstation as root to change the default memory management option.  The changes were successful, I have no problem logging in, and I have not noticed anything broken.  My research tells me that I may have corrupted my environment.  My question is, can I conclude from the fact that I can login fine and have noticed no ill effects that I dodged a bullet here?  Are there any tell-tale signs that I have corrupted my OS install?  One site tells me that I can safely use sudo with the -H argument to make sure ROOT stays in its own environment... is this accurate?  Thanks!

---

### Post by TheFu on 2022-03-16
It isn't system files. It is the files+directories in your HOME directory which could be owned by root which is the failure. If the files + directories already exist, the ownership will not be changed to root, so there aren't any issues, but if the files (especially config files) do not already exist, root:root will become the owner and group, then when you attempt to use a related or same GUI under your normal account, access will be refused and often those GUI programs will crash.

If you use **sudo -H**, then the $HOME environment variable will be set to the correct value for the userid you are using sudo to change into.  sudo isn't just for root, but can be used to become **any** other user on the system. People forget that.

Whether you dodged any bullets or not is unknown. You can search for any root-owned files in your $HOME. If there aren't any, then all is fine.

This isn't about the OS. It is purely about personal configuration files stored in your HOME.

Of course, if you use sudo <some gui program> then go modify system files ... anything bad is possible. People often make terrible mistakes with GUIs. I've known a number of people using file managers to relocate /etc/ somewhere else, crashing their OS completely.

Some distros have sudo -H (equivalent) used by default.  Ubuntu may have changed this as well. I don't use non-LTS releases, so I have no idea if 20.10 and later have gone that way or not. There is a configuration setting in the sudoers file which will handle this. I don't know what it is, but the sudoers manpage will have the details. That manpage is a work of art, BTW. It is extremely dense with knowledge and wisdom.

---

### Post by Impavidus on 2022-03-17
> **TheFu said:**
> 
Some distros have sudo -H (equivalent) used by default.  Ubuntu may have changed this as well. I don't use non-LTS releases, so I have no idea if 20.10 and later have gone that way or not. There is a configuration setting in the sudoers file which will handle this. I don't know what it is, but the sudoers manpage will have the details. That manpage is a work of art, BTW. It is extremely dense with knowledge and wisdom.

On my Xubuntu 21.10 (upgraded from earlier releases):
```
user@host:~$ sudo bash
[sudo] password for user: 
root@host:/home/user# echo $HOME
/root
root@host:/home/user# exit
exit
user@host:~$ 
```So indeed, sudo -H is the default now.

For most home users, every file in your home directory should be owned by you and be in your own group. If this is not the case for you, you will know. So if any damage was done, a recursive chown should fix it:```
sudo chown -R $USER:$USER $HOME
```Be careful and run this command in your own shell (not root's shell) with your own proper environment, as a recursive chown on the wrong directory can be so damaging that you may have to reinstall.

---

### Post by tea for one on 2022-03-17
This command will locate root-owned files in your user home directory.
I'm sure that I found it in these forum pages some time ago.
```
find $HOME -not -user $USER -exec ls -lad {} \;

```

---

### Post by mongo42 on 2022-03-17
You guys are awesome... Thank you!  I looked in my home (/home/Mongo) directory, and the only root-owned files are a backup I made of the .bashrc file prior to adding a new user prompt, and the ".." directory (though I can navigate just fine).  I noticed that in other directories, the "." and ".." directories vary in their ownership (in the \home directory, the only two "files" are "." and ".." and, of course, my /mongo user directory - both "." and ".." are root owned).  Thank you guys again so much for your expertise (and patience with a stupid mistake).

Mongo

---

### Post by Impavidus on 2022-03-17
"." and ".." are special directories. "." is the current directory, so the same directory as the one in which it's found. ".." is the parent directory of the current directory.

---

### Post by GhX6GZMB on 2022-03-17
Rule #1: _Don't_ fiddle with permissions anywhere except in $HOME!

It will just bring you tears. I learned this the hard way.

---

### Post by TheFu on 2022-03-17
/home/[COLOR="#FF0000"]M[/COLOR]ongo?

_Usernames should be all lowercase_.  Don't mix case in usernames, groupnames, hostnames.  It is always best to avoid issues before a poorly written script from some hobby programmer shows why.  There are some other old-man tips to avoid issues on Unix-link OSes.  Always remember, these tools were written by volunteers, in their free time, over the last 30 yrs. Not all of them are created by gurus, so every possible input that seems reasonable to you is unlikely to be handled.

---

