---
title: "Is it possible to chown future files?"
date: 2008-05-12
forum: General Help
---

### Post by ruipedroca on 2008-05-12
Hi,

Is it possible to chown future files?

Example:
Every file and directory created by user1 inside dirA gets automatically chown to user2.


Regards

---

### Post by pointone on 2008-05-14
You can set your umask to change the permissions on created files/directories, but I don't think this is possible to do with ownership. 

Two possible solutions:

You could easily configure a cron job to run every 5 minutes: 

```
*/5 * * * * root chown -R user2:user2 /path/to/dir
```

Or, you could create files using sudo, providing you have your sudoers file configured properly.

```
sudo -u user2 mkdir /path/to/dir
```

---

### Post by p_quarles on 2008-05-14
I don't know of a way to set a user owner for future files, but there is an easy way to set group owner. This, combined with the appropriate access for group users, should allow you do anything you're looking for. Just set the gid for the directory:
```
chmod g+s /path/to/dir
```
Run with "sudo" as necessary.

---

### Post by balagosa on 2008-05-14
i think it is possible. BUT it would require HARD-CODED programming.

in short, impossible as of now.

---

### Post by ruipedroca on 2008-06-02
Hi,

Just to provide feedback:
I've managed in some situations with the group permissions, and in others with umask!

Thanks all for your replies!

---

### Post by tors on 2008-06-02
You can do this with Access Control Lists aswell:

```
man acl
```

...
1.   The new object inherits the default ACL of the containing directory
     as its access ACL.
...

---

