---
title: "vsftpd and access rights"
date: 2013-06-19
forum: General Help
---

### Post by Daktyl198 on 2013-06-19
I installed vsftpd via the instructions on the Ubuntu help site and it works perfectly.... for one out of the two users I have set up.

The really weird part is this:
the users are both in the same group. I have them accessing two different folders, but the folders have EXACTLY the same permissions (owner:group, chmod 755).
User A can access, read, write, delete, etc perfectly fine.
User B can access and read, but not write, delete, or anything else.

I'm not kidding when I say that the folders have exactly the same permissions, so I'm pretty confused about what's happening here :(

Thanks in advance for any answers.

---

### Post by HiImTye on 2013-06-19
why not use sftp instead? it's more secure (ftp authenticates in plain text) and easier to set up[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Daktyl198 on 2013-06-19
> why not use sftp instead? it's more secure (ftp authenyicates in plain text) and easier to set up
I would have to set up sftp without giving the users shell access, which I don't know how to do.
I have never had an issue with vsftpd before this, but I'll look into it...

---

### Post by HiImTye on 2013-06-19
[http://kpdirection.com/technology/setting-up-sftp-on-ubuntu/](http://kpdirection.com/technology/setting-up-sftp-on-ubuntu/)
you can restrict their access fairly easily
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Daktyl198 on 2013-06-19
Thanks, I'll try that out tomorrow as it's quite late right now.

The original question still stands, though.

---

### Post by Daktyl198 on 2013-06-20
Actually, that tutorial is kind of useless...
I already knew how to set up sftp, what I would need to know is how to set up sftp for a user, while blocking them from ssh access :/

---

### Post by HiImTye on 2013-06-20
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
it does the next best thing, it confines them to a chroot jail
[http://m.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://m.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)
but here's a shell-less client
[http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)

---

### Post by Daktyl198 on 2013-06-21
> **HiImTye said:**
> it does the next best thing, it confines them to a chroot jail
[http://m.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://m.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)
but here's a shell-less client
[http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)

I'll try that :D
 but I hope there is a way to choose the users you want to restrict with rssh because there are two users I don't want restricted as well...

---

### Post by HiImTye on 2013-06-21
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
use openssh for those users, you can easily use permissions to restrict who can use openssh

---

