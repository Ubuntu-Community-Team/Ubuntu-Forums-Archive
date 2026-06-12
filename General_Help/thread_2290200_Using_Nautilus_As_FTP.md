---
title: "Using Nautilus As FTP"
date: 2015-08-10
forum: General Help
---

### Post by bigpappajohn1984 on 2015-08-10
On Ubuntu is it possible to use Nautilus as an ftp client?  if so, how would I do such?

---

### Post by Lars Noodén on 2015-08-10
One way is to press ctrl-L and then enter the URI

```

ftp://somesite.example.com/dir/subdir/

```

Then use the default, "Anonymous FTP"

If you want to actually use a login with a password, then FTP should be avoided like the plague and SFTP should be used instead.

---

### Post by bigpappajohn1984 on 2015-08-10
Yes, SFTP is what I would want to use.  Is their a good tutorial on how to set this up?

Mostly, how to create a user and ONLY give that specified user access to 1 directory (or maybe the proper terminology is set the home directory for that user)

---

### Post by Lars Noodén on 2015-08-10
The connection would be like this for SFTP:

```

**s**ftp://somesite.example.com/dir/subdir/

```

SFTP is easy to set up on the server side, if you use the one that is in the package OpenSSH-server.  For basic service, just install the package openssh-server from the repository.  If your machine is facing the open Internet, then it would be a good idea to disable passwords and require keys instead.  Nautilus will work with SSH keys.

---

### Post by bigpappajohn1984 on 2015-08-10
How do I give a specified user access to just ONE directory?  For example, let's say I create two accounts, Account one: TestUser1 Account two: TestUser2 -- I want TestUser1 to ONLY have access to testfolder1 and want TestUser2 to ONLY have access to testfolder2 -- how would I set that up?  (I'm just spoiled with the very easy to use GUI that Windows Filezilla Server provides, haha

---

### Post by Lars Noodén on 2015-08-10
That would be done by using the server settings to force a group of users to use SFTP only and then chroot them to specific directories.  One common configuration for home directories could be like this:

```

Subsystem sftp internal-sftp

Match Group sftp-only
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u

```

That would force users in the group 'sftp-only' to use only SFTP, no shell access.  The details are in the manual page for [sshd_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html)

In that style of configuration, if it is necessary to hide the contents of the home directories from other users, chmod should be used. Permissions could be 0711 for /home and 0751 for the users' directories.

---

### Post by bigpappajohn1984 on 2015-08-10
And where would I place that syntax above?  Is that in the terminal window or would that be input into a config file?

---

### Post by Lars Noodén on 2015-08-10
That would go at the tail end of /etc/ssh/sshd_config

You can edit it like this:

```

sudoedit /etc/ssh/sshd_config

```

and that should give the [nano](http://manpages.ubuntu.com/manpages/trusty/en/man1/nano.1.html) editor.

---

### Post by bigpappajohn1984 on 2015-08-10
How do I create the group?  I believe I have everything all set other than that!
```

Subsystem sftp internal-sftp
Match Group sftp-only
        ChrootDirectory /home/Testingdirectory
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u


```

---

### Post by Lars Noodén on 2015-08-10
> **bigpappajohn1984 said:**
> How do I create the group?  I believe I have everything all set other than that!
```

Subsystem sftp internal-sftp
Match Group sftp-only
        ChrootDirectory /home/Testingdirectory
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u


```

Also, /home/Testingdirectory/testuser1 and /home/Testingdirectory/testuser2 need to exist while /home/Testingdirectory itself must be owned by root.  

To create the group

```

sudo addgroup sftp-only
sudo gpasswd -a testuser1 sftp-only

```

---

### Post by bigpappajohn1984 on 2015-08-10
Ahh...thank you for the tip on the directory structure.  Each user would need their own directory!

Your syntax above creates the group, how would I create the user then assign to the group?

---

### Post by Lars Noodén on 2015-08-10
gpasswd assigns the user to the group

---

### Post by bigpappajohn1984 on 2015-08-10
and this would set the home directory and only give the user access to the one directory?
```

ChrootDirectory /home/Testingdirectory/testuser1

```

---

### Post by Lars Noodén on 2015-08-10
> **bigpappajohn1984 said:**
> and this would set the home directory and only give the user access to the one directory?
```

ChrootDirectory /home/Testingdirectory/testuser1

```

Yes, but then it would have to be owned by root and not writable by anyone else.  (That requirement is hidden in the manual page for sshd_config) In order for it to be usable, you'd have to populate it with subdirectories.  The subdirectories can be owned and writable by anyone.

---

