---
title: "Profile-sync-daemon throws errors"
date: 2013-09-18
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-09-18
The Pkg Update Mgr. tried to download and install the package:

profile sync daemon

I looked at the Developer's ppa and installed it and this is what the terminal returned:

mark@Lexington:~$ sudo apt-get install profile-sync-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following packages will be upgraded:
  profile-sync-daemon
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.

Need to get 0 B/15.8 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Supported

Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-IN4DHz/@' in '/tmp/apt-btrfs-snapshot-mp-IN4DHz/@apt-snapshot-2013-09-18_08:10:17'

Setting up profile-sync-daemon (5.39-1) ...
/var/lib/dpkg/info/profile-sync-daemon.postinst: 27: /etc/psd.conf: chromium: not found
dpkg: error processing profile-sync-daemon (--configure):
 subprocess installed post-installation script returned error exit status 127

Errors were encountered while processing:
 profile-sync-daemon

E: Sub-process /usr/bin/dpkg returned an error code (1)

=============

PSD puts the browser's "profiles" into RAM, saving wear and tear on your hard disk drive.

psd.conf may not have found: chromium, per the above, but I am using it as the browser to send this message.

I have no idea where to start to fix this.

======== 5 days after this post ==============

While installing Adobe's Acrobat Reader via: sudo apt-get install acroread, the terminal returned:

Setting up profile-sync-daemon (5.40.1-1) ...
/var/lib/dpkg/info/profile-sync-daemon.postinst: 27: /etc/psd.conf: chromium: not found
dpkg: error processing profile-sync-daemon (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up acroread-bin (9.5.5-1precise1) ...
Setting up acroread (9.5.5-1precise1) ...
No LSB modules are available.
No LSB modules are available.
Errors were encountered while processing:
 profile-sync-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by graysky on 2013-10-06
Just got your PM.  Not sure if/how BTRFS factors into the equation.  Are you still on 12.04?
Here is my terminal output installing psd (from my PPA) on a fresh Install of 13.10:
```
% sudo apt-get install profile-sync-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  profile-sync-daemon
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 0 B/15.8 kB of archives.
After this operation, 84.0 kB of additional disk space will be used.
Selecting previously unselected package profile-sync-daemon.
(Reading database ... 99256 files and directories currently installed.)
Unpacking profile-sync-daemon (from .../profile-sync-daemon_5.40.1-1_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up profile-sync-daemon (5.40.1-1) ...
--------------------------------------------------------------------------
  Define which users will make use of the sync in /etc/psd.conf
  Read the manpage before use or see the wiki page
  https://wiki.archlinux.org/index.php/Profile-sync-daemon

  ALWAYS backup your profiles data before using utils like psd!
--------------------------------------------------------------------------
 Adding system startup for /etc/init.d/psd ...
   /etc/rc0.d/K20psd -> ../init.d/psd
   /etc/rc1.d/K20psd -> ../init.d/psd
   /etc/rc6.d/K20psd -> ../init.d/psd
   /etc/rc2.d/S20psd -> ../init.d/psd
   /etc/rc3.d/S20psd -> ../init.d/psd
   /etc/rc4.d/S20psd -> ../init.d/psd
   /etc/rc5.d/S20psd -> ../init.d/psd
Processing triggers for ureadahead ...

```

Try this on your machine:
```
$ sudo apt-get purge profile-sync-daemon
```

Once I defined my user in /etc/psd.conf I was able to start it and it works as expected.

Then verify you are not getting any errors in your apt-get output when managing other packages.  If true, try to reinstall it from the ppa:
```
$ sudo apt-get install profile-sync-daemon
```

---

### Post by Mark_in_Hollywood on 2013-10-07
I use Precise Pangolin ver. 12.04 LTS

Following your response, I purged profile-sync-daemon. I then double checked that psd.conf was not in /etc. It was not

on re-install of PSD, I removed the quotation marks from around the browsers= line (#41?). That caused me to uninstall and reinstall profile-sync-daemon again.

After the install, I put quotes around the "browsers=" line and re-booted.

Following your [Profile-sync-daemon]("https://wiki.archlinux.org/index.php/Profile-sync-daemon") wiki, in a terminal, I ran:

profile-sync-daemon parse

and the terminal returned:

mark@Lexington:~$ profile-sync-daemon parse
chromium, is not a supported browser.  Check config file for typos: /etc/psd.conf

So, rather than purging again and re-installing again, from the wiki I tried:

mark@Lexington:~$ systemctl stop psd.service psd-resync.service
systemctl: command not found
mark@Lexington:~$ sudo systemctl stop psd.service psd-resync.service
[sudo] password for mark: 
sudo: systemctl: command not found
mark@Lexington:~$ sudo apt-get install systemctl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package systemctl

So, as I cut and paste the commands from your wiki, I'm unable to make psd work on this computer. Any ideas?

---

### Post by graysky on 2013-10-07
> **Mark_in_Hollywood said:**
> ...on re-install of PSD, I removed the quotation marks from around the browsers= line (#41?). That caused me to uninstall and reinstall profile-sync-daemon again.

No idea why that would be...?

> **Mark_in_Hollywood said:**
> After the install, I put quotes around the "browsers=" line and re-booted.

You should however always quote variables but in your case you should not quote the variable name.  Your psd.conf should read:
```
BROWSERS="chromium"
```

Note all caps for the first part.  Once you edited the file, just run psd again in parse mode and it should show you your chromium dir just fine.  There should be no need to reboot either.  Just restart psd.  On Ubuntu, you can do it like this:

```
$ sudo /etc/init.d/psd restart
```

> **Mark_in_Hollywood said:**
> 
Following your [Profile-sync-daemon]("https://wiki.archlinux.org/index.php/Profile-sync-daemon") wiki

...

So, rather than purging again and re-installing again, from the wiki I tried:

mark@Lexington:~$ systemctl stop psd.service psd-resync.service
systemctl: command not found
mark@Lexington:~$ sudo systemctl stop psd.service psd-resync.service
[sudo] password for mark: 
sudo: systemctl: command not found
mark@Lexington:~$ sudo apt-get install systemctl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package systemctl

So, as I cut and paste the commands from your wiki, I'm unable to make psd work on this computer. Any ideas?

You are confused over the init system that Ubuntu is using.  I wrote psd to run on many different distros.  Some use systemd while others, like Ubuntu use upstart.  See the above for the syntax for interacting with services with upstart/Ubuntu.

---

