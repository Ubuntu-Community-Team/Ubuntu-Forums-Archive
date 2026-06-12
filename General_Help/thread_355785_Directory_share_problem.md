---
title: "Directory share problem"
date: 2007-02-07
forum: General Help
---

### Post by Rich78 on 2007-02-07
Hi,

I've just setup an NFS and NIS setup.

When mounting a directory I'm using sudo mount.  But how do I mount for the logged in user?

Currently if I do a sudo mount, on my Nautilus file browser, the directory is locked.

I assume this is because it was mounted using sudo and not because of access restrictions from NFS?

Thanks

---

### Post by Tuxgrrrl on 2007-02-07
Greetings Rich78,
We know how to mount shares for any user/group ID - GID - so that the shares are read/write folders - auto-mounted at start up.
Is that what you desire to do?

---

### Post by bodhi.zazen on 2007-02-07
This is the BEST NFS guide I know :

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Other then that we would need to look at your server config and add the nfs to fstab ;)

---

### Post by Rich78 on 2007-02-08
Basically I can setup a directory share on NFS and mount it on a users computer via sudo.  But if I browse to that folder, it is locked because I did a sudo.

I'm at work now so can't test it but I wonder if I was to do:

mkdir ~/share
sudo mount {server}:/home/share ~/share

Would that work?

Could it be because I did a sudo mkdir ~/share making the directory only accessible to root?

---

### Post by bodhi.zazen on 2007-02-08
Well without more information I am not sure where the problem may be. Could be on the server or client :p

On the server you need these options in the /etc/exports:[quote]rw,no_root_squash,async[/code]

On the client, go ahead and mount your share.

Then you can try chown and chmod:

```
sudo chown user_name:user_name /home/user_name/share
sodu chmod 770 /home/user_name/share
```

#use the full path for those commands rather then ~/share.

---

