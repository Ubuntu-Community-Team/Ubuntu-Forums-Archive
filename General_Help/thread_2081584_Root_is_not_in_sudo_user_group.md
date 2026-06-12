---
title: "Root is not in sudo user group"
date: 2012-11-07
forum: General Help
---

### Post by konstruktor86 on 2012-11-07
Hi
I have Ubuntu Server 12.04.
I tried to add permission 755 for one location, but I get comunicate that root is not in sudoers file. How is this possible?
Here is screenshot:
[IMG]http://www.picshot.pl/pfiles/249502/1.jpg[/IMG]
Please, help

---

### Post by Lars Noodén on 2012-11-07
If you're running as root, you do not need to prefix your program with 'sudo'.  It is already running as root.  Even so, root should have no problem running sudo, even if it is not in the group sudo, so I wonder where the problem is.

---

### Post by konstruktor86 on 2012-11-07
> **Lars Noodén said:**
> If you're running as root, you do not need to prefix your program with 'sudo'.  It is already running as root.  Even so, root should have no problem running sudo, even if it is not in the group sudo, so I wonder where the problem is.

So, what I should do?

---

### Post by rubylaser on 2012-11-07
As Lars said, the root user is part of the root group like this, but should have no problem using sudo (although it's unnecessary).
```
root@svr-cc-marketing:~# groups
root
```

```
root@svr-cc-marketing:~# sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US 
...
```

What does your /etc/sudoers file look like?

```
cat /etc/sudoers
```

You should see a line in there like this for root.
```
root	ALL=(ALL) ALL
```

---

### Post by konstruktor86 on 2012-11-07
I have something like this:
[IMG]http://zapodaj.net/images/5c36ab13f1a62.jpg[/IMG]

---

### Post by Lars Noodén on 2012-11-07
Strange.  If /etc/sudoers exists, but is empty, then you get the not-in-sudoers error.  Yours appears to be empty.  How it got that way is a puzzle.  What you will need to do is to fill /etc/sudoers.  Here is the default.

```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

Also make sure that the permissions are right.

```

chmod 440 /etc/sudoers

```

---

### Post by konstruktor86 on 2012-11-07
Ok, but I can't save this file. When I try open it with sudo I have error:
> root@ht-50814ffc17b2c:~# sudo vi /etc/sudoers
root is not in the sudoers file.  This incident will be reported.
And when I get :
vi /etc/sudoers
I can't save it. :(

---

### Post by Lars Noodén on 2012-11-07
If you're root, you don't need to preceed your lines with 'sudo'  Just use plain vi

```

vi /etc/sudoers
chmod 440 /etc/sudoers

```

When you have edited the file, open a new terminal and test it there.  Don't close the terminal you have with root until things are working.

To force as save use the !

**:w!**

---

### Post by konstruktor86 on 2012-11-07
Ok, I done this and it works :)
But, I still have a problem to give permission 755 to my file. :(
[IMG]http://www.picshot.pl/pfiles/249549/3.jpg[/IMG]

---

### Post by Lars Noodén on 2012-11-07
Try it with out the -r, you can either use rwx and some combination of ugo (user, group, other) or list a number in octal for [chmod](http://manpages.ubuntu.com/manpages/precise/en/man1/chmod.1posix.html) but not both at the same time.

```

chmod 755 /etc/zabbix/clickatell.php
chmod u=rwx,g=rx,o=rx /etc/zabbix/clickatell.php

```

---

### Post by konstruktor86 on 2012-11-07
Ok, I done this
Command ls -l give me resultat:
> -rwxr-xr-x 1 root root 3980 Nov  6 23:18 /etc/zabbix/alert.d/cli_sms_clickatell.php

It's ok?
I don't know because when I try to run script i have this message:
[IMG]http://www.picshot.pl/pfiles/249564/34.jpg[/IMG]

---

### Post by Lars Noodén on 2012-11-07
To run it, the program must be in your $PATH or else you must specify the path to the program when you try to run it.  You can try to run it two ways:

```

/etc/zabbix/alert.d/cli_sms_clickatell.php 

cd /etc/zabbix/alert.d/
./cli_sms_clickatell.php 

```

---

### Post by Lars Noodén on 2012-11-07
PS.  Scripts should generally not go in /etc, that directory is for configuration data.  There is [a place for them](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html) in /usr/local/bin or in ~/bin

---

