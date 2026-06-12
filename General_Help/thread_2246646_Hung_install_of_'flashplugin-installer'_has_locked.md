---
title: "Hung install of 'flashplugin-installer' has locked further updates of system"
date: 2014-10-02
forum: General Help
---

### Post by comcirebel on 2014-10-02
Hung install of 'flashplugin-installer' has locked further updates of system. I've tried to find and kill the updater service, but am not seeing it running.   

[SIZE=1]Your Ubuntu release is not supported anymore.[/SIZE]
[SIZE=1]For upgrade information, please visit:[/SIZE]
[SIZE=1]http://www.ubuntu.com/releaseendoflife[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]New release '13.10' available.[/SIZE]
[SIZE=1]Run 'do-release-upgrade' to upgrade to it.[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]Last login: Wed Oct  1 21:49:45 2014 from 192.168.1.179[/SIZE]
[SIZE=1]comicrebel@andromeda1:~$ sudo aptitude install do-release-upgrade[/SIZE]
[SIZE=1][sudo] password for comicrebel:[/SIZE]
[SIZE=1]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)[/SIZE]
[SIZE=1]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/SIZE]
[SIZE=1]W: Could not lock the cache file; this usually means that dpkg or another apt tool is already installing packages.  Opening in read-only mode; any changes you make to the states of packages will NOT be preserved![/SIZE]
[SIZE=1]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)[/SIZE]
[SIZE=1]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/SIZE]
[SIZE=1]comicrebel@andromeda1:~$

[SIZE=2]Any help is welcome[/SIZE][/SIZE]

---

### Post by Impavidus on 2014-10-02
1: Killing the package manager whilst installing flashplugin-installer terminated the package manager without a chance to remove its lock. If you're sure you don't have another package manager running, you can remove the lock manually.

2: I see you tried to upgrade to 13.10, which suggests you're running 13.04. Both of them are unsupported, meaning they don't get upgrades and you need some hacks to access the archived repositories. Best thing to do is a clean install of 14.04.

---

### Post by comcirebel on 2014-10-02
Thanks for the info. How do I manually remove the lock? Regarding a clean install, I'd prefer not to do this, but if I do, where can I dl an iso copy of 14.04? Thanks, Tim

---

### Post by slickymaster on 2014-10-02
> **comcirebel said:**
> Thanks for the info. How do I manually remove the lock? Regarding a clean install, I'd prefer not to do this, but if I do, where can I dl an iso copy of 14.04? Thanks, Tim

You can delete the lock file with the following command:```
sudo rm /var/lib/apt/lists/lock
```You may also need to delete the lock file in the cache directory```
sudo rm /var/cache/apt/archives/lock
```

