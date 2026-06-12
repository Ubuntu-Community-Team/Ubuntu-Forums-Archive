---
title: "nautilus ftp no folders displayed"
date: 2008-01-15
forum: General Help
---

### Post by phillips321 on 2008-01-15
hello guys,

i'm trying to connect to an ftp server using nautilus.

I have a problem in that for some reason the directory contents is not displayed.

The server is running server2003 iis.

i know my credentials are correct because i can connect using FireFTP within firefox and using secureftp.

one thing i have noticed is that when i connect using the command line i can use the command "pwd" and it shows i am connected fine, but when i try to connect using nautilus i dont get a connection error so it looks like i'm connected but i dont see any folders (i know there are some present)

any ideas guys?

(p.s. i connected to ftp.gnome.org to test nautilus ftp works)

---

### Post by phillips321 on 2008-01-15
i've also noticed that the ls command doesn't work from the command line, is that normal?

```
phillips321@LinuxDesktop:~$ ftp ftp.arm.linux.org.uk
Connected to zeniv.linux.org.uk.
220 (vsFTPd 2.0.5)
Name (ftp.arm.linux.org.uk:phillips321): anonymous
331 Please specify the password.
Password:
230-Welcome to ZenIV
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
500 Illegal PORT command.
ftp: bind: Address already in use
ftp> quit
221 Goodbye.
phillips321@LinuxDesktop:~$ 

```

---

