---
title: "TrueCrypt Mounting Question"
date: 2008-01-24
forum: General Help
---

### Post by btrichardson on 2008-01-24
Hello all,

Can anyone tell me why the owner of the directory to which I mount a TrueCrypt file system gets changed to root?  For example, say I'm user foo and I've created a TrueCrypt file system named mystuff.txt and a directory named encrypted.  The directory 'encrypted' has 'foo' listed as its owner and group initially, but after I run

truecrypt /home/foo/mystuff.txt -k /home/foo/mykey.txt encrypted/

the directory 'encrypted' has 'root' listed as its owner and group.  Why is this?  How can I make it such that this doesn't happen?  I've already created a group called truecrypt, added myself and root as users in that group, and changed the group of the truecrypt executable in /usr/bin/ to truecrypt.  I also modified the visudo file to make it such that anyone in the truecrypt group can run the truecrypt executable without needing to specify a password.

Thanks in advance! -- BTR

---

### Post by s1m0n13 on 2008-01-24
I ran into a similar issue when i was using forcefield (gui for truecrypt).  I solved it by supplying an additional mount command of "umask=0000"
I believe you can do this using truecrypt by appending the -M flag...
-M umask=0000

Hope this helps.

---

### Post by Zwack on 2008-01-24
> **btrichardson said:**
> Hello all,

Can anyone tell me why the owner of the directory to which I mount a TrueCrypt file system gets changed to root?  For example, say I'm user foo and I've created a TrueCrypt file system named mystuff.txt and a directory named encrypted.  The directory 'encrypted' has 'foo' listed as its owner and group initially, but after I run

truecrypt /home/foo/mystuff.txt -k /home/foo/mykey.txt encrypted/

the directory 'encrypted' has 'root' listed as its owner and group.  Why is this?  How can I make it such that this doesn't happen?  I've already created a group called truecrypt, added myself and root as users in that group, and changed the group of the truecrypt executable in /usr/bin/ to truecrypt.  I also modified the visudo file to make it such that anyone in the truecrypt group can run the truecrypt executable without needing to specify a password.

Thanks in advance! -- BTR

Before you mount a filesystem the mount point is a directory.  The directory has an owner.  Once you mount a filesystem that directory is the root directory of the filesystem and not the mount point directory.  You have two options.

1) mount the filesystem change into it and change it's ownership 

```
chown user.group .
```

2) mount the filesystem with the -o uid=XXX option if it is supported by the filesystem.

I would go for the first but beware that if you mount this on a different machine the user id with that uid will be the owner (and it might not be you.

Z.

---

### Post by anitract on 2008-01-28
I have a volume that I formatted in ext3. When I mount it every copy, delete, etc must be done w/ root permissions.

I tried the -M umask=0000, which gave a mount error...

Also, -u is only for FAT filesystem, so no cigar there...

....so what do I need to do to allow users to copy to my volume once it is mounted?

Help would be greatly appreciated!

---

### Post by s1m0n13 on 2008-01-28
anitract - in your case.. I believe you would have to change the permissions of the directory with  root following successfully mounting the volume.

---

### Post by anitract on 2008-01-29
I've been using linux for about a week...so forgive my ignorance here, but how do you do that to an entire filesystem/volume  

If I understand things, I would mount the volume, then use chmod on it (but with what perms)?  Syntax-wise I'd love to see an example.  :)

And what about chown to become the owner?  Since root is the owner now, is this needed also to get things working?

---

### Post by s1m0n13 on 2008-01-29
Check out this ariticle.. [http://www.cae.wisc.edu/site/public/?title=linpermissions-change](http://www.cae.wisc.edu/site/public/?title=linpermissions-change)
It details how to use chmod and chown.

Below are 2 examples ref'd in the article on how to change permissions using chmod and change ownership using chown.

chmod ex.
If we wanted to change both the /tmp/test and the test.txt permissions so that only the owner has all permissions, we would type:
ComputerName:~# chmod -R 700 /tmp/test

chown ex.
Changing the ownership of the /tmp/testdir/ directory and all the files within it from "root" to "user", using the -R option:
ComputerName:~# chown -R user /tmp/testdir/

Hope this helps.

---

### Post by anitract on 2008-01-29
That's actually a pretty good link.  Not at my computer right now, but say I mount my volume at:
/mnt/tc

If I wanted everyone to have full access to this, I could do:
sudo chmod -R 777 /mnt/tc

That right?

On a side note, one thing that I am sketchy on is Execute permissions as they relate to sharing over the network.  Say I share a folder and do **not** give a user Execute rights to the files within.  Say this user then accesses a script file from that share over the network (so from their machine)......would the file run on their machine, or not?

---

### Post by Zwack on 2008-02-04
> **anitract said:**
> That's actually a pretty good link.  Not at my computer right now, but say I mount my volume at:
/mnt/tc

If I wanted everyone to have full access to this, I could do:
sudo chmod -R 777 /mnt/tc

That right?



Right... But that would also make every file executable by everyone.  A better method would be to use the symbolic mode and something like

sudo chmod -R a+rw /mnt/tc

> 

On a side note, one thing that I am sketchy on is Execute permissions as they relate to sharing over the network.  Say I share a folder and do **not** give a user Execute rights to the files within.  Say this user then accesses a script file from that share over the network (so from their machine)......would the file run on their machine, or not?

That depends on how you're sharing and how the share on the other side has them mounted.  It's usually bad practice to allow execute permissions to be deliberately shared out as too many people have . in their path (foolishly)...  I'll leave you to work out why indiscriminately including the current directory in your path can have unintended consequences.

Z.

---

