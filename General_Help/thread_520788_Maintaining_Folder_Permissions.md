---
title: "Maintaining Folder Permissions"
date: 2007-08-08
forum: General Help
---

### Post by clievers on 2007-08-08
Hi there, I hope I'm not just missing the ball here, but I seem to be a little stuck.

What I want is on my ubuntu fileserver to have a public directory in which any user can read/write.
So I create the directory:
mkdir /home/public
Then I give it full permissions
chmod -R 777 /home/public
Then I want the owner-user of the directory to be me (user='cory', my primary group is 'cory') but I want the owner-group to be the group "users", because every user that will read/write here will be a part of that group (users by default have their primary group set to the same as their user name).
So I did
sudo chown cory:users /home/public
to initially set me as the owner and the users as the group, but then ran 
chown -R :users /home/public
leaving the owner-user part off, as I read that doing this, when a user creates a new file, the owner-user will be their user name, but the owner-group will be "users".

But when I create a directory now inside here
mkdir /home/public/shares
the permissions is "cory:cory" not "cory:users". how would you set this up so it will be "cory:users" without having to run a "chown" everytime a new file/folder is created?

Thanks very much.

---

### Post by misconfiguration on 2007-08-08
First you need to make sure Cory is a member of the users group, I think by default not everyone is a member of the users group you're set as UID and GID as your user name. You have to add cory to the users group first.

vi /etc/group and add cory after the :for the group users.
users:cory
Seperate all new users by ,
chown -R cory:users /dir/share

Try this and tell me how it works.

---

### Post by clievers on 2007-08-08
Yes, I went in through webmin and selected the 'users' group for my user.
I ran the chown again:
drwxrwxrwx  2 cory users 4.0K 2007-08-08 14:17 public
but creating the directory
drwxr-xr-x 2 cory cory 4.0K 2007-08-08 14:18 shares
it's not cory:users  :-(

Thanks.

---

### Post by clievers on 2007-08-08
oh, i'm also seeing that it doesn't keep the full 777 permissions too. the write flag is missing for group and others, on the shares directory.

---

### Post by misconfiguration on 2007-08-08
Make sure when you're editing this stuff you're running the sudo command

sudo chmod 777 /dir/share
sudo chown -R cory:users /dir/share
#if you have files in the dir do this as well

sudo chown -R cory:users /dir/share/*
sudo chmod 777 /dir/share/*

The * tells the command to append the rules to every file within the particular directory.

---

### Post by clievers on 2007-08-08
Yeah, this is what I've done. It sets the permission for the public folder, but creating a new directory, or file, in the folder results in default permissions cory:cory not cory:users like the parent folder.

---

### Post by McNils on 2007-08-08
I think that you want to set group id on the folder. 

```

sudo chmod g+s /home/public
sudo chgrp -R users /home/public

```

Now all folders and files that are created in /home/public will belong to the users group. Look at this link for more information... [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

---

### Post by clievers on 2007-08-08
Yippy Kai Yay!
The Set Group Id worked
chmod g+s /home/public
when i do: mkdir /home/public/shares  -- i get:
drwxr-sr-x 2 cory users 4.0K 2007-08-08 14:47 shares

Now the only other thing is file permissions... Doing the above, there are still no write permissions for files/directories.

drwxr-sr-x 2 cory users 4.0K 2007-08-08 14:47 shares
-rw-r--r-- 1 cory users    0 2007-08-08 14:49 test

Thanks.

---

### Post by misconfiguration on 2007-08-08
Ah, you wanted to set the sticky bit?

Sorry I didn't comprehend your question properly.

---

### Post by McNils on 2007-08-08
> **clievers said:**
> Yippy Kai Yay!
The Set Group Id worked
chmod g+s /home/public
when i do: mkdir /home/public/shares  -- i get:
drwxr-sr-x 2 cory users 4.0K 2007-08-08 14:47 shares

Now the only other thing is file permissions... Doing the above, there are still no write permissions for files/directories.

drwxr-sr-x 2 cory users 4.0K 2007-08-08 14:47 shares
-rw-r--r-- 1 cory users    0 2007-08-08 14:49 test

Thanks.

Make sure that your umask does not filter out write permissions for the group. Try umask 002.

You can try to change it for all users in /etc/profile. But users can have their own in local files such as ~/.profile ~/.bashrc.

---

### Post by clievers on 2007-08-08
@misconfiguration: i didn't actually have any knowledge of this sticky bit / set group id thing. but it does allow me to to keep the users as the group.

@McNils: my umask is currently 0022, but it gives the permissions above. because i want a public directory, i want all files and folders to be read/writable. so far, if i create a file "test" like above, the only user that can write it is "cory".

hmm.

---

### Post by McNils on 2007-08-08
A umask of 0022 is the same as 022. Try 002 and see the difference.

---

### Post by clievers on 2007-08-08
I don't understand. If they're the same, then what do you mean by "Try 002 and see the difference".

I just typed "umask" and it printed out 0022.

---

### Post by McNils on 2007-08-09
Well umask is a shell function that controls creation of files. After **umask 002**, **umask** will answer 0002. The first number controls the sticky bit and is usually not set.

Look at the link I gave you.

---

### Post by clievers on 2007-08-09
But that will control the permissions for files and folders created on the entire file system. I'm just trying to have permissions on certain ones in a certain directory.

---

### Post by McNils on 2007-08-09
There isn't such a big differense between using umask 022 and 002 because all users have their own primary group(unless you changed it) and each is the only user in that group. 

The other sulution I know of is to create a croon job that updates permisions on the files on a regular bases.

---

### Post by clievers on 2007-08-09
Hmm, yeah, a cron. It wouldn't be immediate, but it would work.
What about setfacl? I haven't read about it, but I had someone suggest it to me as well. Is that hard to work with?

---

### Post by misconfiguration on 2007-08-09
ACL's are very arcane and confusing at first, they're very versatile  after you get the hang of it. 

[http://www.linuxcommand.org/man_pages/setfacl1.html](http://www.linuxcommand.org/man_pages/setfacl1.html)

---

