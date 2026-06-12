---
title: "/Opt directory problem, Please help"
date: 2007-04-13
forum: General Help
---

### Post by ssharish on 2007-04-13
Hi,

I am really very new this Linux environment, i had been using windows for ages and from past few years started hate it because of their restriction on so many thing. Any way here is problem.

I was trying to program a board called viper-lite, i was setting up development environment so that i can start programming that board. 

I was trying to install the tool which i need to program the board it was all in compressed format. The instruction says that i got to copy those tar file on to the /opt directory and uncompress it.

It tried copying the file to /opt it copied, but it copied to a /opt file rather than opt directory.

This is what it looks like, when i browse my root directory

```

drwxr-xr-x   2 root root     4096 2007-04-07 23:35 lib64
drwxr-xr-x   2 root root    49152 2007-04-07 21:46 lost+found
drwxr-xr-x   4 root root     4096 2007-04-10 21:15 media
drwxr-xr-x   2 root root     4096 2006-10-19 23:49 mnt
[COLOR="Red"]-rw-r--r--   1 root root 88281557 2007-04-13 21:53 opt[/COLOR]
dr-xr-xr-x 114 root root        0 2007-04-13 14:14 proc
drwxr-xr-x   6 root root     4096 2007-04-13 21:44 root
drwxr-xr-x   2 root root     4096 2007-04-07 23:35 sbin
drwxr-xr-x   2 root root     4096 2006-10-25 15:03 srv
-rw-r--r--   1 root root        0 2007-04-08 01:01 ssh_confi

```

If you can see opt is not a directory. Why is this? Can anyone please help 

thank you

ssharish

---

### Post by Maestro23 on 2007-04-13
Need to make the /opt directory.

> sudo mkdir /opt

Then use "sudo" in front of your copy command to copy your files there.  You need "sudo" because the directory is owned by root "/".

*Remove the opt file: sudo rm opt

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ssharish on 2007-04-13
Maestro23 thanks very much for your reply. I through the opt directory are created at the time of installation itself.

I never knew that the user need to create the folder. 

Any way thanks very much

ssharish

---

### Post by ssharish on 2007-04-13
right i have one more question, how do i add a path on to my bash profile file. Where is it located. How do i add

```

PATH=/opt/gnutools/arm-elf/bin:$PATH ; export PATH

```

Thank you

ssharish

---

### Post by ssharish on 2007-04-13
Never mind i solved it

ssharish

---

