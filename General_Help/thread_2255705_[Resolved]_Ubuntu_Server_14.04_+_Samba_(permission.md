---
title: "[Resolved] Ubuntu Server 14.04 + Samba (permissions and users)"
date: 2014-12-06
forum: General Help
---

### Post by bleudeciel16 on 2014-12-06
I'm in the process of moving my "WAMP" box over to my new ubuntu box.  So far, so good.  I love ubuntu.

I even got samba set up, and am able to read and write from my windows 8.1 machine for web development.  (shared the /var/www directory where the php files live)  The problem is that to be able to write, I had to set permissions to 777.  When it was set to 775, it wouldn't let me write.

I originally set the permissions to 775, and made a new user, then assigned that new user to the /var/www directory owner's group.  775 = group members can write, correct?  I figured assigning the user to the share, assigning the user to the directory's owner's group, and setting to 775 would be safer than guest access with the permissions set to 777.  right?  I'm not super linux savvy so If I'm way off, please let me know.

```

**settings in smb.conf:**

[global]
security = user

[webfolder]
path = /var/www
valid users = beastmaster
available = yes
read only = no
browseable = yes
public = no
writable = yes

**proof that my new user "beastmaster" is part of the www-data group:**

me@stormtrooper:/home$ id beastmaster
uid=1001(beastmaster) gid=1001(beastmaster) groups=1001(beastmaster),0(root),33(www-data)

**here are the directory permissions for the directory I shared:**

me@stormtrooper:/home$ ls -ld /var/www
drwxrwxr-x 4 www-data www-data 4096 Dec  6 21:27 /var/www

**assigned a user to samba and set a password:**

sky@stormtrooper:/var/www$ sudo smbpasswd -a beastmaster
New SMB password:
Retype new SMB password:

```

But when i try to connect from my windows 8.1 workstation, it prompts for password.  I've tried just typing the username and password for the user beastmaster, and it doesn't work.  I tried prefixing the username with the hostname like so: "STORMTROOPER\beastmaster", and it still didn't work.  I don't understand why it won't let me in.  When I remove the "valid users = beastmaster" line from the smb.conf file, I can connect to the share just fine.  (assuming that's guest access?)  But when i specify a user, it prompts for credentials but I can't connect.  Is the user I specify the unix user on MY server?  Ugh.  These little things in linux will get you every time.

Thanks ahead of time.

---

### Post by bleudeciel16 on 2014-12-06
UPDATE:

This is weird.  I successfully mapped and read/wrote from my wife's windows 7 machine.  But on my win 8.1 machine, it denies me.  On hers, the window popped up asking for credentials, so I gave it the username beastmaster and teh password that I set in samba, and it connected and worked perfectly.  What would be different on my windows 8.1 machine that would make it not map the share using credentials?

UPDATE 2:

tried different profile in windows and it worked.  tried again on my original profile and it worked.  must have been some weird caching issue or something.  oh well, it works!

---

