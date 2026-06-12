---
title: "Unexpected Change in permissions/group of /dev/fuse???"
date: 2013-02-19
forum: General Help
---

### Post by liquidonline on 2013-02-19
Hi all,

Has there been a recent change to fuse in 12.10?  I'm a huge Tomboy user with ssh sync, and I noticed that my desktop notes weren't in sync anymore.  Upon a manual sync, I got a failure due to permissions.  Since it had been failing silently on auto-sync's, I have no idea when this really stopped working, except to say "probably" in the last 4-8 weeks.

On my affected desktop, running Kubuntu 12.10 (with KDE backports PPA):
```
myself@loki:~$ sudo ls -ld /dev/fuse
crw------T 1 root root 10, 229 Feb 18 18:00 /dev/fuse
```

My fileserver, also using Tomboy/SSH sync:
```
myself@thor:~$ sudo ls -ld /dev/fuse
crw-rw-rwT 1 root fuse 10, 229 Feb 16 16:43 /dev/fuse
```

Having never had this problem, my first question is:

**How do I permanently change (back) the group membership/permissions of /dev/fuse such that I don't manually do this on each boot? ** My quick/dirty hack of putting a chmod/chown command in /etc/rc.local doesn't sit well with me.

Second question:

**Anyone know when/why this would have been changed? ** If this is intended, it seems like a bad idea to me to make this only usable by root.  This means you'd need to run any scripts relying on this for sshfs (like backups, or other such scripts where you care enough about security to move files through SSH/SCP) as root, which I'm not a big fan of doing unless I *HAVE* to.  

For the record, especially since Tomboy failed silently, I have no clue if this is even an intended change or not - if someone can say with certainty (read: with reasonable source) that /dev/fuse shouldn't be owned by root:root with owner-only privileges, on a proper/healthy Ubuntu/Kubuntu 12.10 system I'll accept that, and turn my attention towards a WTF?-check against my system

---

### Post by rnerwein on 2013-02-20
> **liquidonline said:**
> Hi all,

Has there been a recent change to fuse in 12.10?  I'm a huge Tomboy user with ssh sync, and I noticed that my desktop notes weren't in sync anymore.  Upon a manual sync, I got a failure due to permissions.  Since it had been failing silently on auto-sync's, I have no idea when this really stopped working, except to say "probably" in the last 4-8 weeks.

On my affected desktop, running Kubuntu 12.10 (with KDE backports PPA):
```
myself@loki:~$ sudo ls -ld /dev/fuse
crw------T 1 root root 10, 229 Feb 18 18:00 /dev/fuse
```My fileserver, also using Tomboy/SSH sync:
```
myself@thor:~$ sudo ls -ld /dev/fuse
crw-rw-rwT 1 root fuse 10, 229 Feb 16 16:43 /dev/fuse
```Having never had this problem, my first question is:

**How do I permanently change (back) the group membership/permissions of /dev/fuse such that I don't manually do this on each boot? ** My quick/dirty hack of putting a chmod/chown command in /etc/rc.local doesn't sit well with me.

Second question:

**Anyone know when/why this would have been changed? ** If this is intended, it seems like a bad idea to me to make this only usable by root.  This means you'd need to run any scripts relying on this for sshfs (like backups, or other such scripts where you care enough about security to move files through SSH/SCP) as root, which I'm not a big fan of doing unless I *HAVE* to.  

For the record, especially since Tomboy failed silently, I have no clue if this is even an intended change or not - if someone can say with certainty (read: with reasonable source) that /dev/fuse shouldn't be owned by root:root with owner-only privileges, on a proper/healthy Ubuntu/Kubuntu 12.10 system I'll accept that, and turn my attention towards a WTF?-check against my system
hi
i think you are an extensive "sudo" user. why ? you ain't need sudo for "ls".
have you tried (now you need sudo ! ): sudo chmod 1666 /dev/fuse ??
ciao

---

### Post by liquidonline on 2013-02-20
> **rnerwein said:**
> hi
i think you are an extensive "sudo" user. why ? you ain't need sudo for "ls".
have you tried (now you need sudo ! ): sudo chmod 1666 /dev/fuse ??
ciao

Uhm... I'll refrain from lowering myself to your sort of post... too much.

1. I wasn't sure I'd get output of /dev/fuse without sudo given the permission denied error.  Thanks for the tip though, very thoughtful.  Let me know how using sudo as a precaution breaks or fixes the issue though, k?

2. I know I can chmod it, hence my comment about adding it to /etc/rc.local, but thanks for trying.  I'm sure though that there's a better way to do this permanently.  Key word is permanent.

I invite you to answer my questions if you would like to help.

---

