---
title: "How do I uninstall this program (jetty)"
date: 2014-02-07
forum: General Help
---

### Post by frogwarrior on 2014-02-07
I installed node.js, and it seems to have installed some web server called jetty, and this jetty program has been causing problems ever since, any time I use the package manager it gives me some kind of error about jetty. For example, I just ran aptitude upgrade, and heres what happened:

```
horse@box:~$ sudo aptitude safe-upgrade[sudo] password for horse: 
The following packages will be upgraded: 
  espeak-data libespeak1 
The following partially installed packages will be configured:
  jetty 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,142 kB of archives. After unpacking 1,024 B will be used.
Do you want to continue? [Y/n/?] y
Get: 1 http://ie.archive.ubuntu.com/ubuntu/ saucy-updates/main libespeak1 i386 1.47.11-1ubuntu0.1 [151 kB]
Get: 2 http://ie.archive.ubuntu.com/ubuntu/ saucy-updates/main espeak-data i386 1.47.11-1ubuntu0.1 [991 kB]
Fetched 1,142 kB in 10s (104 kB/s)                                              
(Reading database ... 315406 files and directories currently installed.)
Preparing to replace libespeak1:i386 1.47.11-1 (using .../libespeak1_1.47.11-1ubuntu0.1_i386.deb) ...
Unpacking replacement libespeak1:i386 ...
Preparing to replace espeak-data:i386 1.47.11-1 (using .../espeak-data_1.47.11-1ubuntu0.1_i386.deb) ...
Unpacking replacement espeak-data:i386 ...
Setting up jetty (6.1.26-1ubuntu1) ...
Adding system user `jetty' (UID 121) ...
Adding new user `jetty' (UID 121) with group `jetty' ...
useradd: existing lock file /etc/subgid.lock without a PID
useradd: cannot lock /etc/subgid; try again later.
adduser: `/usr/sbin/useradd -d /usr/share/jetty -g jetty -s /bin/false -u 121 jetty' returned error code 18. Exiting.
dpkg: error processing jetty (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up espeak-data:i386 (1.47.11-1ubuntu0.1) ...
Setting up libespeak1:i386 (1.47.11-1ubuntu0.1) ...
Processing triggers for libc-bin ...
Errors were encountered while processing:
 jetty
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         
Current status: 0 updates [-2].



```

it doesn't prevent me from installing software, but since I use apache2, I don't need another web server so I wanna get rid of this jetty thing, but if I try to uninstall it:

```
horse@box:~$ sudo apt-get purge jettyReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  jetty*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,042 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 315405 files and directories currently installed.)
Removing jetty ...
 * Stopping Jetty servlet engine (was reachable on http://box:8080/). jetty                                                                                     start-stop-daemon: user 'jetty' not found
start-stop-daemon: user 'jetty' not found
invoke-rc.d: initscript jetty, action "stop" failed.
dpkg: error processing jetty (--purge):
 subprocess installed pre-removal script returned error exit status 2
 * Starting Jetty servlet engine. jetty                                         start-stop-daemon: user 'jetty' not found
 * (already running).
                                                                         [ OK ]
Errors were encountered while processing:
 jetty
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I get the same error if I use apt-get remove. It keeps saying "user 'jetty' not found" but I tried creating that user and it tells me it the group jetty already exists. I don't know what else to try.

---

### Post by theDaveTheRave on 2014-02-07
first lets confirm that the jetty user really exists...

```

cat /etc/passwd |grep jetty

```

should return a single line, which will confirm that the user exists.
The end of the line should say
```

/bin/false

