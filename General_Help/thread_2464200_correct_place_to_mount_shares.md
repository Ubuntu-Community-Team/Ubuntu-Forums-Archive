---
title: "correct place to mount shares?"
date: 2021-06-26
forum: General Help
---

### Post by jfaberna on 2021-06-26
I've been using Linux/Unix since the 1980's. Traditionally I always setup fstab to mount network shares on /mnt/. This made it different from the automatic or temporary mounts for USB CD/DVD and Flash drives which got mounted to /media/jim/.

Lately, on some forums when I have a question about an application, or networking issue with samba/cifs, etc. I always get fussed at about using /mnt as a mount point.

Is there some real valid reason that cifs share mounts should not be on /mnt???

---

### Post by CatKiller on 2021-06-26
> **jfaberna said:**
> Is there some real valid reason that cifs share mounts should not be on /mnt?
No. It's your computer; mount things wherever makes most sense to you. /mnt/cifs/ (or similar) would be better than just /mnt/, in case you want to mount something else at the same time.

---

### Post by jfaberna on 2021-06-26
> **CatKiller said:**
> No. It's your computer; mount things wherever makes most sense to you. /mnt/cifs/ (or similar) would be better than just /mnt/, in case you want to mount something else at the same time.
Thanks, I have 2 cifs shares and I really mount them at /mnt/anonymous and /mnt/public so it sort of follows your suggestion.

---

### Post by TheFu on 2021-06-27
> **jfaberna said:**
> I've been using Linux/Unix since the 1980's. Traditionally I always setup fstab to mount network shares on /mnt/. This made it different from the automatic or temporary mounts for USB CD/DVD and Flash drives which got mounted to /media/jim/.

Lately, on some forums when I have a question about an application, or networking issue with samba/cifs, etc. I always get fussed at about using /mnt as a mount point.

Is there some real valid reason that cifs share mounts should not be on /mnt???

Well, there are the Linux File System Hierarchy Standards which all the major Linuxen claim to follow.  Most copies/versions of this information have a table which is pretty clear ... and which, IMHO, Canonical ignores.

[LIST]
[*]/mnt/ is for temporary mounts, like when an admin is getting a file system ready to be mounted elsewhere.
[*]/media/ is for **removable media** that will not be permanently mounted.
[/LIST]

Whether these are "valid reasons" is open to interpretation.  As a 25+ yr Unix admin, I'd never mount anything under /mnt/ overnight, unless I was copying files there.  I would assume /mnt didn't have anything in it and would slap my mount over the top on a whim.

I haven't mounted a DVD or CDROM in years, but if I did, it would be somewhere under /media/.  I suppose external USB drives or flash storage could be considered removable media. Judgement call.

NFS definitely isn't either of those.  For NFS, we get to use our imaginations. Long ago, we'd use /export(s)/ or /nfs/.  I found those to be too long and go with /d/ ... data. Of course, HOME directories can also go almost anywhere. I use the /u/{username} in small clients and for servers with thousands of users, /u/u1/{username}, /u/u2/{username} .... /u/u99/{username}.

Here's the rub.  Canonical has been pushing snap packages more and more. They've hard coded specific locations where a packager of snap packages _may_ choose to allow storage not in the user's HOME to be accessed.  Those hard coded locations are /mnt/ and /media/ because I think the team believes we all run our computers like a locked down cellular phone.  The constraint in "snap" terms is removable-media. This must be enabled both by us and by the package creator for /mnt/ and /media/ storage to be accessed.  Forget about /d/ or /opt/ or /data/ or /cifs/ or /nfs/. Those will never work with snap programs.

Snap packages do not work in any way with NFS storage. The bug for that was opened in 2017.  I understand it was pushed upstream, but Flatpaks and AppImages work fine with NFS.  Sometimes NFS errors for snaps are clear, concise and correct.
```
$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```
An excellent error message. But it doesn't work because the HOME directory for that userid both in the LDAP DB and on storage is not under /home/ . That's just crazy to me.  Unix is supposed to be flexible, right?  The required solution, if NFS isn't used, is to use a bind-mount and modify the password entry.

Sorry. Didn't mean to write this.  It is just that a server upgrade failed today from 18.04 --> 20.04 because the snap packager couldn't reach the internet and blocked the upgrade.  No clue why, since the rest of the upgrade process worked fine pulling stuff off the network.  For me and admins like me, snaps are forcing an OS change as they get embedded deeper and deeper into our beloved Ubuntu.  The server with the failure didn't have any snaps that I'm aware. Somehow, an APT dependency must have pulled some snap packages into the system. {insert word we can't write here!!}

---

### Post by teddymills on 2021-06-27
mkdir usb1 usb2 etc in home directory. Change permissions  mount drives and add to fstab. Not necessarily correct but easy and convenient.

---

### Post by TheFu on 2021-06-27
> **teddymills said:**
> mkdir usb1 usb2 etc in home directory. Change permissions  mount drives and add to fstab. Not necessarily correct but easy and convenient.

And what about the 4 other users who want access to the same storage?  That's the flaw with many things done automatically on desktop Linux today. They assume 1 user per computer.

If mounting storage under HOME was a good idea, then why does /media/ get mounted partitions at all?  The answer is because mounting added file systems under someone's HOME will likely break system backups since backup storage won't have 2TB of free space, but will likely want to grab everything in each user's HOME.  Also, newer versions of Linux are changing back to the locked down defaults for users - 770 on the HOME, so userids not part of the same group won't have any access under another user's HOME.

My point isn't that there are usually work arounds. It is that none should be required for standard, normal, things Unix does and has been doing for 40+ yrs.

---

