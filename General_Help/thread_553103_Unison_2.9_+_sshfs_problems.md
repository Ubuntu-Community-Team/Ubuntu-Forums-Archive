---
title: "Unison 2.9 + sshfs problems"
date: 2007-09-17
forum: General Help
---

### Post by Nicklas Overgaard on 2007-09-17
Hi everybody!

I've recently installed Ubuntu 7.10 Tribe 5 on my laptop (i have to use this beta, as it's a brand new laptop, and the older distros does not support the hardware properly).

The problem is, that i mount my homefolder on a SUN server, through sshfs. Everything is OK here, i can see all my files etc.

But when i try to synchronise my local copies, with the ones on the server, i get the following error in all the locally changed files:

"Error in renaming /path/to/local_file.filename
Operation not permitted [rename(/path/to/remote_file.filename)]"

Now, if i delete the file on the remote filesystem, and try again, the file is created without errors again, on the remote filesystem.

What have i done wrong?

p.s It works flawlessly from windows XP, with SftpDrive and Usinson 2.2 for Windows.

Thanks in advance

/Nicklas

---

### Post by pollian on 2007-09-17
I had the same problem, and it turned out to be an issue with sshfs. I solved it simply by starting sshfs with the option *-o workaround=rename *(see [http://fuse.sourceforge.net/wiki/index.php/SshfsFaq](http://fuse.sourceforge.net/wiki/index.php/SshfsFaq) )

pollian

---

### Post by Nicklas Overgaard on 2007-09-18
Thank you so much pollian - it works :)

It looks like i can finally get rid of my WXP installation....

/Nicklas

---

