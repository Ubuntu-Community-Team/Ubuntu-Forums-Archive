---
title: "sudo apt-get update won't work"
date: 2013-08-17
forum: General Help
---

### Post by Underpaw on 2013-08-17
Hello I have a serious problem. When ever I'm trying to run sudo apt-get update I'm getting:
W: Unable to read /etc/apt/apt.conf.d/ - DirectoryExists (20: Not a directory)
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: No keyring installed in /etc/apt/trusted.gpg.d/.

What is the problem? The only files I have in /etc/apt is apt.conf and sources.list. That's it.

---

### Post by Buntu Bunny on 2013-08-17
My guess is it's because Hardy Heron reach end of life in May. There are no updates for it anymore.

---

### Post by Cheesemill on 2013-08-17
What version of Ubuntu are you using?

The lines that are giving you errors are for version 8.04 of Ubuntu which is no longer supported.

---

### Post by Underpaw on 2013-08-17
I'm using 12.04.

---

### Post by Cheesemill on 2013-08-17
I don't know what those lines are doing in your sources.list but we need to remove them. Can you post the output of...
```
cat -n /etc/apt/sources.list
```

---

### Post by Underpaw on 2013-08-17
> **Cheesemill said:**
> I don't know what those lines are doing in your sources.list but we need to remove them. Can you post the output of...
```
cat -n /etc/apt/sources.list
```

* Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Sat Aug 17 12:08:12 2013 from s***********
root@szx0yo:~# cat -n /etc/apt/sources.list
     1  # See sources.list(5) for more information, especialy
     2  # Remember that you can only use http, ftp or file URIs
     3  # CDROMs are managed through the apt-cdrom tool.
     4  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
     5  deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
     6
     7  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
     8  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
     9
    10  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
    11  deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted

---

### Post by Cheesemill on 2013-08-17
Are you sure you are running 12.04? Your entire sources.list file is from version 8.04 of Ubuntu, and this won't have happened by accident. Have you made any changes to this file at all?

You can check which version you are running with the following command...
```
lsb_release -a
```

If it really is precise (12.04) then you can use this website to generate yourself a new sources.list file although it would still be interesting to figure out why this has happened.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Underpaw on 2013-08-17
It is precise 12.04:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise


Now when I'm trying to run sudo apt-get update I'm getting:

W: Unable to read /etc/apt/apt.conf.d/ - DirectoryExists (2: No such file or directory)
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: No keyring installed in /etc/apt/trusted.gpg.d/.

---

### Post by ibjsb4 on 2013-08-17
Have you recently done an upgrade to 12.04?

---

