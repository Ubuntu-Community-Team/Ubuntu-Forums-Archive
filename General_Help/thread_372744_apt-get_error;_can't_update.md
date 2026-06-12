---
title: "apt-get error; can't update"
date: 2007-02-28
forum: General Help
---

### Post by th3gh05t on 2007-02-28
Hi,

I have been having lots of problems with apt-get recently.

Here is the error that I am receiving when I hover over the orange icon:

> A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'

When I run 'sudo apt-get install -f' from the terminal, this is what I get:

> derek@ghost:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 159064 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I fix this issue?

---

### Post by Ramses de Norre on 2007-02-28
Try ```
sudo aptitude clean && sudo aptitude autoclean && sudo aptitude install samba
```

---

### Post by th3gh05t on 2007-02-28
Thanks!

But this is what happened after that cmd:

> derek@ghost:~$ sudo aptitude clean && sudo aptitude autoclean && sudo aptitude install samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Freed 0B of disk space
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  kdelibs-bin kdelibs4c2a libc6 libc6-dev libc6-i686 opera
The following packages will be upgraded:
  samba
1 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 2845kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba 3.0.22-1ubuntu3.2 [2845kB]
Fetched 2845kB in 15s (179kB/s)
Preconfiguring packages ...
(Reading database ... 159107 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by Ramses de Norre on 2007-03-02
Could you try running ```
sudo /etc/init.d/samba stop
``` and try those commands again then?

If that doesn't work, can you do **file-roller /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb ** then go to control.tar.gz, click on the . directory and open prerm with gedit. Has it got the same contents as this:

```
#!/bin/sh -e

if [ "$1" = upgrade -a -n "$2" ] && dpkg --compare-versions "$2" lt 2.99 \
   && [ -e /var/lib/samba/passdb.tdb -a ! -e /etc/samba/smbpasswd ]
then
	pdbedit -i tdbsam -e smbpasswd
	rm -f /var/lib/samba/passdb.tdb
fi

# Automatically added by dh_installinit
if [ -x "/etc/init.d/samba" ]; then
	if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
		invoke-rc.d samba stop || exit $?
	else
		/etc/init.d/samba stop || exit $?
	fi
fi
# End automatically added section


```

---

### Post by th3gh05t on 2007-03-02
Command not found.

> derek@ghost:~$ sudo /etc/init.d/sambo stop
sudo: /etc/init.d/sambo: command not found


---

### Post by gejr on 2007-03-02
sambo = samba

---

### Post by th3gh05t on 2007-03-02
Still doesn't work:

> 
derek@ghost:~$ sudo /etc/init.d/samba stop
Password:
 * Stopping Samba daemons...                                             [ ok ]
derek@ghost:~$ sudo aptitude clean && sudo aptitude autoclean && sudo aptitude install samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Freed 0B of disk space
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  firefox firefox-gnome-support kdelibs-bin kdelibs4c2a libc6 libc6-dev libc6-i686 libnspr4 libnss3 opera
The following packages will be upgraded:
  samba
1 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 2845kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba 3.0.22-1ubuntu3.2 [2845kB]
Fetched 2845kB in 10s (262kB/s)
Preconfiguring packages ...
(Reading database ... 159107 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by th3gh05t on 2007-03-06
Hi,

Does anyone know why this is happening? It looks my 'samba' is broken and can't be fixed.

> 
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is to  be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).
derek@ghost:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 159107 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_ i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Aikon- on 2007-03-06
I am getting a similar problem (different dangling symlink name) with Samba. See my thread here:

[http://www.ubuntuforums.org/showthread.php?t=377179](http://www.ubuntuforums.org/showthread.php?t=377179)

No replies for me yet.

---

### Post by th3gh05t on 2007-03-08
Hi,

Can someone please help me out with this problem?

I don't care about samba, I don't even use it. I just want apt-get to be working again so that I can install new programs.

This is the error code I get when I try to update the package:

> E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb: subprocess new pre-removal script returned error exit status 102

This is the error message I get when I try and "Mark for Complete Removal":

> E: samba: subprocess pre-removal script returned error exit status 102


Thanks for your time and effort!

---

### Post by cyborgspiders on 2007-03-13
same game for me over here......
can't use apt-get

The following packages will be REMOVED:
  samba
0 packages upgraded, 0 newly installed, 1 to remove and 40 not upgraded.
Need to get 0B of archives. After unpacking 7250kB will be freed.
Writing extended state information... Done
(Reading database ... 135569 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

