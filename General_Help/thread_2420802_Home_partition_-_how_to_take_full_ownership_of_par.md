---
title: "Home partition - how to take full ownership of partition and all content"
date: 2019-06-11
forum: General Help
---

### Post by jaynix2 on 2019-06-11
Hi,
I have a separate 'Home' partition in a new install. How to take full ownership of partition and all it's content, current and future?  Have been frustrated by being unable to download from web into any folder other than downloads, can't move from downloads to another folder, can't add /delete a folder except via terminal, etc, etc. As owner of system, and just one user account, I would like to access, add, create, edit, delete, change contents of Home partition in any way that suits me -without permission error messages coming up, and without needing to go to terminal to do any of these things.

I realise that I will have to enter commands in terminal to change the ownership permissions, I don't know how though. 

Thanks

---

### Post by dino99 on 2019-06-11
Already answered ;) [https://askubuntu.com/questions/6723/change-folder-permissions-and-ownership](https://askubuntu.com/questions/6723/change-folder-permissions-and-ownership)

---

### Post by jaynix2 on 2019-06-11
Oops! just hoping that if I add to this thread the option will appear to subscribe to it and get updates - and it did:D

---

### Post by jaynix2 on 2019-06-11
Thanks Dino, but that doesn't seem to be helpful. Or is a /home partition considered a folder in Ubuntu?

---

### Post by CatKiller on 2019-06-11
> **jaynix2 said:**
> Hi,
I have a separate 'Home' partition in a new install. 
How, exactly, did you do that? Creating a /home partition as part of the install sorts out the permissions automatically. 
> How to take full ownership of partition and all it's content, current and future? 
You only want the user to have ownership of their own Home folder. Ownership of a partition doesn't have any meaning. 
>  I realise that I will have to enter commands in terminal to change the ownership permissions, I don't know how though. 
You **ch**ange **own**ership of files and folders with the **chown** command. 
> **jaynix2 said:**
> Thanks Dino, but that doesn't seem to be helpful. Or is a /home partition considered a folder in Ubuntu?
/home is a folder. That folder is used as a **mount point** for your partition, which contains other folders, which have their own permissions. The Home folder for your user will be something like /home/jaynix2.

---

### Post by oldfred on 2019-06-11
I either download something or use root when I should not and ownership or permissions are not correct. I periodically run this on /home and most of my real data is in /mnt/data and I then run commands on it also.

       Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER

 sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data 

         All directories will be 775.
All files will be 664 except those that were set as executable to begin with. 

Note that -R is recursive and also changes all lower folders. Never, ever run on any system partition, only partitions with just your data.

---

### Post by Impavidus on 2019-06-11
There seems to be some confusion between /home and the home directory. Hardly anything of what follows is a hard rule, but most of it are guidelines followed on nearly all home systems.

The /home partition is the partition mounted at the /home directory. This /home directory is the directory containing home directories and is owned by root, with no write permissions for ordinary users. It contains your home directory, /home/username, along with those of the other users (if any). In your own home directory everything is owned by you and you have read and write permissions everywhere and execute permissions on the directories. Others have no write permission. Outside of your home directory, including in other directories in /home, you have no write permissions.

This all means that you can (or at least, should be able; maybe there's something wrong on your system) store files outside ~/Downloads, create new directories etc., but you can't create files just anywhere in your /home partition.

---

### Post by jaynix2 on 2019-06-14
> **Impavidus said:**
> There seems to be some confusion between /home and the home directory. Hardly anything of what follows is a hard rule, but most of it are guidelines followed on nearly all home systems.

The /home partition is the partition mounted at the /home directory. This /home directory is the directory containing home directories and is owned by root, with no write permissions for ordinary users. It contains your home directory, /home/username, along with those of the other users (if any). In your own home directory everything is owned by you and you have read and write permissions everywhere and execute permissions on the directories. Others have no write permission. Outside of your home directory, including in other directories in /home, you have no write permissions.

This all means that you can (or at least, should be able; maybe there's something wrong on your system) store files outside ~/Downloads, create new directories etc., but you can't create files just anywhere in your /home partition.

Thanks Impavidus,the answers you and Catkiller have given me make it clearer that I should be asking about /home/my username, I created a partion for /  and a different partition for Home. I read several places where this is suggested as a way of preventing loss of personal files if system crashes. Have been  frustrated by the kind of permissions issues I mentioned at the start of this thread, when trying to do anything in  /home/my username, and want to stop this from happening.

I am hoping the solution oldfred gave might work.

Not sure if it's ok to use those same instructions for /opt and /usr/local? Also need to change permissions for /opt and /usr/local  so I can download a tar.gz file to /opt, extract to, and install from there; and download a .deb file to /usr/local and install from there.

---

### Post by jaynix2 on 2019-06-14
> **oldfred said:**
> I either download something or use root when I should not and ownership or permissions are not correct. I periodically run this on /home and most of my real data is in /mnt/data and I then run commands on it also.

       Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER

 sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data 

         All directories will be 775.
All files will be 664 except those that were set as executable to begin with. 

Note that -R is recursive and also changes all lower folders. Never, ever run on any system partition, only partitions with just your data.

Thanks oldfred. what would I use to change permissions of /opt and /usr/local? I Need to change permissions for /opt and /usr/local  so I  can download a tar.gz file to /opt, extract to, and install from there;  and download a .deb file to /usr/local and install from there. Have read that's the right place to download those kind of files from trusted sources, but am blocked by permissions issues here also, and can't even download to there  - get insufficient permissions' error messages. Neither can I copy from downloads folder, and paste into these folders.

---

### Post by jaynix2 on 2019-06-14
> **CatKiller said:**
> How, exactly, did you do that? Creating a /home partition as part of the install sorts out the permissions automatically. 
 
You only want the user to have ownership of their own Home folder. Ownership of a partition doesn't have any meaning. 

You **ch**ange **own**ership of files and folders with the **chown** command. 

/home is a folder. That folder is used as a **mount point** for your partition, which contains other folders, which have their own permissions. The Home folder for your user will be something like /home/jaynix2.

During install, I gave / its own partition, and made a partition for home next to it. I am still having permissions issues in /home/username. I am hoping the instructions oldfred has given will sort these out. I have also been asking about how to change permissions of /opt, and /usr/local so I can download and install trusted software via these folders

---

### Post by Impavidus on 2019-06-14
I'd keep /opt and /usr/local owned by their default owners (mostly root). /opt is occasionally used by third-party .deb packages, which can make their own decisions on ownership, groups and permissions, with which you better not interfere. /usr/local is mostly for manually installed stuff. You may have noticed that some directories under /usr/local belong to the staff group and have the sgid bit set (permissions 2775 / rwxrwsr-x). This means that users belonging to the staff group may install stuff there. That's already somewhat less restrictive than allowing root only and a recursive chown would break that feature (note that it's not used on a standard system; /usr/local only contains empty directories on a freshly installed Ubuntu system).

The proper way to install stuff to /opt and /usr/local is to download or build the software in your home directory, then unpack/install it into /opt or /usr/local. Just run the command to unpack/install with sudo. If that would result in copying many files from your /home partition to your root partition, it may be better to give yourself full permissions on a subdirectory of /usr/local (like /usr/local/src/myproject).

---

### Post by ajgreeny on 2019-06-14
> **jaynix2 said:**
> During install, I gave / its own partition, and made a partition for home next to it. I am still having permissions issues in /home/username. I am hoping the instructions oldfred has given will sort these out. I have also been asking about how to change permissions of /opt, and /usr/local so I can download and install trusted software via these folders
No, no, no!

Do not run that same chown command on any folder in /opt or in /usr or you will probably cause even bigger problems for yourself.

Did you set that home partition at install with the mountpoint of /home?  It sounds as if you may have missed that step, but it's difficult to be sure.

Why do you believe that you need to download to, and install trusted software from, the /opt and /usr/local folders.  There is absolutely no reason to do this at all so we need to know more about what you're really trying to do.

Finally, as you seem to have problems with your home partition file ownership, can you confirm that you do not, and never have used sudo to open any GUI applications as doing so can, depending on the application, change ownership of some of your folders and files in /home/username to root, stopping you using home as you want, and also potentially stopping you logging in as that user.

See Root_Sudo in my signature below for details.

---

### Post by CatKiller on 2019-06-14
To amplify what ajgreeny has said, running graphical applications as root will give you exactly the kind of permissions problems you've said you have. Root is not the same as "Run As Administrator." 

You also shouldn't download and execute random files that you got off some random website, not in /usr/local, and not anywhere else. You might *think* that you want to do that, because you used to do something similar on Windows, but really, really, really, **don't do that**.

Use the package manager to install software. That's what it's for.

---

### Post by TheFu on 2019-06-15
Not being able to save downloads outside the ~/Download/ directory could be part of the browser security setup for newer Ubuntu releases.  If the browser you are using is a Snap, this is likely.  There are many reasons for this.

I agree with everything said above.
Leave /opt/ and /usr/local/ with the default permissions until you really understand Unix and permissions better.  File and directory permissions on Unix systems is the first line of defense for a secure system. There are many subtle considerations that people even with years of experience don't always catch.

**Clear up confusion about HOME**
~/ is the home directory for the current userid, which might be marc or pete or steve.

~marc/ is the home directory for a userid "marc" - that any other userid can use to access marc's home in that manner. In a typical, single-user install, the directory would be /home/marc/

~/marc/ is a directory inside HOME called "marc".  Likely it is /home/marc/marc/

The ~ ... asks the shell to use the **getent passwd $USER** command to fill in the correct directory from the password DB. It doesn't assume /home/{something}, which is only used for non-corporate setups. Well, if a ~/ is used, it simply fills in the environment variable for $HOME, but effectively that works in the same way because login pulls the data using getent to set HOME correctly.  echo $HOME will show how that environment variable is set for a userid.

In most home Linux installs, these are all the same place, assuming the current logged in user is "marc":

[LIST]
[*]$HOME
[*]~/
[*]~marc/
[*]/home/marc/
[/LIST]
If I'm steve and want to access Marc's home, I'd use ~marc/ .

Another set of unclear directories. These are hardly ever confused, but using the correct term helps.
[LIST]
[*]/ is the *root directory*.
[*]/root/ is *root's HOME directory*.  Also ~root/ works.
[/LIST]

Extra fun: run these commands.
```
sudo -i
echo $HOME
exit
sudo -s
echo $HOME
exit
```
If you use **sudo nautilus**, where do the config files get written and which userid is the owner?

If you use **sudo -H nautilus**, where do the config files get written and which userid is the owner?

Where HOME points is extremely important.  Having the wrong HOME for a specific program running as a different userid is bad, bad, bad .... almost always.

---

### Post by jaynix2 on 2019-06-16
> **ajgreeny said:**
> No, no, no!

Do not run that same chown command on any folder in /opt or in /usr or you will probably cause even bigger problems for yourself.

Did you set that home partition at install with the mountpoint of /home?  It sounds as if you may have missed that step, but it's difficult to be sure.

Why do you believe that you need to download to, and install trusted software from, the /opt and /usr/local folders.  There is absolutely no reason to do this at all so we need to know more about what you're really trying to do.

Finally, as you seem to have problems with your home partition file ownership, can you confirm that you do not, and never have used sudo to open any GUI applications as doing so can, depending on the application, change ownership of some of your folders and files in /home/username to root, stopping you using home as you want, and also potentially stopping you logging in as that user.

See Root_Sudo in my signature below for details.

Have replied to all in single reply below

---

### Post by jaynix2 on 2019-06-16
> **CatKiller said:**
> To amplify what ajgreeny has said, running graphical applications as root will give you exactly the kind of permissions problems you've said you have. Root is not the same as "Run As Administrator." 

You also shouldn't download and execute random files that you got off some random website, not in /usr/local, and not anywhere else. You might *think* that you want to do that, because you used to do something similar on Windows, but really, really, really, **don't do that**.

Use the package manager to install software. That's what it's for.

have replied to all in single reply below

---

### Post by jaynix2 on 2019-06-16
> **Impavidus said:**
> I'd keep /opt and /usr/local owned by their default owners (mostly root). /opt is occasionally used by third-party .deb packages, which can make their own decisions on ownership, groups and permissions, with which you better not interfere. /usr/local is mostly for manually installed stuff. You may have noticed that some directories under /usr/local belong to the staff group and have the sgid bit set (permissions 2775 / rwxrwsr-x). This means that users belonging to the staff group may install stuff there. That's already somewhat less restrictive than allowing root only and a recursive chown would break that feature (note that it's not used on a standard system; /usr/local only contains empty directories on a freshly installed Ubuntu system).

The proper way to install stuff to /opt and /usr/local is to download or build the software in your home directory, then unpack/install it into /opt or /usr/local. Just run the command to unpack/install with sudo. If that would result in copying many files from your /home partition to your root partition, it may be better to give yourself full permissions on a subdirectory of /usr/local (like /usr/local/src/myproject).

Thank you, I will try that. Copy pasting in file manager from downloads to /opt resulted in error message saying that not all components had been transferred. But will try the way you have suggested instead.

---

