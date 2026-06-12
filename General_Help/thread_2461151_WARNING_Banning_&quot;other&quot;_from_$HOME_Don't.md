---
title: "WARNING: Banning &quot;other&quot; from $HOME: Don't do it like I did!"
date: 2021-04-25
forum: General Help
---

### Post by GhX6GZMB on 2021-04-25
In another thread, I asked about the implications/ramifications of removing "other" rights from the $HOME directories.

[https://ubuntuforums.org/showthread.php?t=2460569](https://ubuntuforums.org/showthread.php?t=2460569)

This has turned out to be a total disaster, and I'm now forced to do a 100% complete new install and configuration. A lot of programs simply don't work anymore.

My big mistake was removing "other" rights from the hidden directories/files. For the "normal" user directories  it works fine.

I apologise for inconveniences this may have caused others.

---

### Post by scorp123 on 2021-04-25
> **ml9104 said:**
>  This has turned out to be a total disaster, and I'm now forced to do a 100% complete new install and configuration. A lot of programs simply don't work anymore.

Reinstalling because of wrong permissions on your $HOME??? Seems like total overkill to me. =;

Also, in a corporate environment setting the permissions to "700" is totally normal (nobody but me has any business reading the files on my "$HOME" directory) so I fail to see what programs *"don't work anymore"* since restrictive permissions on your $HOME shouldn't have any influence on a system-wide program working or not...

Unless you messed up the permissions in other places too, e.g. you modified places like /etc, /usr, /var, /lib and so on??

---

### Post by GhX6GZMB on 2021-04-25
No, the problem is that I messed up the permissons on the hidden files.

---

### Post by ajgreeny on 2021-04-25
Which hidden files do you mean?
Giving 700 permissions to everything in your home folder would include all the hidden files and folders so I don't really understand what you mean by giving wrong permissions to hidden files.

---

### Post by scorp123 on 2021-04-25
> **ml9104 said:**
> No, the problem is that I messed up the permissons on the hidden files.

And so? Giving "700" is standard too for most of them, especially critical things such as **~/.ssh** have no business of having anything but "700". 

As I wrote before: A complete reinstallation just because some program for some stupid reason can't find it's dot-config file inside your $HOME seems excessive + overkill. You could simply create a 2nd user e.g. "User2" and then check what config file defaults this new guy would be given? Then just reproduce the permissions "User2" has on some of his files and apply them to the few files inside your $HOME that don't seem to work properly.

---

### Post by grahammechanical on 2021-04-25
As a distraction I would like to say that from 21.04 onward the home folder becomes private by default. I have just run a couple of tests from 20.04. 

1) Using the file manager I access the partition of a 20.10 install. I see all the system folders including Home which I open and then I open the username home folder and see all the folders and files we usually see.

2) I try the same thing with 21.04 and when I open the system Home folder it is empty. There is no user name home folder. I have the same user name and password for several installs of Ubuntu/Linux on this computer. The only username home folder I cannot now access is the 21.04 user home folder.

I assume that if there was more than one user on a 21.04 install each user's home folder would be not only inaccessible but also not viewable.

Regards

---

### Post by kneutron on 2021-04-26
If you chmod 700 just the /home/username directory it should block everything under it, you shouldn't have to use the -R recursive switch.

---

### Post by TheFu on 2021-04-26
Installed Ubuntu Desktop (Gnome) 21.04 yesterday as a demo for my LUG.  Had some issues, mainly with the GPU, resolution, and systemd-resolved after I masked it.  Anyway, the /home looks like this:

```
$ ll /home/
total 12
drwxr-xr-x  3 root root 4096 Apr 25 16:07 ./
drwxr-xr-x 20 root root 4096 Apr 25 16:06 ../
[COLOR="#FF0000"]drwxr-x---[/COLOR] 17 tf   tf   4096 Apr 25 17:22 tf/
```

I haven't noticed any issues related to that.
I'm in the 700 group. Should be perfectly fine.  This is normal and has been in corporate environments since before Linux existed.