```

This is correct, as you don't want anyone logging in to your system with this user. The other directory tells you where jetty should be installed, this will likely be /usr/jetty or /opt/jetty or /var/jetty or something similar (it may say www as it is the web server).

Jetty is often used as an embeded web server, if you are already running apache, what ever you downloaded that has jetty bundled with it should be configurable without jetty.

I'm surprised that node.js has installed jetty as a requirement, as they are 'competing' technologies, the scare quotes are important here. Jetty would be bundled with an enterprise app that need a web server to function (many apps now run in a web browser, embeding jetty allows users to access the web based UI without the need to mess about installing a standalone web server).

A potential problem for you is that as you already have apache running, and hence listening on port 80, I'm not sure you can have jetty running alongside, also trying to listen to port 80. This may be why the jetty install is failing, as port 80 is already being used.

you'll need to find the configure script for jetty to modify it's listening port, then you will be able to install and remove it (i should hope)

Dave.

---

### Post by frogwarrior on 2014-05-11
Sorry for the late reply, the thread didn't show up in my control panel. This problem has been driving me insane, its interfering with everything so the help is much appreciated.

 Running 
cat /etc/passwd | grep jetty

returns nothing, a blank line so the user doesn't exist. Running **cat /etc/group | grep jetty** returns:
**jetty:x:134:**
so the group exists. Ah, that you think its because apache2 is already using port 80 that it is failing. I'll switch off the apache server temporarily, then see what happens.

BTW: I looked for these jetty directories, and heres what I found:
> 
$ **locate */jetty**
/etc/jetty
/etc/cron.daily/jetty
/etc/default/jetty
/etc/init.d/jetty
/usr/share/jetty
/usr/share/doc/jetty
/usr/share/maven-repo/org/mortbay/jetty
/usr/share/maven-repo/org/mortbay/jetty/jetty
/var/cache/jetty
/var/lib/jetty
/var/log/jetty


Heres what happened when I tried to stop the process:
> $ sudo /etc/init.d/jetty stop
 * Stopping Jetty servlet engine (was reachable on [http://box:8080/](http://box:8080/)). jetty                                                                                     
start-stop-daemon: user 'jetty' not found
start-stop-daemon: user 'jetty' not found


So its not actually listening on port 80. To access the node.js site, I had to go through port 8080. I suppose its cron.daily thats running the server in the first place, so I'm gonna take a look in there.

EDIT: Heres the jetty script in /etc/cron.daily:
```

  GNU nano 2.2.6                                         File: jetty                                                                                          

#!/bin/sh

NAME=jetty
DEFAULT=/etc/default/$NAME

# The following variables can be overwritten in $DEFAULT

# Default for number of days to keep old log files in /var/log/jetty/
LOGFILE_DAYS=14

# End of variables that can be overwritten in $DEFAULT

# overwrite settings from default file
if [ -f "$DEFAULT" ]; then
        . "$DEFAULT"
fi

if [ -d /var/log/$NAME ]; then
        find /var/log/$NAME/ -name \*.log -mtime +$LOGFILE_DAYS -print0 \
                | xargs --no-run-if-empty -0 rm --
fi


```

Looks like its only for logging. Suppose the next logical step is to see what the hell its been logging all this time. It seems /var/log/jetty is empty at this very moment. I checked all the autostart folders for a jetty launcher but there are none. There aren't any launchers in there for apache2 either, so I'm guessing the /etc/init.d folder serves that purpose for web servers. I don't know if that will even stop it from being launched. I can't even figure out how to kill the server. pgrep jetty returns nothing, **ps aux | grep jetty**, gives no indication that jetty is even running. When I pgrep apache2, a heap of processes come up. Is there some kind of script that jetty installed which gets activated whenever I use dpkg? I put "exit" at the top of the init.d script, rendering it useless, but that didn't solve the problem. How do I stop this unholy server? Is there a way I can see whats going on behind the scenes when I use dpkg, as in a way to see what jetty related script is being activated, and how its being triggered?

---

### Post by matt_symes on 2014-05-11
Hi

The lock file seems to be giving you problems and is not allowing configuration of jetty to complete.

Open a terminal and type

```
sudo mv /etc/subgid.lock{,.old}
```

```
sudo apt-get purge jetty
```

Then try to reinstall it, if you want to use it.

Post back any errors.

If the above procedure works correctly, cleanup with

```
sudo rm /etc/subgid.lock.old
```

Kind regards

---

### Post by frogwarrior on 2014-05-11
It worked! I really need to learn about these locks. I don't have any need for jetty so wont be installing it again. Heres what happened:

```

sudo apt-get purge jetty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  jetty*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 1,042 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 489538 files and directories currently installed.)
Removing jetty ...
Purging configuration files for jetty ...
/usr/sbin/deluser: The user `jetty' does not exist.
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```

The part about the database "(Reading database ... 489538 files and directories currently installed.)", I wonder what thats all about. I have a lot of MySQL databases, but never used this jetty server.  It didn't delete anything from my databases. Do you know what it means when it says ureadahead will be reprofiled on next reboot? 

Thanks a million for this though, that was a massive pain in the ass, I'll know now how to deal with this kinda problem in the future.

---

### Post by matt_symes on 2014-05-11
Hi

Certain files get locked when they are edited to stop more than one program/application/service reading/writing to them while they are being edited as this can leave the file being edited file in an inconsistent state, or the information being read from the file stale. 

