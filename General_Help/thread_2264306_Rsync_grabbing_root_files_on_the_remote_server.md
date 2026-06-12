---
title: "Rsync grabbing root files on the remote server?"
date: 2015-02-06
forum: General Help
---

### Post by NertSkull on 2015-02-06
How could I set up rsync to grab files owned by root on the remote server. I've noticed that if I log in over ssh with rsync as a 'regular' user, that it doesn't pull the files that are owned by root.  Even if the files have read for group/world permissions. I get permission denied errors.

But I figure this should be doable. There must be something I can add to the sudoers file that gives the 'regular' user permission access those files for rsync.

Like adding 'cp' or 'mv' or 'rsync' or some other command to the sudoers file so my regular user doesn't need a password.Is this doable?

(I don't want to allow root login on ssh if I can avoid it)

Thanks.

I must admit, I didn't think this would be a problem since the files are readable by the world. I thought I could just read them off and transfer them, but leave ownerhsip root. But this doesn't work (unless I'm doing something wrong).

---

### Post by SeijiSensei on 2015-02-06
You need to use keys: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You can add the key for the account rsync runs as to the remote's /root/.ssh/authorized_keys.  Then you won't need a password, and the transfer will have full permissions.

---

### Post by kpatz on 2015-02-06
The files may have world-readable permissions, but what about the directory/ies they reside in?  If those aren't readable, rsync won't be able to find them.

What I do is I enabled root login in ssh but left the root password in the default locked state, and use ssh keys for access.

---

### Post by NertSkull on 2015-02-06
Found the answer that does NOT require logging in with root (even with rsa keys).

This is it:

First, you have to add rsync to the sudoers file.  This must be done on the side where the files are owned by root that was blocked from transfering.

So run

```
sudo visduo

```
Then add this line

```
username ALL=NOPASSWD:/usr/bin/rsync
```

Save that and now rsync can be run on the server as the 'user' but that user now has sudo ability for rsync.

Now, add the following switch to the rsync command. 

```
--rsync-path='sudo rsync'
```

This tells rsync to run with sudo, allowing it to access the root files. And you don't need a password, because you added rsync to the sudoers file.  

Plus, no root login and/or keys for root, which is ideal.


I'm going to mark this as solved, but if someone see's a problem with this, let me know.

---

