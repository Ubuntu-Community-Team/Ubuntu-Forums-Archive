---
title: "Problem with creating ssh chroot"
date: 2015-07-24
forum: General Help
---

### Post by peter1897 on 2015-07-24
I have user bob to which i want to give him shell access but i want to limit his access only to his home directory. In sshd_config file i added these lines at the end:

```
Match User bob
          ChrootDirectory /home
```

The home directory is owned by root:

```
max@ubuntu:/home$ ll
total 16
drwxr-xr-x  4 root root 4096 Jul 23 22:55 ./
drwxr-xr-x 21 root root 4096 Jul 21 23:40 ../
drwxr-xr-x  3 bob  bob  4096 Jul 24 00:52 bob/
drwxr-xr-x  9 max  max  4096 Jul 23 15:27 max/
```

But user bob is not able to connect to the server. I get this message:
```
Could not chdir to home directory /home/bob: No such file or directory
/bin/bash: No such file or directory
```


How to setup shell chroot for user bob?

---

### Post by Lars Noodén on 2015-07-24
The chroot concept is a little strange but when using it, you're changing the top directory / so if the chroot is /home, what the system sees on bob's behalf is

```

max@ubuntu:/ $ ll
total 16
drwxr-xr-x  4 root root 4096 Jul 23 22:55 ./
drwxr-xr-x 21 root root 4096 Jul 21 23:40 ../
drwxr-xr-x  3 bob  bob  4096 Jul 24 00:52 bob/
drwxr-xr-x  9 max  max  4096 Jul 23 15:27 max/

```

Note that first line, so /home is not there but /bob and /max are.  So his home directory needs to get changed to /bob but ... there's a lot more.  You have to build up copies or hardlinks of all the devices and utilities he might use, such as bash, ls, cp, mv and so on.  It's a lot of work.  There might be another option first.  Have you considered making his shell [rbash](http://manpages.ubuntu.com/manpages/trusty/en/man1/rbash.1.html) instead and giving him a custom $PATH?

Chrooted SFTP is, on the other hand, very easy to set up.  Perhaps you can get by with that.

---

### Post by peter1897 on 2015-07-24
For sftp chroot is it enough to edit only the sshd_config file? I created a new user demo and in sshd_config file i added these lines:
```
Match User demo
    ChrootDirectory /home
    ForceCommand internal-sftp
    AllowTCPForwarding no
    X11Forwarding no
```

And now user demo can connect to the server through sftp but do i have to change any of the settings for user demo in passwd file which are these:
```
max@ubuntu:~$ cat /etc/passwd | grep demo
demo:x:1002:1002:,,,:/home/demo:/bin/bash
```

If i try to login as user demo through ssh i am not able to and i get this message:
```
Could not chdir to home directory /home/demo: No such file or directory
This service allows sftp connections only.
```

But in therms of security do i have to change /bin/bash to /bin/false or /bin/nologin or it is not necessary?

---

### Post by Lars Noodén on 2015-07-24
Yes, for SFTP chroot, it is enough to change sshd_config.  

If you want that user to start in his home directory you could use this instead:

```

    ChrootDirectory /home/%u 

```

The %u gets substituted for the user name.

---

### Post by peter1897 on 2015-07-24
Thanks.
Can you give me a brief guide how to restrict a user with rbash?

---

### Post by Lars Noodén on 2015-07-24
You would make the user's own shell be /bin/rbash instead of /bin/bash.  That supplies the basic restrictions.  

Then it could get more complex if you want to restrict which programs the restricted user can run.  To do that you have to change their path and that is done in ~/.profile, but to keep it that way you'd have to take away write access and ownership of the top level of their own home directory as well as that of ~/.profile so that they can't change it back.

---

### Post by peter1897 on 2015-07-24
I changed the shell for user bob with this command:
```
sudo chsh -s /bin/rbash bob
```

```
max@ubuntu:/home/bob$ cat /etc/passwd | grep bob
bob:x:1001:1001:,,,:/home/bob:/bin/rbash
```

How can i see which commands bob can run? Also, can i allow him to use the cd command but only to go in folders that are inside his home directory but not to be able to go above his home directory?

---

### Post by Lars Noodén on 2015-07-25
With rbash, cd is limited and cannot start with ., .. or / but ls arguments can.  So he can still look but not cd.  

As far as which commands he can use, you'd have to log in as him to be sure and then check the $PATH

```

sudo su -l bob
for path in $(echo $PATH | sed "s/:/ /g" ); do find $path -maxdepth 1 -type f; done

```

If you want to limit the commands he can use, then either trim $PATH to just the directories he is allowed or point to a new directory containing links to only the programs he actually is allowed.  If you do that, make sure that he can't change .bashrc or .profile.

---

### Post by peter1897 on 2015-07-25
Thanks!

---

