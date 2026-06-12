---
title: "Error when Installing something"
date: 2013-09-07
forum: General Help
---

### Post by ali6 on 2013-09-07
Hello, first of all thank you for atleast considering helping me (much appreciated). Everytime i install something on my VPS i an error after the installation is complete Scroll down to see an example. I tried googling the error but i cant find any solutions. If anyone know how to fix it please reply to this post. Thanks ! - Ali

root@vps:~# sudo apt-get install sqlite
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libsqlite0
Suggested packages:
  sqlite-doc
The following NEW packages will be installed:
  libsqlite0 sqlite
0 upgraded, 2 newly installed, 0 to remove and 251 not upgraded.
4 not fully installed or removed.
Need to get 206 kB of archives.
After this operation, 505 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libsqlite0 amd64 2.8.17-7fakesync1build1 [189 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe sqlite amd64 2.8.17-7fakesync1build1 [17.3 kB]
Fetched 206 kB in 0s (788 kB/s)
Selecting previously unselected package libsqlite0.
(Reading database ... 63518 files and directories currently installed.)
Unpacking libsqlite0 (from .../libsqlite0_2.8.17-7fakesync1build1_amd64.deb) ...
Selecting previously unselected package sqlite.
Unpacking sqlite (from .../sqlite_2.8.17-7fakesync1build1_amd64.deb) ...
Processing triggers for man-db ...
Setting up courier-pop (0.66.1-1ubuntu4) ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "start" failed.
dpkg: error processing courier-pop (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of courier-pop-ssl:
 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing courier-pop-ssl (--configure):
 dependency problems - leaving unconfigured
Setting up courier-imap (4.9.1-1ubuntu4) ...
 * Courier IMAP server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error processing courier-imap (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-imap-ssl:
 courier-imap-ssl depends on courier-imap (>= 1.3.7-3); however:
  Package courier-imap is not configured yet.
dpkg: error processing courier-imap-ssl (--configure):
 dependency problems - leaving unconfigured
Setting up libsqlite0 (2.8.17-7fakesync1build1) ...
No apport report written because MaxReports is reached already
                                                              Setting up sqlite (2.8.17-7fakesync1build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 courier-pop
 courier-pop-ssl
 courier-imap
 courier-imap-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ian-weisser on 2013-09-07
> **ali6 said:**
> ```

[COLOR=#ff0000]4 not fully installed or removed.[/COLOR]

```

That's the important error message. Sometime in the recent past, you tried to install something (the courier-pop package). Install failed.

> **ali6 said:**
> ```

Setting up courier-pop (0.66.1-1ubuntu4) ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "start" failed.
dpkg: error processing **courier-pop** (--configure):
 subprocess installed post-installation script returned error exit status 1

[...]

 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing **courier-pop-ssl** (--configure):
 dependency problems - leaving unconfigured

[....]

Setting up courier-imap (4.9.1-1ubuntu4) ...
 * Courier IMAP server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error processing **courier-imap** (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-imap-ssl:
 
[...]

courier-imap-ssl depends on courier-imap (>= 1.3.7-3); however:
  Package courier-imap is not configured yet.
dpkg: error processing **courier-imap-ssl** (--configure):
 dependency problems - leaving unconfigured 
```

Those are your four packages clogging the system:
courier-pop
courier-imap
courier-pop-ssl
courier-imap-ssl

Would you like instructions on how to remove those packages?
Or would you like help on trying to fix them?

---

### Post by ali6 on 2013-09-07
> **ian-weisser said:**
> That's the important error message. Sometime in the recent past, you tried to install something (the courier-pop package). Install failed.

Until you successfully install or remove courier-pop, your package manager will steadfastly refuse to do anything, including install packages, remove packages, upgrade packages, or handle security updates.



Those are your four packages clogging the system:
courier-pop
courier-imap
courier-pop-ssl
courier-imap-ssl

Would you like instructions on how to remove those packages?
Or would you like help on trying to fix them?
to remove it

---

### Post by matt_symes on 2013-09-07
Hi

Try this

```
sudo apt-get install --reinstall courier-{pop,imap,pop-ssl,imap-ssl}
```

It will not remove it but reinstall it. (I assume this is what you want).

Kind regards

---

### Post by 3rdalbum on 2013-09-07
Each line is a separate suggestion. Try installing or removing a package after each line and see if it has worked; if it has, then stop following this post.

```
sudo apt-get remove courier-pop courier-imap
```

```
sudo dpkg --purge courier-pop courier-imap
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by 3rdalbum on 2013-09-07
> **ian-weisser said:**
> Until you successfully install or remove courier-pop, your package manager will steadfastly refuse to do anything, including install packages, remove packages, upgrade packages, or handle security updates.

Not actually true; those unconfigured packages will raise error messages, but will not stop other packages from being installed or removed (unless they depend on the courier-pop and courier-imap packages).

Look at the quoted terminal output more closely - you'll see that the user was trying to install sqlite, and they did successfully despite the courier-pop and courier-imap errors.

---

### Post by ian-weisser on 2013-09-07
> **3rdalbum said:**
> Not actually true; those unconfigured packages will raise error messages, but will not stop other packages from being installed or removed (unless they depend on the courier-pop and courier-imap packages).

Look at the quoted terminal output more closely - you'll see that the user was trying to install sqlite, and they did successfully despite the courier-pop and courier-imap errors.

Quite correct. Thanks for pointing that out.
I have edited my previous post.

---

### Post by ali6 on 2013-09-07
Hi, saddly both[**[COLOR=#000000] 3rdalbum[/COLOR]**]("http://ubuntuforums.org/member.php?u=61044") and [**[COLOR=#C61919][B]matt_symes**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1067998") methods didn't work

```

-------------

root@vps:~# sudo apt-get install --reinstall courier-{pop,imap,pop-ssl,imap-ssl}
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up courier-pop (0.66.1-1ubuntu4) ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "start" failed.
dpkg: error processing courier-pop (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-pop-ssl:
 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing courier-pop-ssl (--configure):
 dependency problems - leaving unconfigured
Setting up courier-imap (4.9.1-1ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                           * Courier IMAP server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error processing courier-imap (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-imap-ssl:
 courier-imap-ssl depends on courier-imap (>= 1.3.7-3); however:
  Package courier-imap is not configured yet.
dpkg: error processing courier-imap-ssl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 courier-pop
 courier-pop-ssl
 courier-imap
 courier-imap-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------
root@vps:~# sudo apt-get remove courier-pop courier-imap
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  courier-imap courier-imap-ssl courier-pop courier-pop-ssl
0 upgraded, 0 newly installed, 4 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 1102 kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 64581 files and directories currently installed.)
Removing courier-imap-ssl ...
 * Courier IMAP-SSL server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap-ssl, action "stop" failed.
dpkg: error processing courier-imap-ssl (--remove):
 subprocess installed pre-removal script returned error exit status 1
 * Courier IMAP-SSL server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap-ssl, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing courier-imap ...
 * Courier IMAP server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap, action "stop" failed.
dpkg: error processing courier-imap (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing courier-pop-ssl ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop-ssl, action "stop" failed.
dpkg: error processing courier-pop-ssl (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing courier-pop ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "stop" failed.
dpkg: error processing courier-pop (--remove):
 subprocess installed pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 courier-imap-ssl
 courier-imap
 courier-pop-ssl
 courier-pop
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------
root@vps-1140746-17891:~# sudo dpkg --purge courier-pop courier-imap
(Reading database ... 64581 files and directories currently installed.)
Removing courier-pop ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "stop" failed.
dpkg: error processing courier-pop (--purge):
 subprocess installed pre-removal script returned error exit status 1
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing courier-imap ...
 * Courier IMAP server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap, action "stop" failed.
dpkg: error processing courier-imap (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 courier-pop
 courier-imap
---------


root@vps:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up courier-pop (0.66.1-1ubuntu4) ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "start" failed.
dpkg: error processing courier-pop (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-pop-ssl:
 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing courier-pop-ssl (--configure):
 dependency problems - leaving unconfigured
Setting up courier-imap (4.9.1-1ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                           * Courier IMAP server: ERROR - imapd configuration file missing
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error processing courier-imap (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-imap-ssl:
 courier-imap-ssl depends on courier-imap (>= 1.3.7-3); however:
  Package courier-imap is not configured yet.
dpkg: error processing courier-imap-ssl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 courier-pop
 courier-pop-ssl
 courier-imap
 courier-imap-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

----------

---

### Post by matt_symes on 2013-09-08
Hi

Apt really wants those systemV scripts.

I want to take a look at you system first, so please post the output of these commands (copy and paste them into the terminal)

```
uname -a
```

```
cat /etc/lsb-release
```

```
ls -l /etc/init.d/courier*
```

That is a small L after ls.

```
cat /etc/init.d/courier*
```

```
initctl --version
```

To get around this problem (apt failing), it is usually possible to create the SystemV files manually and just return a valid value from the file. 

This can fool apt and should fix the apt issue but does not explain what is happening with the scripts. Hopefully the above commands will shed some light on that.

Anyway, after posting the output of the commands above..

Copy and paste (and please do copy and paste to eliminate errors) this into the terminal.

```
sudo bash -c 'for f in pop "pop-ssl" imap "imap-ssl" ;do echo "exit 0;" | tee "/etc/init.d/courier-${f}"; chmod 755 "/etc/init.d/courier-${f}"; done;'
```

Then i would personally try to purge the packages at this point, as per 3rdalbums instructions, and see if they are purged correctly. I would use a slightly modified command though.

```
sudo apt-get purge courier-{pop,imap,pop-ssl,imap-ssl}
```

This should, and i say "should" reservedly as always, fix the problem with apt and purge the packages (assuming there are no more issues with the packages).

I would purge at this point as opposed to reinstalling to make sure the problem is not with upstart as, if you reinstall, you may get the same issue you are currently facing (a long shot but worth guarding against at this point).

Then after we take a look at the output of the commands you post (from the first part of this post), we can make a decision about the best way forward.

Kind regards

---

