---
title: "Odd Apache2 Problem -- Will Not Reinstall"
date: 2007-08-15
forum: General Help
---

### Post by pgupta on 2007-08-15
Well, let me detail my problem a bit.  The other day I was trying to make a move from apache to apache2.  Apache(1) was running quite well, there wasn't any kind of real problem.  Then I moved the S91apache file to K91apache and turned the process off.  Then, since there was a S91apache2 file, I tried to start apache2.

```
/etc/rc3.d/S91apache2 start
```

I ran the above command (and a few variants of it -- reload, restart, stop, etc) and nothing at all happened.  There was no error, there was no log entry (syslog, error.log, etc).  The thing did nothing.

So, I opted to try to remove the application and reinstall it.

```
apt-get remove apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  apache2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 94297 files and directories currently installed.)
Removing apache2 ...
```

And so, somethign appeared to happen.  The app was removed, right?

Then I tried install it:

```

 apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/38.4kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 94295 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2build1_all.deb) ...
Setting up apache2 (2.2.3-3.2build1) ...

```

So, it installed something.. or so it claims, but nothing works.


I'm at a complete loss here -- please help.  =)

---

### Post by chanman on 2007-08-15
I've tried installing apache2 on my laptop also. It installs fine but when I try it out ([http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1)), it does not work. Also, If I try installing mysql5, it does not install. I get this:
```

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

```

---

### Post by pgupta on 2007-08-15
> **chanman said:**
> I've tried installing apache2 on my laptop also. It installs fine but when I try it out ([http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1)), it does not work. Also, If I try installing mysql5, it does not install. I get this:
```

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

```

I don't know if our two problems are related -- have you appropriately configured apache?  does the process start?  :(

---

### Post by chanman on 2007-08-15
yes, the process starts. Everything seems fine. It's weird cause I use to have apache2 working about a month ago. Then reformated, no reason, just did it. Now it doesn't work at all.

Couple things I have done after the reformat:
- edit the /etc/network/interfaces and commented out everything. When starting up, my laptop would pause for 5 minutes on "Configuring Network Interfaces." This fixed that.
- Install compiz
- edited xong.conf

I doubt the last two would even effect apache in anyway.

---

### Post by pgupta on 2007-08-15
our problems are definitely unrelated -- sorry man =(

---

### Post by chanman on 2007-08-16
It definatelly wasn't. commenting out everything in /etc/network/interfaces was causing the error.

well at least my error was fixed. Hope you fix yours

---

### Post by pgupta on 2007-08-17
Amazing...

I'm still wondering what's wrong with my box. =\

---

