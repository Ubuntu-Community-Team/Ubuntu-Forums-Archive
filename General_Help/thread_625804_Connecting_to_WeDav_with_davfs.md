---
title: "Connecting to WeDav with davfs"
date: 2007-11-28
forum: General Help
---

### Post by HarryMcScary on 2007-11-28
I'm trying to mount a WebDav server with davfs and having trouble with authentication.  I've followed the [tutorial](http://ubuntuforums.org/showthread.php?t=202761), and tried the tip [here](http://ubuntuforums.org/showthread.php?t=137080), with no luck.  The server is Windows, and uses windows authentication.

Here's the output of my last attempt- all of them are about the same.
> matt@matt-desktop:~$ su
Password: 
root@matt-desktop:/home/matt# mount -t davfs [http://wvprcfs.marshall.edu/rlo_testing/](http://wvprcfs.marshall.edu/rlo_testing/) /media/marshall.edu/
Please enter the username to authenticate with server
[http://wvprcfs.marshall.edu/rlo_testing/](http://wvprcfs.marshall.edu/rlo_testing/) or hit enter for none.
Username: [email]smith905@marshall.edu[/email]
Please enter the password to authenticate user [email]smith905@marshall.edu[/email] with server
[http://wvprcfs.marshall.edu/rlo_testing/](http://wvprcfs.marshall.edu/rlo_testing/) or hit enter for none.
Password: 
/sbin/mount.davfs: Mounting failed.
401 Access Denied
Thanks in advance for any help!

---

