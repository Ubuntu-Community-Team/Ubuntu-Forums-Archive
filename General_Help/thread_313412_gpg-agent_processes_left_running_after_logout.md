---
title: "gpg-agent processes left running after logout"
date: 2006-12-06
forum: General Help
---

### Post by meldroc on 2006-12-06
I'm currently running Kubuntu Edgy, and it seems to be running fine, except for this little glitch.  It's documented here...

[https://launchpad.net/distros/ubuntu/+source/gnupg2/+bug/30717](https://launchpad.net/distros/ubuntu/+source/gnupg2/+bug/30717)

Basically, I have the gnupg-agent package installed, which helps track passphrases used by GnuPG, and is necessary for using encryption features in KMail.  That all works.  The bug is that when I log out, I have gpg-agent processes still running afterwards, which I can see if I log in through the console and do a "ps aux | grep username".  Granted, these processes are easily killed, and they don't consume too many resources, but this is a process leak that bugs me.

Is there an easy way to fix this problem?  I could probably hack the scripts that are in /etc/X11/Xsession.d (61pgp-agent and 90gpg-agent seem to be the culprits that start these processes, but have no way to kill them on logout.)

---

### Post by ciscosurfer on 2006-12-06
You can modify your ~/.bash_logout file to kill these agents if you wish.

---

### Post by meldroc on 2006-12-06
Hmm...  That might work, but I was wondering if there was a fix that would work for all users.

Another thing that occurred to me - because there are two files in /etc/X11/XSession.d (61pgp-agent and 90gpg-agent) that invoke gpg-agent, that means that gpg-agent is invoked twice, which is yet another wrong behavior.  If I do my ps aux | grep username after I logout, there are two gpg-agent processes running.

These scripts need to be cleaned up - they invoke gpg-agent twice rather than once, and they don't terminate gpg-agent upon logout.  Maybe the line to start gpg-agent needs to be moved elsewhere.

---

### Post by meldroc on 2006-12-12
Replying to my own post - I don't seem to have a solution to this problem yet.  I'm thinking I'll have to come up with one of my own.  I can do some script hacking - I'm pretty familiar with shell scripting & such.  What I'm thinking is that gpg-agent's going to have to be started somewhere else.  Scripts in /etc/X11/XSession.d work except for one problem - there's no mechanism to kill things that are started in here upon logout.

The .bash_logout file's certainly an option, but I'm not sure how to make it global to all users.

Another option, for KDE users would be to put a file to start gpg-agent in the autostart folder (for an individual user, ~/.kde/Autostart/ or IIRC, /usr/share/autostart systemwide.)  I'm not sure how to do the same thing for GNOME users.

---