One standard way to lock a file is to create a lock for for the file being edited. In your case the file being edited was /etc/subgid, and to lock it another file /etc/subgid.lock was created. However this lock file (/etc/subgid.lock) was not deleted after the file /etc/subgid had finished being edited. That may have been because what ever application was originally editing the file /etc/subgid crashed before it deleted the file /etc/subgid.lock that it had created.

Please don't delete files from your system (lock files or otherwise) unless you are pretty sure they will afford the fix :)

> 
The part about the database "(Reading database ... 489538 files and  directories currently installed.)", I wonder what thats all about. I  have a lot of MySQL databases, but never used this jetty server.  It  didn't delete anything from my databases. Do you know what it means when  it says ureadahead will be reprofiled on next reboot?

The database eluded to here is the dpkg package database. It is not related to any MySQL databases installed on your system but is instead, a flat file text database.

ureadahead is a service that attempts to profile your boot sequence to help boot your system quicker. It will be re-run for you the next time you reboot your system in an attempt to make subsequent boots faster.

Kind regards

---

### Post by frogwarrior on 2014-05-12
Cheers matt, that explains it. Now I get why I get problems with a lock when I force kill the terminal (or synaptic) while a program is in the middle of installation (i.e. when it crashes). That one fixes itself if I reboot the comp, but it'd be easier to just delete the lock. Is there a danger in deleting locks, other than two programs writing at the same time and messing up the file? I usually reinstall Ubuntu regularly just in case I get infected with malware, but don't have the time right now. Better off learning about the problem instead of reinstalling the OS every time I encounter a tricky one. Had a weird problem with the /var/lib/dpkg/status file recently, the error I was getting was:
```
[COLOR=#2B2B2B][FONT=Lato]dpkg: warning: parsing file ‘/var/lib/dpkg/status’ near line 25126 package ‘debconf-i18n’:[/FONT][/COLOR]
[COLOR=#2B2B2B][FONT=Lato]missing description
```[/FONT][/COLOR]
running apt-get install -f didn't solve it, so I edited the file manually and found out that the word description was spelled wrong for this package. If was spelled descripion. How the hell did that happen I wonder.

---

### Post by matt_symes on 2014-05-13
> **frogwarrior said:**
> Cheers matt, that explains it.

No problem :)

> Now I get why I get problems with a lock when I force kill the terminal (or synaptic) while a program is in the middle of installation (i.e. when it crashes). That one fixes itself if I reboot the comp, but it'd be easier to just delete the lock. Is there a danger in deleting locks, other than two programs writing at the same time and messing up the file? 

That is the main problem; concurrent processes (applications, services and such like) reading/writing to the same file at the same time. It's never good to get a context switch while one piece of software is updating a file (or data structure - the same principle applies in multi-threaded applications) to another piece of software that wants to read or update the same file (or data structure) without some kind of locking mechanism.

I will point out that, as a general rule, try not to use

```
kill **-9** <program_pid>
```
```

matthew-S206:/home/matthew:0 % kill -l 9
KILL
matthew-S206:/home/matthew:0 %
```

or 

```
kill -SIGKILL <program_pid>
```

-9 is a KILL request and can leave all kinds of files (such as lock files) and other junk on your system. It does not give the program any attempt to shut down gracefully and close any open files etc.

Only use SIGKILL if the hanging process does not respond to any gentler methods to close it such as SIGTERM.

> I usually reinstall Ubuntu regularly just in case I get infected with malware, but don't have the time right now.

Malware is less of an issue (although it's not non existent) on Linux currently. As for browsing habits, look to install extensions such as noscript and the like and be choosy about links clicked and sites visited :) There is a good write-up about security in the security sub forum.

> Better off learning about the problem instead of reinstalling the OS every time I encounter a tricky one. Had a weird problem with the /var/lib/dpkg/status file recently, the error I was getting was:
```
[COLOR=#2B2B2B][FONT=Lato]dpkg: warning: parsing file &#8216;/var/lib/dpkg/status&#8217; near line 25126 package &#8216;debconf-i18n&#8217;:[/FONT][/COLOR]
[COLOR=#2B2B2B][FONT=Lato]missing description[/FONT][/COLOR]
```
running apt-get install -f didn't solve it, so I edited the file manually and found out that the word description was spelled wrong for this package. If was spelled descripion. How the hell did that happen I wonder.

Maybe a bug in the deb file ? 

I hope that helps.

Kind regards

---

