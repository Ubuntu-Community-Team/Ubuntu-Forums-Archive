---
title: "can't run gedit/nautilus as root"
date: 2008-05-30
forum: General Help
---

### Post by metrorat on 2008-05-30
Hi all...

Have been trying to fix a gnome-settings-daemon bug which was once bearable but got really bad after the latest round of hardy updates.

See [http://ubuntuforums.org/showthread.php?t=812770]("http://ubuntuforums.org/showthread.php?t=812770")

Now I have a major problem.  Have discovered I can't run nautilus or gedit from a shell with sudo nor from a root shell.

After the last set of updates I also found a info popup window would appear at boot asking me to set my default soundcard. I ran:

```
asoundconf set-default-card Intel
```

The next time i booted it appeared I ran the above code again but because I'm a muppet I ran it as root(! I know !).  I got a warning that this may have unexpected consequences. The info message has not appeared again but I'm experiencing a raft of other issues and I'm not sure whether they are as a result of that or whether they are connected to the gnome-settings-daemon error as described in the above post.

Issues are:
Boot & login both v slow
Default gnome icons appear instead of custom icons in both desktop and apps.
Dodgy boot messages (attached)
sudo gedit/nautilus not working
Gnome-settings-daemon error on *every* boot & login

Would appreciate it if anyone could help me sort any of this out...

Feel like my hands are tied as I can't use gedit as root.

Cheers

---

### Post by fragos on 2008-05-30
The 1st user created is placed in sudoers and the admin group. Other added users aren't. There is a special program for editing sudoers. That is what I'd check first. Not being the 1st user or removing yourself from the admin group are posibles. Hve you edited your /etc/hosts file? The name in /etc/hostname need to be there as in:

127.0.0.1	localhost
127.0.1.1	{your hostname}

---

### Post by metrorat on 2008-06-01
Hi.  /etc/hosts looks fine. There is only 1 user on my system 'metroat' plus root. I have attached a couple of screenshots of each one's user privileges.
I have also attached a summary of the users-admin > manage groups settings.  If you could take a look and tell me if looks obviously wrong I would greatly appreciate it. I've included all listed groups although I'm sure most of them are irrelevant but I'm not sure which ones.

Oddly though I can successfully run sudo synaptic and metrorat is listed as a member of the admin group - does his then mean that the issue is something else?

Thanks for your help

---

### Post by metrorat on 2008-06-01
Update... I'm thinking that this may all be a result of the gnome-settings-daemon error that I get every time I log in.  Its seem that sudo gedit does work it just takes a VERY long time to come up with the window.  I tried the workaround given at [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15]("http://ubuntuforums.org/showpost.php?p=3776732&postcount=15") using nano but to no avail (I have now undone changes).  It still takes ages to log in, sudo'd apps take forever to start.  No custom icons on the desktop or in apps work until about 10-15mins into the session (everything is gnome defaults no matter which theme is selected).

This really sucks and is driving me nuts!  Sorry if I had you barking up the wrong tree there but any further help would be great.

Thanks

---

### Post by fragos on 2008-06-01
Your group settings are fine. If the group settings was a problem, sudo wouldn't work at all. My desktop and laptop are both running Ubuntu 8.04 and I've not experienced anything like this. When fsck runs every 30 boots or so it does take longer for the system to come up but that is just during the disk check. If for example you try to mount an NFS connection to another PC it can have problems if the IP is wrong. If I were you, I'd save my data and do a reinstall. If you updated instead of a clean install in the 1st place that might be the source of your problem. The more CLI tweaking, compiling and out of repositoty installs you do; the greater the chance that a distrobution upgrade will have problems.

---

### Post by metrorat on 2008-06-03
Hi Fragos - thanks for your advice.  It seems all this has had to do with the persistent gsd error - being cause by etc/network/interface and (you were right) /etc/hosts settings carried over from a previous version. In etc/hosts I had Linux.linksys.net instead of simply Linux and there was no entry for my wireless adaptor in etc/network/interface, although very oddly it has been working (except the configure button in wireless monitor says 'Device does not exist').  With these two things sorted the gsd error has disappeared and apps and icons work as they should.

Bitchin.

---

