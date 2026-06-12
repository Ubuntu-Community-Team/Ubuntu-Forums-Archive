---
title: "home directories readable by everybody by default - why"
date: 2007-11-18
forum: General Help
---

### Post by be4truth on 2007-11-18
Hi Everybody,
why is it in Ubuntu that the home directories inclusive the /root is readable by all by default? Can I change this with chmod -R 750 /home/myusers ?

---

### Post by prince_niceguy on 2007-11-19
not sure about the default permissions... but yes you can change your home directory permission to 750.

---

### Post by mahousaru on 2007-11-19
From what I gather Ubuntu by default is set so that a non experienced user can setup a system and it will work as easiest as possible, in the most simplest situation.  That being one user on one computer.  Once you become more experienced and wish to have more then one user then I personally do the following things.

```

sudo gedit /etc/profile

```

Change the line

umask 022

to 

umask 027

The umask is the permissions that files and directories are created with.  Some people advocate 077 which means only the user gets rights to newly created files, but I think that breaks the idea of using groups easily.  Especially since Ubuntu follows the RedHat default group of the username.

Next you need to remove rights to your home directory.

```

chmod -R o-rx /home/username

```

Now this will recursively remove all read and execute rights to your home directory.  Is it dangerous?  Not really just don't do it to the whole of your file system or it will break as you do need other read execute rights else where.

Will it break stuff.  Yes it will.  For example I use the Public directory on my server to allow users to share stuff.  Dunno if that is its exact purpose but thats what I use it for.  So therefore I give the user's home directory execute rights to allow other users to enter it.

```

sudo chmod o+x /home/username

```

This will allow ppl to cd into the users home directory but not list whats in it or change anything.

Also if you use the public_html directory to serve webpages from user's home directories, you will need to give other read rights or just make the group belong to www-data.

Another issue is some program such as vmware installed from the tarball will use the umask to copy over the files and u will have no access to the program.  To get around this before you untar the downloaded file manually set your umask back to 022 with

```

umask 022

```

extracted the installation, run the process and after it has completed set your umask back to its restricted form.  I haven't noticed any debs causing this issue yet.

*EDIT*

Personally I would never do a recursive 750 to a directory  as I don't want everything t be executable.  Instead I prefer to remove the rights from other as I want them blank but the rights to user and group left alone.

---

### Post by be4truth on 2007-11-22
Thx for the replies. These are i interesting aspects. I will think about it and do some more research before I change this settings on a couple of machines.

---

