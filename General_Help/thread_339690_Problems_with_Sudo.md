---
title: "Problems with Sudo"
date: 2007-01-16
forum: General Help
---

### Post by Catsworth on 2007-01-16
Hi Guys,

I've just installed Ubuntu 6.10 (having previously been a part-time user of 6.06) with the aim of completely replacing my Windows install and I've run into problems straight away.

Ubuntu has done to me on this install exactly what it did on the last one, it's left me off of the sudoers list.

The list has root (obviously) able to use Sudo, and members of the admin group.

I've changed my group so I'm a member of the admin group but it still won't let me use Sudo, and it won't let me edit the sudoers list to put my user id onto it.

I seem to recall that there was a workaround (fudge) that involved editing the grub bootloader at startup, and adding some sort of runlevel command, that would get 'round this but I can't remember what it is.

Can anybody point me in the right direction, or tell me what I'm doing wrong?

Also, this is the second time a Ubuntu install hasn't automatically set the owner account up as a sudoer.  Should I report this as a bug?

Thanks,

Cats

---

### Post by Rhubarb on 2007-01-16
I've never had this problem with any of my Ubuntu installs (5.10, 6.04, 6.10).

The file in question that you need to fix up is:      /etc/sudoers

Unfortunately I'm at work stuck in front of a windowz box so I can't give you an example of the file's contents.

---

### Post by Catsworth on 2007-01-16
Thanks Rhubarb, I knew the file I just can't edit it to add myself to the sudoers list.....because I'm not on the sudoers list :-(

---

### Post by Catsworth on 2007-01-16
Ok, slight twist.....

I've just checked the sudoers file again (from within my Windows install, using a nice little program that allows you to explore Linux file systems) and it looks like I am in the sudoers list.

Here's the sudoers file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
rob ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Is there any other reason why sudo might be failing?

---

### Post by Rhubarb on 2007-01-16
I can't help you out much more, but if you need root privileges you could try this:

[http://www.ubuntuforums.org/showpost.php?p=1717214&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1717214&postcount=7)

---

### Post by schilcha on 2007-01-16
My /etc/sudoers looks pretty much the same. 
Try ```
sudo -l
```
On my machine, it gives:
```

User schilcha may run the following commands on this host:
    (ALL) ALL
    (root) NOPASSWD: /sbin/poweroff
    (root) NOPASSWD: /sbin/reboot
    (root) NOPASSWD: /sbin/shutdown

```

How did you add yourself to the admin-group without sudo-access? Are you sure, you're a member of admin gourp. 

Try booting off a live-cd and fix the problem from there.

Good luck!

---

### Post by Zill on 2007-01-17
> # User privilege specification
root	ALL=(ALL) ALL
rob ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

My sudoers file does not have any named users listed at all so your reference to "rob ALL=(ALL) ALL" is worrying.

As a wild guess can I ask if you tried, during setup, to enter your first user with the username of root?  If so, this is **not** the correct way to do it.  The first user should always be an ordinary user, and then sudo is automatically given to this user.  Some distros do first ask for a root user/password, but that is not the Ubuntu way :-)

Once the first user is up and running it is then easy to add more users, with sudo access if wanted, via the System, Administration menu.

---

### Post by Catsworth on 2007-01-18
> **Zill said:**
> My sudoers file does not have any named users listed at all so your reference to "rob ALL=(ALL) ALL" is worrying.

As a wild guess can I ask if you tried, during setup, to enter your first user with the username of root?  If so, this is **not** the correct way to do it.  The first user should always be an ordinary user, and then sudo is automatically given to this user.  Some distros do first ask for a root user/password, but that is not the Ubuntu way :-)

Once the first user is up and running it is then easy to add more users, with sudo access if wanted, via the System, Administration menu.

Nope, the first user is called 'rob'.  I added that account (but I'm not sure how) to the sudoers list when Ubuntu wouldn't let me do anything as sudo.  Neither the first user account nor the first user's group (with the same name) had been added to the sudoers list, only root and the admin group.

---

### Post by Pobega on 2007-01-18
Well if you're able to look at /etc/sudoers, doesn't that mean you've got all of the privledges you'd want?

> pobega@ackbar:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
pobega@ackbar:~$ sudo cat /etc/sudoers
Password:
# /etc/sudoers

---