```
drwx------ 17 tf   users   4096 Apr 25 17:22 tf/
```
is very common. Or if you work in a team, then your primary group would be that for the team:
```
drwx------ 17 tf   accounting   4096 Apr 25 17:22 tf/
```
Very common.  The idea that a new group would be created for every freakin' user just seemed wrong to me when I first came on that with Ubuntu. It was not standard.

---

### Post by Impavidus on 2021-04-26
Those hidden files contain configuration, cache and sometimes saved projects or something similar, belonging to particular applications and specific to the user. It should be no problem if they're not readable by others ... unless you run those applications as a different user or messed up ownership before. Have you ever used sudo with those applications? Or chown'ed any of those hidden files?

---

### Post by The Cog on 2021-04-26
How did you change the permissions? 
Is it possible that a "chmod -R" of some sort has recursively removed the execute permissions from all the sub-directories? If so, that is quite easily fixable.

---

### Post by scorp123 on 2021-04-26
> **The Cog said:**
> How did you change the permissions? 

OP has a 2nd thread here about the same topic:
[https://ubuntuforums.org/showthread.php?t=2460569]("https://ubuntuforums.org/showthread.php?t=2460569")

---

### Post by GhX6GZMB on 2021-04-26
My Apologies!!
After a detailed analysis, I've found out that the removal of the "other" permissions is NOT the culprit.
Rather, it's messy ownership of some of the directories, where not every directory/file was assigned to the correct owner.
I've fixed this issue with a new install and restore, and am confident that it will work (but have made an extra backup just in case).
I'm not as restrictive as @TheFu and target a 750 rights environment. That way interaction between users is still possible.

Again, Sorry, Mea Culpa.

---

### Post by TheFu on 2021-04-26
> **ml9104 said:**
> My Apologies!!
After a detailed analysis, I've found out that the removal of the "other" permissions is NOT the culprit.
Rather, it's messy ownership of some of the directories, where not every directory/file was assigned to the correct owner.
I've fixed this issue with a new install and restore, and am confident that it will work (but have made an extra backup just in case).
I'm not as restrictive as @TheFu and target a 750 rights environment. That way interaction between users is still possible.

Again, Sorry, Mea Culpa.

In a default Ubuntu desktop environment, _there is no practical difference between 750 and 700_ since the group is also unique to the userid and doesn't have any other members.  We often get lazy here, make assumptions based on Ubuntu and don't explain things clearly in the interest of not confusing people new to permissions.

And just like it is easy for us not to spend time explaining the "group" aspects, I could see where end-users wouldn't bother to learn and understand those either until they need them.

---

### Post by GhX6GZMB on 2021-04-26
Deleted/misunderstood. Sorry.

---

### Post by GhX6GZMB on 2021-04-26
> **TheFu said:**
> In a default Ubuntu desktop environment, _there is no practical difference between 750 and 700_ since the group is also unique to the userid and doesn't have any other members.  We often get lazy here, make assumptions based on Ubuntu and don't explain things clearly in the interest of not confusing people new to permissions.

And just like it is easy for us not to spend time explaining the "group" aspects, I could see where end-users wouldn't bother to learn and understand those either until they need them.

This is very dependent on the working environment.
I use Group membership to temporarily allow access from one user to another or vice versa. Instead of carrying USB-thumbs back and forth.

---

### Post by TheFu on 2021-04-26
> **ml9104 said:**
> This is very dependent on the working environment.
I use Group membership to temporarily allow access from one user to another or vice versa. Instead of carrying USB-thumbs back and forth.

Have you looked at the **gpasswd** command? This lets us set a password on a "group" that can be shared quickly with non-members, then either changed or removed.  Group members won't be bothered for the password.

From the manpage:
```
       If a password is set the members can still use newgrp(1) without a
       password, and non-members must supply the password.

   Notes about group passwords
       Group passwords are an inherent security problem since more than one
       person is permitted to know the password. However, groups are a
       useful tool for permitting co-operation between different users.
...
       -A, --administrators user,...
           Set the list of administrative users.
```
the -A flag means non-sudoers can still be group managers.  Handy for dynamic software development teams with visiting developers.

Just another option for consideration.

---