You can donwload 14.04 images from:
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)
[http://lubuntu.net/tags/download](http://lubuntu.net/tags/download)
[http://ubuntugnome.org/download/](http://ubuntugnome.org/download/)

---

### Post by grahammechanical on 2014-10-02
Have you tried logging out and logging back in? Or even a reboot?

The reason for the installation of the flash plugin to fail is due to 13.04 being End of Life. The same reason will prevent an upgrade to 13.10 from succeeding. If you do manage to upgrade to 13.10 you will continue to have updating problems until you get to 14.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards.

---

### Post by comcirebel on 2014-10-02
After running the above commands for manually removing the lock file, I am still getting this message: 

[SIZE=1]root@andromeda1:~# aptitude install samba
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
W: Could not lock the cache file; this usually means that dpkg or another apt tool is already installing packages.  Opening in read-only mode; any changes you make to the states of packages will NOT be preserved!
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[SIZE=2]AND[/SIZE]

root@andromeda1:~# dpkg --configure -a
dpkg: error: dpkg status database is locked by another process
root@andromeda1:~# E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
root@andromeda1:~# E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/SIZE]

I am not able to get past this lock condition.

---

### Post by slickymaster on 2014-10-02
> **grahammechanical said:**
> Have you tried logging out and logging back in? Or even a reboot?<...snip...>

This ^^
Since manually removing the lock didn't accomplished it, please reboot your system and try again.

---

### Post by comcirebel on 2014-10-02
OK, thanks. Yes, I've rebooted. Can I back out of the flashplugin-install operation? As I've said, I tried killing the pid, but that didn't work. 

Also, what is the process for a new install of 14.04? Will I have to completely build up the machine from scratch, and configure my drives, directory structure and mount points?

---

### Post by comcirebel on 2014-10-02
Below is the message I'm seeing when I try to install anything. I realize that the version I am using is no longer supported, but how do I get rid of the locked process *flashplugin-installer*? I have tried all of the above.

[COLOR=#008000]root@andromeda1:~# aptitude install samba[/COLOR]
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
W: Could not lock the cache file; this usually means that dpkg or another apt tool is already installing packages.  Opening in read-only mode; any changes you make to the states of packages will NOT be preserved!
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
[COLOR=#008000]root@andromeda1:~# dpkg --configure -a[/COLOR]
Setting up update-notifier-common (0.134) ...
[COLOR=#ff0000]flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.335.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.335.orig.tar.gz)[/COLOR]

The flashinstaller-installer process has hijacked my system!

---

### Post by Impavidus on 2014-10-02
What do you get from```
lsof /var/lib/dpkg/lock
ls -l /var/lib/dpkg
```(run them as root, but I see you already have a root shell)

If you install 14.04 you don't have to start from scratch. You can reuse your existing partitions. You can backup a list of installed packages and reinstall all of them with two simple commands (for as far as they are still available). You can backup your settings, but some care should be taken there. Most of the work is configuring new features and things like that.

Edit: flashplugin-installer was not configured yet because of the failed installation. Running **dpkg --configure -a** configures it again. It should however succeed in downloading the flash player, as that location is not specific to 13.04.

Edit2: Or maybe not. The directory is still valid, but the file name is old. Just checking... Yep, link is valid, but it's an old release of flash.

---

### Post by comcirebel on 2014-10-02
Output...

root@andromeda1:~#
root@andromeda1:~# **[COLOR=#ff0000]lsof var/lib/dpkg/lock[/COLOR]**
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/comicrebel/gvf                                      s
      Output information may be incomplete.
lsof: status error on var/lib/dpkg/lock: No such file or directory
lsof 4.86
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhKlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]] [+|-e s]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
root@andromeda1:~# **[COLOR=#ff0000]ls -l /var/lib/dpkg[/COLOR]**
total 6684
drwxr-xr-x 2 root root    4096 Apr  6 21:49 alternatives
-rw-r--r-- 1 root root      11 Mar 30  2014 arch
-rw-r--r-- 1 root root 1561006 Apr  6 21:48 available
-rw-r--r-- 1 root root 1558745 Apr  6 21:47 available-old
-rw-r--r-- 1 root root       8 Apr 23  2013 cmethopt
-rw-r--r-- 1 root root    1120 Mar 30  2014 diversions
-rw-r--r-- 1 root root     998 Mar 30  2014 diversions-old
drwxr-xr-x 2 root root  331776 Apr  8 19:56 info
-rw-r----- 1 root root       0 Oct  2 11:15 lock
drwxr-xr-x 2 root root    4096 Mar 22  2013 parts
-rw-r--r-- 1 root root     135 Mar 30  2014 statoverride
-rw-r--r-- 1 root root     105 Mar 30  2014 statoverride-old
-rw-r--r-- 1 root root 1670384 Oct  2 11:15 status
-rw-r--r-- 1 root root 1670384 Oct  1 19:53 status-old
drwxr-xr-x 2 root root    4096 Apr  6 21:49 triggers
drwxr-xr-x 2 root root    4096 Oct  2 11:15 updates
root@andromeda1:~#

---

### Post by comcirebel on 2014-10-02
[SIZE=1][SIZE=2]Thank you Impavidus![/SIZE]

RE: *Edit: flashplugin-installer was not configured yet because of the failed installation. Running **dpkg --configure -a** configures it again. It should however succeed in downloading the flash player, as that location is not specific to 13.04.*[/SIZE]
-For some reason, I never got this install to complete, after a few attempts. I decided not to install it, since it was problematic anyway.

[SIZE=1]RE: *If you install 14.04 you don't have to start from scratch. You can reuse  your existing partitions. You can backup a list of installed packages  and reinstall all of them with two simple commands (for as far as they  are still available). You can backup your settings, but some care should  be taken there. Most of the work is configuring new features and things  like that.*[/SIZE]
1. How do I run a list of installed packages?
2. How to reinstall all of them with two simple commands?
3. How to backup my settings?

Clearly I'm a newcomer to ubuntu, but hey, I'm learning, thanks to lots of good information found here and other places!

Thanks

---

### Post by Impavidus on 2014-10-03
1: Use```
dpkg --get-selections > package.txt
```to create the file package.txt, containing a list of installed packages. Copy this file to an external drive, so that you don't lose it.
2: On your new install, go the the directory with your package.txt file and run these two commands:```
sudo dpkg --set-selections < package.txt
sudo apt-get dselect-upgrade
```This will install all packages from your previous install, except those no longer available.
3: For those in your home directory, just backup your entire home directory. You may wish to remove some caches and thumbnails first. If you have a separate /home partition this is even easier, as can just keep it. Keeping /home also seems to be possible without a separate /home partition, but I've never seen this. For your system wide settings, like network settings, it may be safer if you reconfigure them after installing. It shouldn't be too much. They are all stored somewhere, mostly in /etc, but it's difficult to find out which can be backed up and restored and which cannot. Most cannot I think.

---

### Post by comcirebel on 2014-10-03
Hi Again,
Thank you for the info, once again. I'll do this next chance I get. I'll need to burn an iso of 14.04. I do have a separate home partition, so that will remain in tact with the reload. Thanks for being out there! I am learning how to use ubuntu, and messing with nginx web server, etc. I want to set up a networked file server, and will probably load samba, and see how that works, to play with my ubuntu and windows workstations.

This is in my home office network, so it doesn't have exposure to the mean, outside world.

Thank for everything!

Tim

---

