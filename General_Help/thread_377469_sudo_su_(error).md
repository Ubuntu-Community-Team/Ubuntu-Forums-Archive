---
title: "sudo su (error)"
date: 2007-03-06
forum: General Help
---

### Post by hudelfa on 2007-03-06
Hi my friends after along time!

I updated  ubuntu dapper drake to edgy eft .and  I got some errors in edgy eft.

1-When I wrote sudo su  in the congole to take root privileges  it appears an error reads `configuration error - unknown item 'FAIL_DELAY' (notify administrator)`. How can I fix this problem.

2-I can not access  my folders in ntfs  partitions any more.I could access before.

---

### Post by mac.ryan on 2007-03-06
> **hudelfa said:**
> 1-When I wrote sudo su  in the congole to take root privileges  it appears an error reads `configuration error - unknown item 'FAIL_DELAY' (notify administrator)`. How can I fix this problem.

Hello, I am far from being a linux guru, but... are you sure you have to type "sudo su"? In my understanding, "sudo" serves to execute a command as "super user", and should be typed in front of each command you require root priviledges, while "su" changes the logged users into a new user (possibly the "super user") giving you permanently (for that sessions) its priviledges...

([COLOR=Red]EDIT: the "sudo su" command is indeed correct, please read following post by mcduck[/COLOR])

> 2-I can not access  my folders in ntfs  partitions any more.I could access before.Can you give some more details about the problem? Are your drives mounted correctly? Can you see the the folders even if you can't enter them? ... ?

[COLOR=Red]EDIT:[/COLOR] I am also not sure you can become super user in ubuntu, as I believe there is no root account installed, just the possibility for the user created during installation to run commands with sudo!

---

### Post by mcduck on 2007-03-06
1) Try using 'sudo -i' instead of 'sudo su'. This should correctly load root user's configurations. (mac.ryan: you can't run 'su' as that would require root password that you don't have in Ubuntu. that's why you would use 'sudo su' to get the same result. but indeed 'sudo -i' is the best way)

2) could you post your /etc/fstab and output of 'sudo fdisk -l' here?

---

### Post by hudelfa on 2007-03-07
Thanks very much  for  ''sudo -i''  I fixed this problem. But I  want to know  what -i parameter means.

And my  ''fdisk-l '' output here.

---

### Post by hudelfa on 2007-03-07
My  "fdisk-l" output.

---

### Post by cookfromfrozen on 2007-03-07
> **hudelfa said:**
> 1-When I wrote sudo su  in the congole to take root privileges  it appears an error reads `configuration error - unknown item 'FAIL_DELAY' (notify administrator)`
Open the file /etc/login.def as root (or use the recovery console if you can no longer sudo) and look for any FAIL_DELAY lines and remove them.

---

### Post by hudelfa on 2007-03-07
and  my  fstab  output  ...

---

### Post by Carl H on 2007-03-07
> **hudelfa said:**
> Thanks very much  for  ''sudo -i''  I fixed this problem. But I  want to know  what -i parameter means.

It runs a terminal as the root user, which saves you having to keep typing "sudo" before every command. 

Note how the prompt changes :- 
```

carl@ground-control:~$ sudo -i
root@ground-control:~#
```

---

### Post by mcduck on 2007-03-09
In short the -i makes the shell behave as if you really had logged in as root, properly loading root user's environment.  When you use "sudo -i" you should also keep in mind that it moves you to /root (root user's home directory. Just like when you open a terminal it opens in your home dir).

Here's the -i part of "man sudo":
```
The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user&#8217;s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.
```

For the NTFS partitions, sorry but I forgot to ask for your /etc/fstab as well. But at least fdisk sees the partitions so we should be able to get them working..

Actually you could also run "ls -la /dev/disk/by-uui" to get a list of UUID numbers for your partitions. We'll probably need that with your fstab anyway.

---

