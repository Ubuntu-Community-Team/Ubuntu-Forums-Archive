---
title: "Is sftp totally useless ???"
date: 2013-10-22
forum: General Help
---

### Post by thuizt on 2013-10-22
Hello all,

To begin with I won't call myself a Linux expert but managed to setup a chrooted sftp server.

This all works but....  for the permissions.
All uploaded files have readonly for the group (640). This means not any one but the user can modify the files.
In my case this makes the uploading and so my SFTP server totally useless.

I sincerely hope I overlooked something cause I cannot find any solution to solve this.
How to make sure all uploaded files on a chrooted sftp server are 660 ???

Thanks.

---

### Post by TheFu on 2013-10-22
The linux sftp client has lumask, chmod, chgrp, chown commands built-in. Are those not working?

From the "help"```

lumask umask                       Set local umask to 'umask'
chgrp grp path                     Change group of file 'path' to 'grp'
chmod mode path                    Change permissions of file 'path' to 'mode'
chown own path                     Change owner of file 'path' to 'own'
```

Enough of the /etc/passwd and /etc/group files will need to be available for some of those options/commands, but the lumask and chmod should work regardless.

---

### Post by thuizt on 2013-10-23
Thank for answering,

It is not that I cannot change permissions. I could run a script to update permissions on a frequent basis but that is a crappy solution.

The point is that my clients use a IOS (iPxd) device to upload data. This data always has the group permissions set to read only. 
I have not yet found a way to make sure that the uploaded files have 660 or 664 permissions.

Thanks

---

### Post by TheFu on 2013-10-23
I tested this here. Whatever the file permissions were on the source system were carried over to the target system in my tests. Just did 3 different tests a few min ago.  I tried using the g+s (the group "sticky bit") on the target directory - it didn't help to force greater access. The most I could get was 775, never 777 or 776. o+w wasn't possible, but my umask is 0002, so that explains that.  I'm unwilling to change my umask to test.  Too many automatic file transfers happening here.

All this leads me to believe the issue is on the client side, not on the server.  Some clients do allow scripting, so it might be possible to upload files, then chmod them inside the sftp client. Don't know if any iOS clients do that.

Check the client OS for control over permissions. Perhaps the client sftp app can control this or a different app can be used?

---

### Post by sudodus on 2013-10-23
Try rsync or if it does not work, make tarballs and expand them after transfer (via sftp or rsync).

---

### Post by btindie on 2013-10-23
On newer version of openssh you can tell it what umask to use quite easily. [http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Umask](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Umask)

Presumably you're creating your chroot SFTP server as below?
```
Match Group sftpusers
        ChrootDirectory       /home/%u
        AllowTCPForwarding    no
        X11Forwarding         no
        ForceCommand          internal-sftp
```

All you need to do is change the ForceCommand to
```
ForceCommand          internal-sftp -u 0002
```
to set the UMASK.

It'll work as long as your client doesn't preserve local permissions / try and change them.

---

### Post by thuizt on 2013-10-23
btindie, you're a hero !!
All the others thanks for answering and digging in to it.
The question why couldn't I find that one myself ??
Anyway the SFTP server is very usefull again.

Thanks.

---

