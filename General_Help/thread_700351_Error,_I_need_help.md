---
title: "Error, I need help"
date: 2008-02-18
forum: General Help
---

### Post by glmoring on 2008-02-18
[SIZE="4"]I'm getting the following error:[/SIZE]



Errors were encountered while processing:

amavisd-new

amavisd-new-milter

emdebian-tools



[SIZE="4"]The entire script is as follows.[/SIZE]


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up amavisd-new (1:2.4.2-6.2ubuntu1) ...
Creating/updating amavis user account...
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "gary-desktop", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing amavisd-new (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of amavisd-new-milter:
 amavisd-new-milter depends on amavisd-new (= 1:2.4.2-6.2ubuntu1); however:
  Package amavisd-new is not configured yet.
dpkg: error processing amavisd-new-milter (--configure):
 dependency problems - leaving unconfigured
Setting up emdebian-tools (0.2.0) ...
Unable to determine apt-cache policy for Debian main! at /var/lib/dpkg/info/emdebian-tools.postinst line 132.
dpkg: error processing emdebian-tools (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amavisd-new
 amavisd-new-milter
 emdebian-tools



[I][SIZE="3"]
Please help[/SIZE][/I].

---

### Post by seventhc on 2008-02-18
What command did you run???

---

### Post by glmoring on 2008-02-18
I ran apt-get install.

---

### Post by seventhc on 2008-02-18
it should be
```
sudo apt-get install <package_name>
```
or you can also
```
sudo aptitude install <package_name>
```
where package name is the name of what you are trying to install.
probably you need
```
sudo apt-get install amavisd-new
```

---

### Post by glmoring on 2008-02-18
Now I'm getting this:


~$ sudo apt-get install amavisd-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amavisd-new is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up amavisd-new (1:2.4.2-6.2ubuntu1) ...
Creating/updating amavis user account...
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "gary-desktop", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing amavisd-new (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of amavisd-new-milter:
 amavisd-new-milter depends on amavisd-new (= 1:2.4.2-6.2ubuntu1); however:
  Package amavisd-new is not configured yet.
dpkg: error processing amavisd-new-milter (--configure):
 dependency problems - leaving unconfigured
Setting up emdebian-tools (0.2.0) ...
Unable to determine apt-cache policy for Debian main! at /var/lib/dpkg/info/emdebian-tools.postinst line 132.
dpkg: error processing emdebian-tools (--configure):
 subprocess post-installation script returned error exit status 255
[COLOR="Red"]Errors were encountered while processing:
 amavisd-new
 amavisd-new-milter
 emdebian-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

---

### Post by seventhc on 2008-02-18
I'm not positive since I don't use this program, but from your error msg, it looks like you need to create some directories. Or needs to be configured
```

Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "gary-desktop", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
```
There is some documentation and a troubleshooting guide here:
[http://www.ijs.si/software/amavisd/](http://www.ijs.si/software/amavisd/)

---

