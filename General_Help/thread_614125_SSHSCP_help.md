---
title: "SSH/SCP help"
date: 2007-11-15
forum: General Help
---

### Post by BlanchyUk on 2007-11-15
Hi,

I'm trying to copy a file from my university server to the machine I'm using now at home.

I've logged into the server using SSH, and I've tried lots of different commands, none of which have been successful.

eg..

scp [email]cb5681@ice.cs.bris.ac.uk:~/crypto3.odt[/email] [email]mum@192.168.1.103:/Desktop/crypto3.odt[/email]

but this lasts forever and never completes.

What am I doing wrong?

Thanks

---

### Post by IcemanV9 on 2007-11-16
Try this from your terminal (no need to ssh first) ...

```
cd Desktop
scp cb5681@ice.cs.bris.ac.uk:<full path>/crypto3.odt .
```

---

### Post by xeth_delta on 2007-11-16
BlanchyUk have you solved the problem? IcemanV9 is right in the fact that you have to use the full path to the file on the remote server. The tilde character ~ will expand the path to your home directory in your local machine, since the command was issued from it.

For what is worth, I also have been having problems with scp. It turned out to be a problem with the .cshrc file in my home directory on the remote server. After making a slight change in that file I am finally able to use sshfs.
More information on [http://openssh.org/faq.html#2.9]("http://openssh.org/faq.html#2.9").

Xeth

---

