---
title: "Setting up accounts / permissions for backup device"
date: 2007-01-26
forum: General Help
---

### Post by AndyC_772 on 2007-01-26
My NAS drive is capable of automatically backing up remote devices over NFS, rsync or Samba on a regular schedule. I'd like to use it to back up the contents of my two PCs' hard drives without user intervention.

Since I have more than one user account on each PC, ideally I'd like the backup device to have read access to all users' files. Is it possible to set up an account with this level of access, so the NAS drive can log in and copy (for example) the entire /home directory in one go?

---

### Post by matthewstory on 2007-01-26
Set up an account with the same name an UID (for this you'll have to edit the /etc/passwd and /etc/group files, the number after the user/gropu name is the one you want to match accross all PCs) and then NFS will be able to access on all machines.

---

### Post by AndyC_772 on 2007-01-26
OK, that gives me an account which is valid on all machines - but is is possible to grant that account read access to files owned by other users?

(I guess I could always just let the NAS drive log in as root - but that seems like a bad idea for reasons I can't quite put my finger on...)

---

### Post by matthewstory on 2007-01-26
yeah, probably not a good idea.  What you could do is set a sane Umask, something like 022, so that all files aside from security sensitive ones are readable by your user.  you could also do some tweaking with a group maybe, add a group, and add that user to the group, and make that group the default group on all new files . . . this would most likely give more permissions than necissary to that user though.  The other option would be to tweak the /etc/sudoers file, and to give that user sudo priveleges to use cat, with the NOPASSWD option so that you could do it without interference . . . that would let him read any file.  Just some ideas . . .the implementation of this stuff is all a bit nasty though.  Hit me back if you like any of those ideas and need more help implementing them.

---

### Post by AndyC_772 on 2007-01-26
Thanks for the suggestions.

I suspect it'll be easiest to set default group permissions to be read only, and change the group ownership of everything I want to back up to be the same group as my 'backup operator' account.

I'm surprised that there isn't a trivial answer to this problem, though. I only have a fairly simple home setup; there must be much bigger deployments out there with dozens of users, sharing files amongst each other in various ways, and needing a 'catch-all' backup strategy that individual users don't need to worry about. Or am I assuming too much?

---

### Post by matthewstory on 2007-01-26
alot of datacenters do offer the kind of thing you're talking about, and they do a wholesale type backup of the entire drive to a tape drive or SAN via SFTP, but this usually involves a proprietary solution using an administrative user with backdoor access for the datacenter.  Generally what we do . . . and by that I mean what I do for backups with my company . . . is i do a seperate backup rig for each important area of a server, where critical information is stored.  For example, each of the home directories of my devlopers is backed up via SSH nightly, but this is done through a script run as their user, or the subversion repository is backed up 2xs daily, done by the svnadmin user . . . same for the database  . . . as mysql user, the webserver . .. as www-data and on and on and on.  Another thing you could consider is writing a backup script that's run as root, and initialized by rc.d on system startup, or a daily/hourly backup script executed as root by the cron-tab  .. . this would be more secure, and allow you to backup absolutely anything that your heart desired.

---

