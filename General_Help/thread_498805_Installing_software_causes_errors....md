---
title: "Installing software causes errors..."
date: 2007-07-11
forum: General Help
---

### Post by Kono on 2007-07-11
Hi there!

Updating and installing new packets worked just fine. Till yesterday. Every time I add a new package via Applications -> Add/Remove..., the installation works fine (and the programs actually seem to work), but at the end there always show up these errors:

"An error occurred.

The following details are provided:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured"

There was also a detailed log of the terminal, stating which error occurred, but I could not paste it into this window.

I have Ubuntu for about 2 weeks now and this is my first try at Linux, so please explain anything in newbie terms ;).

Thanks in advance for any help,
Kono.

---

### Post by NickD-NLUG on 2007-07-12
I realise there's a lot of detail, but does this help?

[https://answers.launchpad.net/ubuntu/+question/3586](https://answers.launchpad.net/ubuntu/+question/3586)

It's always a good idea to google for any error messages you get in relation to a problem.

And welcome to Linux :)

---

### Post by Kono on 2007-07-15
> **NickD-NLUG said:**
> I realise there's a lot of detail, but does this help?

[https://answers.launchpad.net/ubuntu/+question/3586](https://answers.launchpad.net/ubuntu/+question/3586)

It's always a good idea to google for any error messages you get in relation to a problem.

And welcome to Linux :)

Thank you for your response.

But it didn't help, I've gone thru everything the link you gave me said, but the problem still remains. Can someone tell me what may be wrong?

Here is an excerpt from the terminal (in chronological order of what I did):

> 
lxusr@computer-name:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured


> 
lxusr@computer-name:~$ sudo dpkg --remove --force-all cman
dpkg: cman: dependency problems, but removing anyway as you request:
 rgmanager depends on cman (= 2.20070315-0ubuntu2.1).
(Reading database ... 121560 files and directories currently installed.)
Removing cman ...



> lxusr@computer-name:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of clvm:
 clvm depends on cman; however:
  Package cman is not installed.
dpkg: error processing clvm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on cman; however:
  Package cman is not installed.
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster


Thanks in advance.

---

### Post by Kono on 2007-07-19
No one has an idea? :(

---

### Post by Kono on 2007-07-20
I'd rather like to avoid having to reformat my entire harddisc. Isn't there an easier solution? Or at least a hint what could cause the problem?

---

### Post by NickD-NLUG on 2007-07-21
Sorry, I don't know what it causing the problem, but reformatting the hard disk and starting from scratch isn't going to solve the problem.  Well... it might, but if it does you won't know what the problem was and won't learn anything by fixing it.  Stick with this one.... 

Especially as this problem doesn't appear to be stopping software installing or functioning, it's just a bit of an aberration.  So just keep poking away at it, and sooner or later the problem will go away :)

---

### Post by jocko on 2007-07-21
Have you tried to completely uninstall all the packages it complains about?
You can always try to reinstall them later if you need them...
Try this:
```
sudo aptitude purge cman clvm redhat-cluster-suite system-config-cluster
```

---

### Post by Kono on 2007-07-21
> Well... it might, but if it does you won't know what the problem was and won't learn anything by fixing it. Stick with this one....

You are so right. I don't like giving up on things and you only learn by these problems :)

> **jocko said:**
> Have you tried to completely uninstall all the packages it complains about?
You can always try to reinstall them later if you need them...
Try this:
```
sudo aptitude purge cman clvm redhat-cluster-suite system-config-cluster
```

I tried that, but the problem of removing cman remained, EVEN when forcing the removal.

But I solved the problem after google-ing again. Here's what I did:

I changed the file /var/lib/dpkg/info/clvm.prerm from:
```
#!/bin/sh
set -e
# Automatically added by dh_installinit
if [ -x "/etc/init.d/clvm" ] && [ "$1" = remove ]; then
if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
invoke-rc.d clvm stop || exit $?
else
/etc/init.d/clvm stop || exit $?
fi
fi
# End automatically added section
```

to

```
#!/bin/sh
set -e
exit 0
# Automatically added by dh_installinit
if [ -x "/etc/init.d/clvm" ] && [ "$1" = remove ]; then
if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
invoke-rc.d clvm stop || exit $?
else
/etc/init.d/clvm stop || exit $?
fi
fi
# End automatically added section
```

(I added the "exit 0" right at the beginning). I don't know why this did the trick, I guess, because the script didn't return an error code anymore and therefore the removal process continued.

Can someone explain to me, what all this was exactly about?

---

### Post by zenmester on 2007-07-22
I don't know. But it is the only thing that have worked so far so i am happy:)

---

### Post by Directrix1 on 2007-07-25
The following worked for me:
```
sudo rm /etc/init.d/clvm
sudo apt-get remove clvm
```

---

### Post by cabraswel2 on 2007-07-26
[http://ubuntuforums.org/showthread.php?t=401707&highlight=clvm](http://ubuntuforums.org/showthread.php?t=401707&highlight=clvm)

---

