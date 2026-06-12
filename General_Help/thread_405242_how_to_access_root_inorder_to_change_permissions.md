---
title: "how to access root inorder to change permissions"
date: 2007-04-09
forum: General Help
---

### Post by hopefull on 2007-04-09
Hi

I have installed feisty and I am trying to install my scanner, lookiing at some howto's for epson perfection  3490 i see I need to change some permissions but I cannot work out how to access these files as root. I have looked at the how to login as root thread but I cannot work out how to apply this to gaining access to files. Could anyone help? I have set up a root pass word using sudo passwd root but how do i go from that to launching file browsers so I can change the permissions?

Cheers

hopefull

---

### Post by Kizilbas on 2007-04-09
Applications>>System>>Users & Groups>>(enter your password) and do the permission changes.

You can then select the user, e.g. **root** & click on Properties>>User Privileges


Hope that helps, I'm very newb.. I woudn't want to mislead you.

---

### Post by taurus on 2007-04-09
Please be real careful with changing permissions of anything outside your $HOME directory.  Doing so could crash your machine.  Instead, use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by altaaa on 2007-04-09
You can also assign permissions using the Gnome Terminal.

It works as follows: if you type in ls -al, you get a list of all files and directories in your current directory.  Like this: (as you can see my current directory is /boot)

```
ruurd@ruurd-laptop:/boot$ ls -al
total 16164
drwxr-xr-x  3 root root    4096 2007-02-13 22:28 .
drwxr-xr-x 21 root root    4096 2007-02-13 22:28 ..
-rw-r--r--  1 root root  285721 2006-12-05 23:47 abi-2.6.17-10-generic
-rw-r--r--  1 root root  285721 2007-02-01 21:11 abi-2.6.17-11-generic
-rw-r--r--  1 root root   74707 2006-12-05 22:20 config-2.6.17-10-generic
-rw-r--r--  1 root root   74707 2007-02-01 19:44 config-2.6.17-11-generic
drwxr-xr-x  2 root root    4096 2007-03-03 11:02 grub
-rw-r--r--  1 root root 5455400 2007-02-13 22:28 initrd.img-2.6.17-10-generic
-rw-r--r--  1 root root 5454346 2007-02-13 22:28 initrd.img-2.6.17-11-generic
-rw-r--r--  1 root root   94600 2006-10-20 13:44 memtest86+.bin
-rw-r--r--  1 root root  728778 2006-12-05 23:47 System.map-2.6.17-10-generic
-rw-r--r--  1 root root  729932 2007-02-01 21:12 System.map-2.6.17-11-generic
-rw-r--r--  1 root root 1636700 2006-12-05 23:47 vmlinuz-2.6.17-10-generic
-rw-r--r--  1 root root 1636239 2007-02-01 21:11 vmlinuz-2.6.17-11-generic
```

Do you see  the first column? Those are the filesystem rights. The "root root" stands for owner:root group:root. There is a pretty straightforward system in those r's and w's and x's :) The first character is d, which stands for directory. This one is not interesting. Next you get this: 

```
rwxrwxrwx
```

Which stands for

```
rwx     rwx     rwx
owner   group   rest
```

All those r's, w's and x's can be changed with the tool chmod. Chmod takes a number and a filename as argument. The number can be calculated like this:

```
rwx rwx rwx
421 421 421
```

Just add the numbers, and pass that through to chmod.

For instance, if I have a file on which I want to give the owner full rights (rwx), the group Read & Execute (rx) and the rest only Read (r), the numbers would be 7 for rwx (4+2+1), 5 for rx and 4 for r.

As root, type in this:

```
chmod 754 filename
```

Take a look at how this goes. I have a file named testing with the permissions rw for owner, r for group and r for rest. Looking at the numbers, the current number is 744. Let's change that: (If you are the owner of the file you don't have to be root to change it)

```
ruurd@ruurd-laptop:~$ ls -al testing
-rw-r--r-- 1 ruurd ruurd 0 2007-04-09 21:08 testing
ruurd@ruurd-laptop:~$ chmod 754 testing 
ruurd@ruurd-laptop:~$ ls -al testing
-rwxr-xr-- 1 ruurd ruurd 0 2007-04-09 21:08 testing
```

This also works on directories. With this knowledge you can change the permissions on the files (and/or directories) you need to. As stated above, **Be Careful When Changing Stuff As Root!**

Sorry for the long post! ;-)

---

