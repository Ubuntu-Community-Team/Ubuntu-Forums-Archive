---
title: "More than one user running program in $home"
date: 2008-07-10
forum: General Help
---

### Post by nikgare on 2008-07-10
Hi,

I've got some banking software that installs itself in my home directory here:
/home/nik/moneyplex

This was always fine, but now my other half want to start using it.
She is user Brigitte and, obviously has another home directory, and is unable to access mine.
I don't want to have to install the program twice, so how would I go about allowing her access to this part of my home directory?
Do I change the permission of the moneyplex directory, reinstall in another directory altogether or something else?

---

### Post by HalPomeranz on 2008-07-10
This is what Unix groups are for.  The basic idea is that you will create a new group, add yourself and Brigitte to it, and then make the /home/nik/moneyplex directory writable by this group.

First add an entry to /etc/group.  You can either do this via "System -> Administration -> Users and Groups" or by editing the /etc/group file directly ("sudo vi /etc/group").  You want to end up with an entry in /etc/group that looks like:

```

moneyplex:x:555:nik,brigitte

```

Note that you can use a different group name ("moneyplex") and group ID ("555") than the ones I use above-- they just have to be unique and not conflict with any other entries in /etc/group.  Note also that you and Brigitte will have to log out and log back in again after you have created this group-- until you do the system will not know about your membership in the new group.

Now change the permissions on the /home/nik/moneyplex directory:

```

chgrp -R moneyplex /home/nik/moneyplex
chmod -R g+rwx /home/nik/moneyplex
find /home/nik/moneyplex -type d -exec chmod g+s {} \;
chmod +x /home/nik

```

If you use a different group name than "moneyplex" in the /etc/group file, then change the first line to use the appropriate group name.

Some explanation of the last couple lines above is appropriate.  The "find" command sets the "set-GID" bit on all directories from /home/nik/moneyplex on down.  "set-GID" on a directory forces all new files created in that directory to be owned by the group owner of the directory rather than the default group of the user creating the file.  You want to make sure that everything continues to be owned by "moneyplex" and not some other group.

The last line of the example code sets the "x" bit for all users on /home/nik.  This allows other users to access files and directories under your home directory (like Brigitte getting access to /home/nik/moneyplex).  Probably your home dir already has this bit turned on, but I'm just being careful.  If you don't want Brigitte to have access to your home dir, you'll have to reinstall the moneyplex software into a different directory.

---

### Post by nikgare on 2008-07-10
Thanks for the quick reply.
It sort of works, but due (I think) to the fact that the program will always write to the directory as well, I can either use the program as user Brigitte, or user Nik.
When I want to start using the other user, I have permission problems again!

---

### Post by Fixman on 2008-07-10
> **nikgare said:**
> Thanks for the quick reply.
It sort of works, but due (I think) to the fact that the program will always write to the directory as well, I can either use the program as user Brigitte, or user Nik.
When I want to start using the other user, I have permission problems again!

```
 chmod -R a+rwx $HOME 
``` (when you are logged as your user)

---

### Post by HalPomeranz on 2008-07-10
> **nikgare said:**
> Thanks for the quick reply.
It sort of works, but due (I think) to the fact that the program will always write to the directory as well, I can either use the program as user Brigitte, or user Nik.
When I want to start using the other user, I have permission problems again!

Hmmm, it sounds like new files are not being created with "group write" permissions.  It may help to alter your umask settings.  Put the following line in the ~/.bashrc file in both your and Brigitte's accounts:

```

umask 002

```

Assuming the application is obeying your umask settings, this should ensure that any files created will be "group writable", allowing all members of the "moneyplex" group to modify them.  Note that you will need to log out and log back in again for the change to take effect.

The bad news is that the application may be creating the files with deliberately restrictive settings, in which case the whole "group ownership" trick may not work at all.  The only alternative would be to re-install the application under some shared account and use sudo to run the application as the shared user.  This seems wrong in a lot of ways.

---

### Post by bodhi.zazen on 2008-07-10
Just have your wife run it with sudo.

```
sudo -u nik /home/nik/moneyplex/<moneylex>
```

If you do not want to give her your password, edit sudo to run that command with NOPASSWD

Other options include installing the program in /usr/local or make a link

ln -s /home/nik/moneyplex/ /home/wife/moneyplex/

then chown/chmod

---

### Post by lswb on 2008-07-10
Usually programs that can run from a home directory can be installed in /opt, with a symlink in /usr/bin or /usr/local/bin pointing to the executable. I have a question though, are you and your wife going to use the same data, or is she using the program for separate data?

---

